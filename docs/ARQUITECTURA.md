# Arquitectura

## Estructura

```
.
├── README.md
├── docs/
│   ├── ESPECIFICACION.md
│   ├── ARQUITECTURA.md
│   ├── ALGORITMOS.md     # cada quien escribe la sección de su parte
│   ├── REPARTO.md
│   └── REFLEXION.md      # una sección por persona
├── examples/             # entrada1.txt (ejemplo del enunciado) + entradas extra
└── src/
    ├── main.py           # orquesta e imprime; sin lógica de algoritmos
    ├── io_utils.py       # lectura de la entrada y nombres con letras
    ├── cableado.py       # Parte 1: Prim
    ├── ruta.py           # Parte 2: ramificación y poda
    ├── flujo.py          # Parte 3: Ford-Fulkerson
    └── centrales.py      # Parte 4: se define al verla en clase
```

## Contratos (firmas acordadas)

| Módulo | Función | Contrato |
|---|---|---|
| `io_utils` | `leer_entrada(path: str) -> tuple[int, list[list[int]], list[list[int]], list[tuple[int, int]]]` | Devuelve `(n, distancias, capacidades, centrales)`. |
| `io_utils` | `letra(i: int) -> str` | `0 -> "A"`, `1 -> "B"`, ... |
| `cableado` | `cableado_optimo(distancias: list[list[int]]) -> list[tuple[int, int]]` | Arcos del árbol en el orden en que Prim los agrega desde el nodo 0; cada par con el índice menor primero. |
| `ruta` | `ruta_mas_corta(distancias: list[list[int]]) -> list[int] \| None` | Ciclo que empieza y termina en 0 (ej. `[0, 1, 2, 3, 0]`), o `None` si no existe. |
| `flujo` | `flujo_maximo(capacidades: list[list[int]], fuente: int, destino: int) -> int` | Valor del flujo máximo. No modifica la matriz recibida. |
| `centrales` | por definir | Parte 4. |

## Reglas
- Los módulos de algoritmos no leen archivos ni imprimen; solo `main.py` imprime.
- Cada función lleva arriba un comentario `#funcion nombre: complejidad O(...), porque ...`, como en las actividades anteriores.
- Python 3.10 o superior por las anotaciones `| None`.
- Sin dependencias externas.
- Si cambia una firma, se actualiza este archivo en el mismo PR.
