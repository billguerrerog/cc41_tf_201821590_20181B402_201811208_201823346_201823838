# Algoritmo 1

Topic | Desc
-|-
Autor | Bill Guerrero González
Técnica principal | Fuerza Bruta

## Definición

Este algoritmo consistirá en la utilización de la fuerza bruta a través del algoritmo de búsqueda BFS(Breadth First Search), para hallar el camino con menor costo desde un almacén a un punto de entrega, los cuales serán representados por nodos en un grafo. Asimismo, cada arista tendrá un costo para llegar del punto A al punto B, el cual será considerado para establecer el camino con menor costo:

![image](https://user-images.githubusercontent.com/55320230/135740616-cf19b514-7ab8-4c20-b097-5c8924921e5e.png)

## Lógica del algoritmo BFS

El algoritmo BFS visitará cada nodo adyacente al nodo de punto de partida. Luego, visitará cada uno de los nodos adyacentes de los nodos adyacentes al punto de partida, y así sucesivamente.

Para ello, utilizará el concepto de colas, para añadir los nodos adyacentes de cada nodo y saber cuáles serán los nodos que deberá visitar luego. 

Así, luego de haber llegado al nodo destino (punto de entrega), se seleccionará el camino de menor costo.

## Desarrollo del algoritmo

### Se toma como punto de partida el nodo 0
![image](https://user-images.githubusercontent.com/55320230/135742048-60ec57d7-5fca-40c0-80f5-f0661c806627.png)

### Luego, se añaden los nodos adyacentes a la cola y se visitan los nodos en la cola
![image](https://user-images.githubusercontent.com/55320230/135742061-3daadd59-e72e-4733-aa2e-b36bf3704df1.png)

![image](https://user-images.githubusercontent.com/55320230/135742070-7dcfb19a-f3e1-456d-b5a4-61a6e9f9be56.png)

![image](https://user-images.githubusercontent.com/55320230/135742085-00a86016-505d-49bd-b1d7-96397b50a2e3.png)

### Finalmente, se han recorrido todos los nodos
![image](https://user-images.githubusercontent.com/55320230/135742092-692f3509-bb31-4c2e-8bfc-c8c52d1d25c5.png)


## Análisis asintótico

La complejidad del algoritmo BFS está representado por O(V + E), debido a que el algoritmo visitará todos los vértices(V) y aristas(E). Así, en el peor de los casos, el algoritmo visitará cada uno de los nodos.
