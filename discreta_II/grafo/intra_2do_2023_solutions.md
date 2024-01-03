# Ideas de solución Intra-Grafos 2do 2023

## Problema 1

Primeramente hay que modelar el problema a un grafo y reducirlo a emparejamientos. Nótese que $m$ constituye un emparejamiento máximo y $m'$ un emparejamiento maximal, cumpliéndose que $|m| \ge |m'|$.

Sea $G$ un grafo formado por aristas $e$ tal que $e \in m$ o $e \in m'$, pero no a ambos. En $G$ se cumple que cada componente conexa es o un camino o un ciclo, y que las aristas se alternan entre $m$ y $m'$ debido a que ambos son emparejamientos.

Ver que la menor distribución para las aristas de $m'$ es que cada una esté en un camino de 3 aristas, y junto a esta dos aristas de $m$, por lo que en ese caso $|m'| = \frac{|m|}{2}$.

Dicha distribución se puede mejorar tomando uno de esos caminos y cambiar las aristas de los bordes por aristas de $m'$ y eliminando la del medio, lo cual provocaría que $|m'| \gt \frac{|m|}{2}$.

## Problema 2

La primera observación a hacer es que, en el camino más largo, los vértices extremos no pueden ser adyacentes, ya que escogeríamos un vértice exterior adyacente a alguno del ciclo y se formaría un camino más largo. Esto ocurre siempre y cuando el grafo no sea $C_n$, en cuyo caso, como $k\lt n$ basta tomar un camino simple de $k$ vértices del ciclo.

Supongamos que el camino más largo tiene tamaño $\lt k$, por lo ya demostrado, los vértices extremos no son adyacentes, sin embargo, todos sus adyacentes están en el camino, porque de lo contrario, habría un camino más largo al hacer un análisis análogo al anterior. Nótese que como $deg(u)+deg(v) \ge k$ siendo $u,v$ los vértices extremos de ese camino, existen dos vértices internos $p_i,p_{i+1}$ en ese orden, tales que $p_i$ es adyacente a $v$ y el otro con $u$. Por tanto, existe un ciclo y análogo a lo ya dicho con un vértice exterior al ciclo, existiría un camino más largo


## Problema 3

Hay que demostrar que para cualquier par de vértices existe un ciclo simple que los contenga $\iff$ no existe punto de articulación.

Supongamos que no existe punto de articulación, por tanto, para todo par de vértices existen dos camino entre ellos $\implies$ existe un ciclo entre ellos.

Supongamos que para cualquier par de vértices existe un ciclo simple que los contiene y que existe al menos un punto de articulación, al eliminarlo se generan al menos dos componentes conexas, sea $u$ y $v$ vértices en distintas componentes conexas, como entre ellos había un ciclo, al eliminar un vértice en un camino entre ellos $\implies$ existe un camino entre ellos, contradición.

## Problema 4

Si $G$ es libre de triángulos $\implies w(G) \le 2$ y sabemos que $w(G) \le \mathcal{X}(G) = k$. Por tanto, basta analizar el caso $k=1$, el cual cumple la condición.

