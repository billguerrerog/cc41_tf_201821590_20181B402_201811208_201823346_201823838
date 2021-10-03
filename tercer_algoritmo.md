# Algoritmo 3
Topic | Desc
------------ | -------------
Autor | José Tarazona
Tecnica Principal | Dijkstra with list algorithm

# Dijkstra with list algorithm

El algoritmo Dijkstra trata sobre una particularidad de la búsqueda de costo uniforme, pero no funciona en grafos con aristas de costo negativo. Para nuestro 
problema el algoritmo agrupar los puntos de entrega más cercanos a los puntos de distribución (almacenes), después se debe calcular las rutas con menor costo desde
cada almacén a cada punto de entrega.

Utilizar este algoritmo sería la mejor solución ya que permite recorrer un grafo utilizando la ruta más económica, esto quiere decir que revisa el peso de la arista que une
dos nodos y recorre el de menor peso. Sin embargo, para el problema este algoritmo no debe pasar por el mismo punto de entrega dos veces. Este código sigue los siguientes pasos:

1. Iniciar todos los nodos con distancia "infinita" e iniciar el nodo inicial con 0.
2. Marcar la distancia del nodo inicial como permanente, y las demás distancias como temporal.
3. Configurar el nodo del inicio como activo.
4. Calcular las distancias temporales de todos los nodos vecinos del nodo activo sumando su distancia con los pesos de los bordes.
5. Si esa distancia calculada de un nodo es menor a la actual, se debe actualizar la distancia y configurar el nodo actual como antecesor.
6. Repetir los pasos 4 y 6 hasta que no queden nodos con una distancia permanente, cuyos vecinos todavía tienen distancias temporales.

**Análisis de Complejidad**

El orden de complejidad del algoritmo es: O(|V|2+|A|) = O(|V|2) sin utilizar la cola de prioridad. Podemos evaluar la complejidad computacional del algoritmo de Dijkstra
(en términos de sumas y comparaciones). El algoritmo a lo más realiza n-1 iteraciones, ya que en cada iteración se añade un vértice al conjunto distinguido. Para calcular
el número total de operaciones basta estimar las que se llevan a cabo en cada iteración.

![image](https://user-images.githubusercontent.com/51182166/135742585-9c34a567-d3a1-4e2c-8c28-1ea8cf570689.png)




