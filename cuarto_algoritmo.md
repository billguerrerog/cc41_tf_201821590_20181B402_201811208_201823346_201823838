# Algoritmo 4 <h1>
  
Topic | Desc
------------ | -------------
Autor | Sebastian Alfaro
Técnica Principal | Prim algorithm

Para resolver el problema de enrutamiento de vehículos, se implementará el algoritmo de Prim. 
El algoritmo de Prim tiene una complejidad de O(n^2). 
A comparacion del algoritmo de Dijkstra, el algoritmo de Prim es asintóticamente mucho más rápido.

### Pseudocódigo del algoritmo de Prim <h2>

  	Algoritmo_Prim(G grafo, A conjunto_aristas)
            A:= conjunto_vacío;
            VISTOS:= añadir (conjunto_vacio, {1});
            Para i=2 hasta n hacer
                        VECINO[i]:= 1;
                        COSTE_MÍNIMO [i]:= M [i, 1];
            FinPara
            Mientras (|VISTOS| < n) hacer           
                        min:= infinito;
                        Para j=2 hasta n hacer
                                   si (0 <= COSTE_MÍNIMO [j] < min) entonces
                                               min:= COSTE_MÍNIMO [j]; k:= j;
                                   FinSi
                        FinPara
                        A:= A U {(k, VECINO[k])};
                        VISTOS:= VISTOS U {k};
                        COSTE_MÍNIMO [k]:= -1;
                        para j=2 hasta n hacer
                                   si (M[k,j] < COSTE_MÍNIMO [j]) entonces                   
                                           COSTE_MÍNIMO [j]:= M [k,j]                                          
                                           VECINO[j]:= k;
                                   FinSi
                        FinPara
            FinMientras
    FinAlgoritmo_Prim

### Análisis asintótico de Prim <h3>

![image](https://media.discordapp.net/attachments/829066700808126487/911881665171816478/unknown.png?width=892&height=504)

El análisis asintótico del algoritmo de Prim es de O(n^2).
