# Algoritmo 2

Topic | Desc
-|-
Autor | Josue Cuentas Jave
Técnica principal | Fuerza Bruta

## Definición

Este algoritmo consistirá en la utilización de la fuerza bruta a través del algoritmo de búsqueda DFS(Depth First Search), para hallar el camino con menor costo desde un almacén a un punto de entrega, los cuales serán representados por nodos en un grafo. Asimismo, cada arista tendrá un costo para llegar del punto A al punto B, el cual será considerado para establecer el camino con menor costo:

![BFS Representation](https://user-images.githubusercontent.com/55953542/135744155-961a02ef-d79e-475e-a238-df89919f23eb.jpg)

## Lógica del algoritmo DFS

El algoritmo DFS comienza en el nodo raíz de un grafo. Realiza un recorrido por todo el grafo empezando con el primer hijo del nodo raíz luego va al hijo del primer hijo del nodo raíz hasta llegar a un nodo hoja.

## Ejemplo de recorrido del algoritmo

![DFS](https://user-images.githubusercontent.com/55953542/135744164-ddd2c27f-7563-4331-87ff-3592cc47c269.jpg)

## Análisis asintótico

```
def DFS(G, s):            
  n = len(G)                # 1
  visited = [False]*n       # n
  parent = [None]*n         # n
  stack = [s]               # 1
  while stack:              # n*
    u = stack.pop()         # 1
    if not visited[u]:      # 1
      visited[u] = True     # 1
      for v in G[u]:        # 1 + n*
        if not visited[v]:  # 1
          parent[v] = u     # 1
          stack.append(v)   # 1
  return parent             # 1
```

![Analisis asintotico](https://user-images.githubusercontent.com/55953542/135744266-3a970099-2c8d-4ba1-a71c-3d922234f93f.PNG)
