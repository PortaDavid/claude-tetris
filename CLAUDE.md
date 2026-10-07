# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Classic Tetris implemented in vanilla JavaScript with HTML5 Canvas. No dependencies, no build step, no package.json. The project language (UI, comments, README) is Spanish.

## Running the Game

Open `index.html` directly in a browser, or serve with any static server:

```bash
python3 -m http.server 8000
```

There are no build, lint, or test commands.

## Architecture

Three files, all at the root:

- **`index.html`** — DOM structure: a 300×600 `<canvas id="board">`, a 120×120 `<canvas id="next-canvas">` for the next-piece preview, a side panel (score/lines/level/controls), and a pause/game-over overlay.
- **`style.css`** — Dark retro-arcade theme. Colors and layout use plain CSS (no variables framework). The board and overlay share a border-radius and backdrop-filter blur.
- **`game.js`** — All game logic (~300 lines). Key concepts:
  - **Board model**: `ROWS × COLS` matrix; `0` = empty, `1–7` = piece color index.
  - **Pieces**: defined as 2D arrays in `PIECES[]`, indexed 1–7 (index 0 is null). Rotation is transpose + row-reverse (`rotateCW`).
  - **Wall kicks** (`tryRotate`): tries offsets `[0, -1, 1, -2, 2]` on rotation failure.
  - **Game loop**: `requestAnimationFrame`-based; accumulates delta time and drops the piece when `dropAccum >= dropInterval`.
  - **Scoring**: `LINE_SCORES = [0, 100, 300, 500, 800]` × level. Hard drop adds 2 pts/cell, soft drop 1 pt/row.
  - **Speed**: `dropInterval = max(100, 1000 - (level-1) * 90)` ms. Level increments every 10 lines.
  - **Ghost piece**: `ghostY()` projects the landing position; drawn at `globalAlpha = 0.2`.
  - **State**: all game state lives in module-level `let` variables (`board`, `current`, `next`, `score`, `lines`, `level`, etc.). `init()` resets everything.

## Canvas Sizing

The board canvas dimensions must equal `COLS × BLOCK` by `ROWS × BLOCK` (default 300×600). If you change `COLS`, `ROWS`, or `BLOCK` in `game.js`, update the `width`/`height` attributes on `<canvas id="board">` in `index.html` to match.
