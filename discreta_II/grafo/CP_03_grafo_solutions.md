# Soluciones CP3 Coloreo

## Problema 1

> Demuestra que $\mathcal{X}(K_n) = n$ para todo $n \in \mathbb{N}$

Procedamos por inducción, demostremos que para todo clique de $n$ vértices se cumple que su número cromático es $n$.

Caso base $n=0, n=1$, cuyos números cromáticos son 0 y 1 respectivamente.

Supongamos que un clique de $k$ vértices tiene como número cromático $k$, nótese que al agregar un vértice, para formar un clique este debe conectarse a los $k$ vértices, y por tanto, no puede ser coloreado de uno de esos $k$ colores porque es adyacente a esos vértices, entonces requiere un nuevo color y el cloque resultante tiene como número cromático $k+1$

Nótese que $K_n$ es un clique de $n$ vértices, por lo que $\mathcal{X}(K_n) = n$

## Problema 2

> $\mathcal{X}(C_n) = 2$ si $n$ es par y $\mathcal{X}(C_n) = 3$ si $n$ es impar

