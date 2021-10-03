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

![GitHub Logo](https://cdn.discordapp.com/attachments/839568290078392383/894071751884029952/1_sqw-VCwr0RCc2uwo4gWfDB_GjMPdxuu-_qUD92GpYESV0mLIZhd6qy-kGAKTiA.png)

El análisis asintótico del algoritmo de dijkstra es de O(n^2).
