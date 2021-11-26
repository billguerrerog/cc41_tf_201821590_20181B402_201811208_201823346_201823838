# Problema de Enrutamiento de Vehículos (VRP) 

#### CC41 - TRABAJO FINAL COMPLEJIDAD ALGORÍTMICA 2021

|INTEGRANTES |CÓDIGO |
|-|-|
|Alfaro Mendoza, Sebastián |U201811208 |
|Cuentas Jave, Josue |U20181B402 |
|Guerrero González, Bill |U201821590 |
|Pain Peralta, José |U201823838 |
|Tarazona Ildefonso, José |U201823346 |

## INTRODUCCIÓN
El Problema de generación de rutas para vehículos (VRP) es un nombre genérico que se 
le da a toda una clase de problemas en los que se debe determinar un conjunto de rutas 
para una flota de vehículos con base en uno o varios depósitos para varias ciudades o 
clientes geográficamente dispersos. El objetivo del VRP es ofrecer un conjunto de clientes 
con demandas conocidas sobre rutas de vehículos de costo mínimo que se originan y terminan 
en un depósito. En las dos figuras siguientes podemos ver una imagen de una entrada típica 
para un problema de VRP y una de sus posibles salidas:

 ![Imagen de VRP](https://cdn.discordapp.com/attachments/729537977092407390/912102993434927164/vrp.png)
 
 ## MARCO TEÓRICO
 ### Algoritmo BFS (Breadth First Search)
 El algoritmo de búsqueda en anchura (BFS) es un algoritmo de búsqueda el cual recorre todos los nodos de un grafo. Comenzando en la raíz, eligiendo un nodocomo raíz en el caso de un  grafo, para seguir con la búsqueda en los nodos adyacentes. Este proceso se repite hasta recorrer todo el grafo, o en su defecto encontrar el nodo solicitado. 

> - La complejidad del algoritmo BFS está representado por O(V + E).
 
 ### Algoritmo DFS (Depth Firts Search)
 El algoritmo de búsqueda en profundidad es un algoritmo de búsqueda que consiste en recorrer un grafo desde un nodo de inicio, de manera que, los nodos que localiza los recorrerá hasta que no queden más en dicho camino, luego de volver al nodo de origen volverá a realizar el mismo proceso con los demás nodos vecinos. Al recorrer todos los nodos o encontrar el nodo buscado, acabará el proceso.

> - El algoritmo DFS emplea la tecnica de Backtracking para resolver los problemas. 
 
 ### Algoritmo de Dijkstra
 El algoritmo de búsqueda en anchura es un algoritmo de búsqueda el cual recorre todos los nodos de un grafo. Comenzando en la raíz, eligiendo un nodocomo raíz en el caso de un  grafo, para seguir con la búsqueda en los nodos adyacentes. Este proceso se repite hasta recorrer todo el grafo, o en su defecto encontrar el nodo solicitado. 
 
 > - Fue concebido por Edsger Dijkstra, científico de la computación de los Países Bajos, en 1956. 
 > - La complejidad del algoritmo de Dijkstra es de O(n^2).
 
 ### Algoritmo de Prim
 El algoritmo Prim es un algoritmo que permite encontrar de un árbol recubridor mínimo en un grafo conexo. El algoritmo encuentra un subconjunto de aristas que forman un árbol con todos los vértices, donde el peso total de todas las aristas en el árbol es el mínimo posible. En caso el grafo no fuera conexo, entonces el algoritmo encontrará el árbol recubridor mínimo para uno de los componentes conexos que forman dicho grafo no conexo.
 
 > - El algoritmo fue diseñado en 1930 por el matemático Vojtech Jarnik y luego de manera independiente por el científico computacional Robert C. Prim en 1957.
 > - Algoritmo del Prim también conocido como algoritmo DJP o algoritmo de Jarnik.
 
 ### Fibonacci Heap
 Fibonacci heap es una estructura de datos subconjunto de los montículos, que a su vez, son un subconjunto especial dentro de los bosques de árboles. Fibonacci heap fue desarrollado en 1984 por Michael L. Fredman y Robert E. Tarjan. En un Fibonacci heap, un nodo puede tener más de dos hijos o ningún hijo. Además, tiene operaciones heap más eficientes que las soportadas por los heaps binomiales y binarios.
 
 > - El algoritmo de Dijkstra usando fibonacci heap tiene una complejidad de O(E + V log V).
 
 ## DESARROLLO
 ### Creación del Grafo 
 Se importa las librerías y la información de los dataset de los puntos de entrega y los almacenes, ambos en archivos **CSV** que se usara para la creación del grafo.
 
 ```python 
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
from copy import deepcopy
import math

almacenes = pd.read_csv("https://raw.githubusercontent.com/billguerrerog
/cc41_tf_201821590_20181B402_201811208_201823346_201823838/main/almacenes.csv")
alm = almacenes[['Coord X', 'Coord Y']]
nodeTypeALM = [1]*100
alm['NodeType'] = nodeTypeALM

puntos_entrega = pd.read_csv("https://raw.githubusercontent.com/billguerrerog
/cc41_tf_201821590_20181B402_201811208_201823346_201823838/main/puntos_entrega.csv")
pe = puntos_entrega[['Coord X', 'Coord Y']]
nodeTypePE = [2]*5000
pe['NodeType'] = nodeTypePE
 ```
 
  ### Visualización del grafo
 ![Imagen del grafo](https://cdn.discordapp.com/attachments/729537977092407390/912115751022891008/GRafo.png)

 ### Creación de regiones de distribución de cada almacén
   ```python 
#Get single region
def get_region(alm, asigned_delivery):
    min_x, min_y = get_coords(alm) # Start
    max_x, max_y = get_coords(alm) # Start
    for i in asigned_delivery: #Getting min and max coords to create region
        delivery_x, delivery_y = get_coords(i) #Coords to compare
        if delivery_x < min_x: #Check min X
            min_x = delivery_x
        elif delivery_x > max_x: #Check max X
            max_x = delivery_x
        if delivery_y < min_y: #Check min Y
            min_y = delivery_y
        elif delivery_y > max_y: #Check max Y
            max_y = delivery_y

    min_max = [min_x, min_y, max_x, max_y]
    return min_max

# Get Regions
def all_regions(asigned_stuff):
    regions = []
    for i in asigned_stuff:
        aux = []
        region = get_region(i[0], i[1])
        aux.append(i[0])
        aux.append(region) #Region coords
        regions.append(aux)
    
    return regions
 ```
  ### Visualización de las regiones de cada almacen
   ![Imagen de las regiones](https://cdn.discordapp.com/attachments/729537977092407390/912116810063691847/descargar.png)
   
 ## SOLUCIONES
 Para encontrar la solución más optima para el Problema de Enrutamiento de Vehículos (VRP) se implementaron 5 algoritmos (1 por integrante).
 
 ### ALGORITMO 1 - FUERZA BRUTA a través del algoritmo de búsqueda BFS(BREADTH FIRST SEARCH)
```python 
def algorithm_1(graph, start):
    visited = {}
    parent = {}
    for i in graph:
        visited[i] = False
        parent[i] = None
    
    visited[start] = True
    queue = [start]

    while queue:
        u = queue.pop(0)
        for v in graph[u]:
            if not visited[v]:
                visited[v] = True
                parent[v] = u
                queue.append(v)

    return parent
```

 ### ALGORITMO 2 - FUERZA BRUTA  a través del algoritmo de búsqueda DFS(DEPTH FIRST SEARCH)
```python 
def algorithm_2(graph, start):
  visited = {}
  parent = {}

  for i in graph:
    visited[i] = False
    parent[i] = None

  stack = [start]

  while stack:
    u = stack.pop()
    if not visited[u]:
      visited[u] = True
      for v in graph[u]:
        if not visited[v]:
          parent[v] = u
          stack.append(v)

  return parent
```

### ALGORITMO 3 - DIJKSTRA con listas
```python 
def algorithm_3(graph, start):
  visited = {}
  path = {}
  cost = {}
  for key in graph.keys():
    visited[key] = False
    path[key] = None
    cost[key] = math.inf

  cost[start] = 0
  queue = [(start, 0)]
  while queue:
    u, g_u = hq.heappop(queue)
    if not visited[u]:
      visited[u] = True        
      for v in graph[u]:
        f = g_u + 1
        if f < cost[v]:
          cost[v] = f
          path[v] = u
          hq.heappush(queue, (v, f))
  return path
```

### ALGORITMO 4 - PRIM
```python 
def algorithm_4(graph, start):
  visited = {}
  path = {}
  cost = {}
  for key in graph.keys():
    visited[key] = False
    path[key] = None
    cost[key] = float('inf')
  cost[start] = 0
  q = [(0, start)]
  while q:
    i, u = hq.heappop(q)
    if not visited[u]:
      visited[u] = True
      for v in graph[u]:
        if not visited[v] and 1 < cost[v]:
          cost[v] = 1
          path[v] = u
          hq.heappush(q, (1, v))

  return path
```

### ALGORITMO 5 - DIJKSTRA con Fibonacci Heap
```python 
def algorithm_5(graph, start):
    visited = {}
    parent = {}
    cost = {}
    fheap1 = [(start, 0)]
    for key in graph.keys():
        visited[key] = False
        parent[key] = None
        cost[key] = math.inf

    cost[start] = 0
    while fheap1:
        u, g_u = popFib(fheap1)
        if not visited[u]:
            visited[u] = True
            for v in graph[u]:
                f = g_u + 1 #No cost
                if f < cost[v]:
                    cost[v] = f
                    parent[v] = u
                    pushFib(fheap1, (v, f))
    return parent
```
## DEMOSTRACION 
``` python
import numpy as np
import matplotlib.pyplot as plt

def get_alm_coords_from_dict(from_dict):
    alm_coords_list = []
    for i in routes_dict.keys():
        x, y = get_coords(i)
        aux = [x, y]
        alm_coords_list.append(aux)
    return alm_coords_list

alm_nodes_list = get_alm_coords_from_dict(routes_dict)

regions_routes_to_coords = []
for storage in routes_dict.keys():
    region_route_to_coords = []
    for delivery in routes_dict[storage]:
        route_to_delivery = []
        for point in routes_dict[storage][delivery]:
            x, y = get_coords(point)
            aux = [x, y]
            route_to_delivery.append(aux)
        region_route_to_coords.append(route_to_delivery)
    regions_routes_to_coords.append(region_route_to_coords)

# Show regions routes
for i in regions_routes_to_coords:
    for j in i:
        data = np.array(j)
        plt.plot(*data.T)

#Show storage points
for i in alm_nodes_list:
    plt.plot(i[0], i[1],marker="o", markersize=10, markeredgecolor="red", markerfacecolor="red")

plt.show()
```
![image](https://user-images.githubusercontent.com/52021716/143510220-07f5f882-f035-462b-a12a-cb9dd2701bba.png)

 ## CONCLUSIONES
 - Dado que tenemos grafos con numero de aristas exponenciales, utilizar algoritmos como BFS aplicando fuerza bruta o Dijkstra, nos brindan una mayor velocidad en la respuesta esperada para la solucion del proyecto.
 - Los problemas de VRP tienen diferentes soluciones aplicables, el uso de estos algoritmos permiten hacer un constraste sobre la exhaustiva tarea que sería implementar una solucion para un VRP.
 - Los implementar los algoritmos en el lenguaje de programacion python, nos ayudó a entender correctamente la logica de los mismos debido a la sencilla sintaxis de código explicada en clases.
 ## BIBLIOFRAFÍA
- Proposal of Fibonacci Heap in the Dijkstra Algorithm for Low-power Ad-hoc Mobile Transmissions. (2020, 1 marzo). IEEE Journals & Magazine | IEEE Xplore. https://ieeexplore.ieee.org/abstract/document/9082735
- Robinson, S. (2021, 21 noviembre). Graphs in Python: Dijkstra’s Algorithm. Stack Abuse. https://stackabuse.com/dijkstras-algorithm-in-python/
- Nelson, D. (2021, 29 junio). Graphs in Python: Minimum Spanning Trees - Prim’s Algorithm. Stack Abuse. https://stackabuse.com/graphs-in-python-minimum-spanning-trees-prims-algorithm/
- Landup, D. (2021, 15 octubre). Graphs in Python: Depth-First Search (DFS) Algorithm. Stack Abuse. https://stackabuse.com/depth-first-search-dfs-in-python-theory-and-implementation/



