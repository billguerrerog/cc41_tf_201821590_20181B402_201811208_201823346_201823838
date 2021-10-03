# Algoritmo 5 <h1>

Topic | Desc
------------ | -------------
Autor | Jose Pain
Tecnica Principal | Dijkstra with fibonacci heap

Para resolver el problema de enrutamiento de vehículos, se implementará el algoritmo de dijkstra junto con fibonacci heap. 
Sin usar fibonnaci heap, Dijkstra tiene una complejidad de 0(n^2), pero usando fibonacci esta complejidad sería de O(1 + nlogn), 
lo cual es asintóticamente mucho más rápido.

### Análisis asintótico de fibonacci heap <h3>

![GitHub Logo](https://cdn.discordapp.com/attachments/893269602577035274/894071244465524776/1hAQr3yuS-jUyQUNAwPaYAfDMQ9huLOfrXSDVbcGl3aSDaeSrb-cNTBwBUD1tjQ.png)

Este sería el análisis asintótico de cada método del fibonnaci heap.

### Pseudocódigo de Dijkstra <h3>
  
1) Establecer todas las distancias de los nodos a infinito y comenzar desde 0
2) Añadir (0,start) a la cola
3) While la cola no está vacía:
4) Pop (d,currently) de la cola
5) if currently no está hecho:
6) Marcar currently como hecho
7) For todas las aristas (currently,w,e):
8) if d+e< w distancia actual:
9) w distancia actual = d + e
10) w anterior nodo es el actual
11) añadir (d+e,w) a la cola
            
                            
  

El análisis asintótico del algoritmo de dijkstra es de O(n^2).
