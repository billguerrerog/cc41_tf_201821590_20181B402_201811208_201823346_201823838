# Algoritmo 4 <h1>
  
Topic | Desc
------------ | -------------
Autor | Sebastian Alfaro
Tecnica Principal | Floyd Warshall algorithm

Para resolver el problema de enrutamiento de vehículos, se implementará el algoritmo de Floyd Warshall. 
El algoritmo de Floyd Warshall tiene una complejidad de 0(n^3). 
A comparacion del algoritmo de Dijkstra, el algoritmo de Floyd Warshall es asintóticamente mucho más rápido.

### Pseudocódigo del algoritmo de Floyd Warshall <h2>

  	n = rows [W]
    	D ^ (0) = W
    	 For k = 1 to n
    	   Do for I = 1 to n 
         Do for j = 1 to n 
    	 d (ij) ^ (k) = min (d(ij) ^ (k-1), d (ik) ^ (k-1) + d(kj) ^ (k-1))
    return D ^ (n)

### Análisis asintótico de Floyd Warshall <h3>

![image](https://user-images.githubusercontent.com/52021716/135740384-59cf3220-fa11-47fb-a969-93352803f874.png)
 
 Siguiendo el análisis:
  1. Asignacion: +1
  2. Leer referencias k y n, Comparacion k=n y k<n: +4n
  3. Asignacion: +1
  4. Leer referencias i y n, Comparacion i=n y i<n: +4n^2
  5. Asignacion: +1n^2
  6. Leer referencias j y n, Comparacion j=n y j<n: +4n^3
  7. Leer referencias i,j,k Ak, Aj, Ai, Suma Ak+Aj, Calculo min , Asignación min(Ai,Aj + Ak) 9n^3
  8. Leer referencias j, Suma j+1, Asignación j+1 3n^3
  9. Leer referencias i, Suma i+1, Asignación i+1 3n^2
  10. Leer referencias k, Suma k+1, Asignación k+1 3n
  
 Resultaría así:
                                                    
![image](https://user-images.githubusercontent.com/52021716/135740422-e61e2d17-426d-4c20-98da-04088fd5a623.png)

El análisis asintótico del algoritmo de Floyd Warshall es de O(n^3).
