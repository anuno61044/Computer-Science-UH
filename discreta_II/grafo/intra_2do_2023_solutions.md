# Ideas de solución Intra-Grafos 2do 2023

## Problema 1

Primeramente hay que modelar el problema a un grafo y reducirlo a emparejamientos. Nótese que $m$ constituye un emparejamiento máximo y $m'$ un emparejamiento maximal, cumpliéndose que $|m| \ge |m'|$.

Sea $G$ un grafo formado por aristas $e$ tal que $e \in m$ o $e \in m'$, pero no a ambos. En $G$ se cumple que cada componente conexa es o un camino o un ciclo, y que las aristas se alternan entre $m$ y $m'$ debido a que ambos son emparejamientos.

Demostremos que no pueden existir caminos con solo una arista. Supongamos que existe un camino de una arista $e$(supongamos sin pérdida de generalidad que dicha arista pertenece a $m$), luego, las aristas adyacentes en el grafo original no pueden pertenecer a $m$ porque $e$ pertenece a $m$, pero esas aristas tampoco pueden pertenecer a $m'$ porque como no pertenecen a $G$ entonces también pertenecen a $m$, lo cual genera una contradicción por lo visto anteriormente.

Ver que la menor distribución para las aristas de $m'$ es que cada una esté en un camino de 3 aristas, y junto a esta dos aristas de $m$, por lo que en ese caso $|m'| = \frac{|m|}{2}$.

Dicha distribución se puede mejorar tomando uno de esos caminos y cambiar las aristas de los bordes por aristas de $m'$ y eliminando la del medio, lo cual provocaría que $|m'| \gt \frac{|m|}{2}$.

## Problema 2

La primera observación a hacer es que, en el camino más largo, los vértices extremos no pueden ser adyacentes, ya que escogeríamos un vértice exterior adyacente a alguno del ciclo y se formaría un camino más largo. Esto ocurre siempre y cuando el grafo no sea $C_n$, en cuyo caso, como $k\lt n$ basta tomar un camino simple de $k$ vértices del ciclo.

Supongamos que el camino más largo $P=\{u=v_1,v_2,\ldots,v_{k'}\}$ es tal que $|P| \lt k \implies$ tiene menos de $k$ aristas $\implies$ tiene menos de $k+1$ vértices, por lo ya demostrado, los vértices extremos no son adyacentes, sin embargo, todos sus adyacentes están en el camino, porque de lo contrario, habría un camino más largo al hacer un análisis análogo al anterior. Tenemos una cantidad $k'\le k$ vértices en el camino, y supongamos que $deg(v)=t$, entonces $s+t\ge k$.

Supongamos que no se cumple que existen en el camino dos vértices $v_i,v_{i+1}$ tal que las aristas $(u,v_{i+1})$ y $(v_i,v)$ están en el grafo, entonces, si $deg(u)=s$ se cumple que ninguno de los vértices que anteceden en el camino $P$ a esos $s$ vértices adyacentes a $u$ deben estar adyacentes a $v$, por tanto, hay en total $k'-1-s$ vértices válidos para ser adyacente a $u$, sin embargo $deg(v) \ge k-s \ge k'-s$, por tanto, $v$ debe ser adyacente a al menos un vértice de los anteriores a los vértices que son adyacentes a $u$.

Luego, $P$ constituye un ciclo, y debe tener a al menos un vértice adyacente a uno externo al camino, lo cual constituye una contradicción porque tomamos el camino más largo.


## Problema 3

Hay que demostrar que para cualquier par de vértices existe un ciclo simple que los contenga $\iff$ no existe punto de articulación.

Probemos que dado un grafo biconexo $\implies$ para cualquier par de vértices existe un ciclo simple que los contiene. Procedamos por inducción la distancia mínima entre los vértices.

- Caso base: para todo par de vértices a distancia 1 (o sea que sean adyacentes) se cumple que debe existir otro camino que los una, porque de lo contrario la arista sería arista puente, lo cual no puede ser porque el grafo es biconexo.
- Hipótesis: supongamos que para todo par de vértices a distancia $k$ se cumple que existen dos caminos disjuntos en vértices que los une, y por tanto existe un ciclo simple.
- Tesis: sean $u,v$ dos vértices a distancia $k+1$, y $w$ el vértice adyacente a $v$ en el camino de longitud $k+1$ de $u$ a $v$. Como $u,w$ están a distancia $k \implies$ existen dos caminos $P,Q$ disjuntos en vértices que van de $u$ a $w$. Sea $R$ un camino de $u$ a $v$ que no pasa por el vértice $w$, y dicho camino existe porque de lo contrario $w$ sería punto de articulación y el grafo no sería biconexo. Sea $x$ el último vértice común de $R$ con $P$ o $Q$, y supongamos sin pérdida de generalidad que $x \in P$, entonces el camino de $u-x$ por $P$ unido a $x-v$ por $R$ es disjunto en vértices al camino $Q$ unido a $w-v$, por tanto existe un ciclo simple que contiene a $u,v$.

Demostremos que si existe un ciclo simple entre cualesquiera dos vértices entonces el grafo es biconexo. Supongamos que existe al menos un punto de articulación, al eliminarlo se generan al menos dos componentes conexas, sea $u$ y $v$ vértices en distintas componentes conexas, como entre ellos había un ciclo, al eliminar un vértice en un camino entre ellos $\implies$ existe un camino entre ellos, contradición.

## Problema 4

Teorema de conferencia de Coloreo
