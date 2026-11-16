# Especificación

## Ejecución
Desde la raíz del repositorio:

```bash
python3 src/main.py examples/entrada1.txt
```

El archivo de entrada se recibe como primer argumento (`sys.argv[1]`).

## Entrada
En este orden (se toleran líneas en blanco y espacios extra):

1. Un entero `N`: número de colonias.
2. Matriz `N x N` de distancias en km entre colonias (grafo ponderado).
3. Matriz `N x N` de capacidades máximas de transmisión de datos entre la colonia `i` y la `j`.
4. Lista de pares `(x,y)`: ubicación de las centrales en el plano.

Ejemplo (`examples/entrada1.txt`):

```text
4

 0 16 45 32
16  0 18 21
45 18  0  7
32 21  7  0

 0 48  12  18
52  0 42 32
18 46  0 56
24 36 52  0

(200,500)
(300,100)
(450,150)
(520,480)
```

Las colonias se nombran con letras: la primera es `A`, la segunda `B`, etc.

## Salida (en este orden)

### Parte 1: cableado con fibra óptica
Lista de arcos `(A,B)`, uno por línea, que conectan todas las colonias con la menor cantidad de km. Se imprimen en el orden en que Prim los agrega empezando en `A`, con la letra menor primero dentro del par.

### Parte 2: ruta del repartidor
Una línea con la ruta más corta que visita cada colonia exactamente una vez y regresa al origen (`A`), con letras separadas por espacio. Si hay empate, se reporta la primera encontrada explorando las colonias en orden `A, B, C, ...`. Si no existe ruta: `No existe ruta`.

### Parte 3: flujo máximo
Una línea con el valor del flujo máximo de información del nodo inicial (`A`) al nodo final (la última colonia).

### Parte 4: centrales
Lista de polígonos; cada polígono es una lista de puntos `(x,y)`. El formato exacto se define cuando se vea el tema en clase.

### Salida esperada del ejemplo (Partes 1 a 3, calculada a mano)

```text
(A,B)
(B,C)
(C,D)
A B C D A
78
```

- Parte 1: `A-B` (16) + `B-C` (18) + `C-D` (7) = 41 km.
- Parte 2: `A B C D A` = 16 + 18 + 7 + 32 = 73 km. Las otras dos rutas posibles cuestan 89 (`A B D C A`) y 116 (`A C B D A`).
- Parte 3: lo que sale de `A` es 48 + 12 + 18 = 78, y sí se puede mandar todo hasta `D`.

## Supuestos
1. Una distancia `0` fuera de la diagonal significa que no se puede meter cable entre esas colonias.
2. La matriz de capacidades es **dirigida**: `capacidad[i][j]` puede ser distinta de `capacidad[j][i]`.
3. Nodo inicial (fuente) = `A` (índice 0); nodo final (destino) = la última colonia (índice `N-1`).
4. Internamente todo es 0-indexed; se convierte a letras solo al imprimir.

## Restricciones
- Solo algoritmos vistos en clase: Prim (técnica avara) para la Parte 1, ramificación y poda para la Parte 2, Ford-Fulkerson para la Parte 3.
- Sin librerías externas, solo biblioteca estándar.
