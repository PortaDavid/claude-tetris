# Implementa

## Menú de pausa completo

Al pausar (tecla `P` o `Escape`) mostrar un overlay con opciones reales:

- **Reanudar** — vuelve al juego
- **Reiniciar** — nueva partida sin recargar página
- **Ver controles** — lista de teclas dentro del menú
- **Nivel inicial** — selector para elegir con qué nivel empezar la próxima partida
- Bloquear inputs del juego mientras el menú está abierto para evitar movimientos accidentales al volver

---

# Implementa

## Tabla de records local

Guardar las mejores puntuaciones en `localStorage`:

- Top 5 puntuaciones con nombre del jugador (campo de texto al game over)
- Mostrar en pantalla de inicio y en el overlay de game over
- Resaltar si la puntuación actual entra en el top
- Botón para resetear records
- Mostrar también el mejor combo y líneas máximas conseguidas

---

# Implementa

## Temas visuales / skins

Selector de skin que cambia la apariencia completa:

- **Retro** — bloques cuadrados, colores planos (estilo actual)
- **Neon** — fondo negro, glow effect con `shadowBlur` en canvas
- **Pastel** — colores suaves, bordes redondeados simulados
- **Pixel art** — patrón de textura dibujado sobre cada bloque
- Guardar preferencia en `localStorage`; cambio sin recargar aplicando nuevas constantes de color y función de draw


Necesito que me generes el comit de los cambios realizados en esta rama
/home/dgarcia/workspace/03-claude-tetris/.trees/pause         eb82fcb [pause]
/home/dgarcia/workspace/03-claude-tetris/.trees/skins         0ad1574 [skins]
/home/dgarcia/workspace/03-claude-tetris/.trees/tabla-records 0aced36 [tabla-records]

Necesito que te crees un comando con el  nombre: /worktree
Ese comandodebe de crear un worktree :git worktree add .tree/[nombre]
Donde el nombre, lo vas a determinar basado en el requerimiento.
Al invocar el comando /worktree, recibes las instrucciones que deben de empezar a ejecutarse en ese worktree, de manera independiente y aislada del código principal.