# Reparto del trabajo

El trabajo es **en orden**: cada persona empieza cuando la anterior ya mergeó su parte a `main`, y al terminar la suya ya no trabaja más. Cada quien entrega su parte completa: código, su sección en `ALGORITMOS.md` y su sección en `REFLEXION.md`.

| Orden | Issue | Persona | Trabajo | Rama |
|---|---|---|---|---|
| 1 | #1 | Jp | Parte 1 (cableado con Prim) + base del proyecto (`io_utils.py`, `main.py`, `examples/`) | `parte-1-cableado` |
| 2 | #2 | Ricky | Parte 2 (ruta con ramificación y poda) + Parte 3 (flujo con Ford-Fulkerson) | `parte-2-3-ruta-flujo` |
| 3 | #3 | Fabian | Parte 4 (centrales) + README final y entregable | `parte-4-centrales` |

## Flujo
1. Crear la rama del issue desde `main` actualizado.
2. PR referenciando el issue (`Closes #N`).
3. Merge a `main` y avisar al siguiente.
4. No se cambian firmas sin actualizar `ARQUITECTURA.md`.
