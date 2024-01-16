# Soluciones grafo 2 (Matching, Euler y Hamilton)

## Problema 1

> Sea T un bosque de orden $n$, tamaño $m$ y $k$ componentes. Pruebe que $m = n − k$.

Como $T$ es un bosque con $k$ componentes conexas $\implies$ está formado por $k$ árboles $A_1, A_2, \ldots, A_k$ con $n_1, n_2, \ldots, n_k$ vértices respectivamente $\implies n_1 + n_2 + \cdots + n_k = n$, y como son árboles se cumple que si tiene $n_i$ vértices entonces tiene $n_i-1$ aristas, luego, $m = n_1-1 + n_2-1 + \cdots + n_k-1 \implies m = n-k$.

## Problema 2

> Sea $T$ un árbol de orden $n$ que solo contiene vértices de degree 1 o 3. Pruebe que $T$ contiene $\frac{n − 2}{2}$ vértices de degree 3.

Sabemos que en el grafo se cumple que $\sum_{v\in V}deg(v) = 2|E|$ y que $|E| = n-1$.

Supongamos que existen $k$ vértices de grado 3 $\implies 3k + (n-k) = 2(n-1) \implies 2k = n-2$

Por tanto, la cantidad de vértices de degree 3 es $k = \frac{n-2}{2}$.

## Problema 3

> Pruebe que si una arista es insertada entre 2 vértices no adyacentes de un árbol, el grafo resultante contiene exactamente un ciclo.

Sabemos de antemano que contiene al menos un ciclo al insertar la arista $u,v$ (siendo $u$ y $v$ vértices no adyacentes en el árbol) ya que al principio existía solo un camino que unía a $u$ con $v$ y ahora además de ese camino se encuentra la arista añadida. Probemos ahora que no existe ningún otro ciclo.

Supongamos que al añadir la arista $u,v$ se genera al menos otro ciclo (con al menos un vértice distinto al ciclo que ya habíamos analizado), luego, dicho ciclo contendrá la arista $u,v$ y por tanto a los vértices $u$ y $v$, por tanto, existen ahora 3 caminos distintos que conectan a $u$ con $v$ (la arista, el primer camino y el camino contenido en el último ciclo encontrado excluyendo la arista $u,v$), y notemos que entre estos 3 caminos solo 1 contiene a la arista $u,v$ y es precisamente el camino formado por dicha arista, luego, al eliminarla todavía existirán dos caminos que conecten a $u$ con $v$, contradicción porque estamos trabajando en un árbol.

## Problema 4

> Pruebe que todo árbol es un grafo bipartito.

Haciendo $BFS$ a partir de cualquier vértice se le asignan los vértices de distancia par a un conjunto y los de distancia impar al otro.

## Problema 5

> Sea $G$ bipartito y regular de grado $k$, entonces existen $k$ emparejamientos perfectos disjuntos.

Para probar esto basta dado un grafo $G$ bipartito y regular de grado $k$ buscar $k$ emparejamientos perfectos disjuntos.

Sean los vértices del conjunto $A = \{v_1, v_2, \ldots, v_k\}$ y $B = \{v_{k+1}, v_{k+2}, \ldots, v_{k+k}\}$. Formemos los emparejamientos de la siguiente forma:

- El primer emparejamiento será cada vértice $v_i$ de $A$ con el vértice $v_{k+i}$ de $B$.
- El emparejamiento $j-$ésimo toma cada vértice $v_i$ de $A$ con el vértice $v_{k+m}$ de $B$, siendo $m \equiv (j+i) \ mod(k)$.

Para cada vértice en cualquiera de los dos conjuntos entre todos los $k$ emparejamiento se habrá emparejado con exactamente todos los vértices del conjunto opuesto, por tanto, estos $k$ emparejamientos son disjuntos.

## Problema 6

> Sea $G$ de orden $n$ (par), tal que para todos $v,w$ no adyacentes $d(v)+d(w)\geq n-1$. Pruebe que existe un emparejamiento perfecto en $G$.

### `Vía 1`

Como se cumple que para todos $v,w$ no adyacentes $d(v)+d(w)\geq n-1$ entonces el grafo es conexo.

Tomemos el camino más largo $P=\{v_1,v_2,\ldots,v_k\}$, supongamos que $v_1,v_k$ son adyacentes, entonces $P$ es un ciclo. Si $v_1,v_k$ no son adyacentes se cumple que $d(v_1)+d(v_k)\geq n-1$, por tanto, haciendo un razonamiento análogo al del **Problema 15** se cumple que existe un ciclo. Como $P$ es un ciclo, supongamos que existe un vértice en el grafo que no pertenece a este, luego, como es conexo el grafo, algún nodo del ciclo debe estar conectado a ese vértice, por lo que, podríamos seleccionar un camino $P'$ más largo que $P$, contradicción $\implies$ el grafo es hamiltoniano, y como tiene una cantidad par de vértices implica que tiene una cantidad par de aristas en el ciclo, por tanto, existe un emparejamiento que abarca todos los vértices.

### `Vía 2`

Sea $M$ un emparejamiento máximo y supongamos que no es perfecto. Como $n$ es par significa que existen una cantidad par de nodos que no forman parte de $M$.

Sean $u$ y $v$ dos de los vértices no emparejados, sabemos que $d(v)+d(w)\geq n-1$, por tanto o son adyacentes o tienen al menos un vértice en común entre sus adyacentes. Si son adyacentes podemos emparejarlos y obtendríamos un emparejamiento mayor que el emparejamiento máximo, contradicción. Supongamos ahora que tienen al menos un vértice $p$ en común entre sus adyacentes y sabemos que ningún par de vértices no emparejados son adyacentes, porque se podrían emparejar y existiría un emparejamiento mayor que el máximo.

Nótese que existen a lo sumo $\frac{n-2}{2}$ parejas de vértices emparejados y como se cumple que $d(v)+d(w)\geq n-1$ entonces existe al menos una pareja de vértices emparejados $x,y$ tal que $x$ es adyacente con $v$ y $y$ es adyacente con $w$. Supongamos que no, entonces $v$ es adyacente a lo sumo con $\frac{n-2}{2}$ y $w$ es adyacente con a lo sumo los mismos vértices que $v$, al sumar esos degree resulta $n-2$, por tanto, es necesario que en una pareja al menos, uno de los vértices $v$ o $w$ sea adyacente al otro, en cuyo caso, basta con eliminar el emparejamiento $p,q$ y emparejar a $q$ con el que es adyacente a él entre $u$ y $v$ y emparejar $p$ al otro, luego, tendríamos un emparejamiento mayor que el emparejamiento máximo, contradicción. Si $p$ no está emparejado con ningún otro vértice $\implies$ existe otro vértice $q$ que no pertenece a $M$, el cual, es adyacente a $u$ o $v$, y supongamos sin pérdida de generalidad que es adyacente a $v$, entonces, al emparejar $q,v$ y $p,u$ obtendremos un emparejamiento mayor que emparejamiento máximo, contradicción.

Por tanto no existen vértices que no pertenezcan al emparejamiento máximo $\implies$ existe al menos un emparejamiento perfecto.

## Problema 7

> Pruebe que un árbol tiene a lo sumo un emparejamiento perfecto.

Nótese que para que exista un emparejamiento perfecto, los vértices hoja (vértices con degree 1) no pueden tener hermanos hoja, o sea, dos vértices con degree 1 no pueden estar conectados al mismo vértice, por el **Teorema de Hall**

Supongamos que tiene 2 emparejamientos perfectos distintos (existe $u$ que en uno está emparejado con $v$ y en otro con $w$). Como son perfectos y teniendo en cuenta el **Lema 1** (al final de la demostración), al eliminar los subgrafos inducidos por las hojas y sus padres en el árbol, eventuamente llegaremos a uno de los 3 nodos $u,v,w$, el cual será hoja en este árbol resultante, y por tanto, estará conectado solo a un nodo, por tanto, su emparejamiento es único, contradicción. Luego, en un árbol existe a lo sumo un emparejamiento máximo.

> **Lema 1**: Si en un árbol existe un emparejamiento perfecto, al eliminar los subgrafos inducidos por los nodos hoja y el nodo adyacente de cada uno, el árbol o bosque resultante seguirá teniendo un emparejamiento perfecto, distinto del anterior solo que no existen las parejas eliminadas.

Es evidente que los nodos hojas solo pueden estar conectados a un nodo en cualquier emparejamiento perfecto que se haga, y ese es su nodo padre, por tanto, a los nodos padres de las hojas no se les puede emparejar ningún otro nodo del árbol para cualquier emparejamiento perfecto $\implies$ al eliminar los nodos hojas, sus padres y las aristas que inciden sobre ellos, el resto del grafo (no necesariamente conexo) no perdió las aristas que pertenecían al emparejamiento del resto de vértices, por tanto, existe un emparejamiento perfecto de estos vértices igual al original excepto en los vértices eliminados.

## Problema 8

> $G$ tiene una cadena de Euler si y solo si exactamente 2 nodos son de degree impar.

Si $G$ tiene una cadena de Euler $\implies$  exactamente 2 nodos son de degree impar, porque si $G$ tiene un camino que abarca todas las aristas sin empezar y terminar en el mismo nodo, ambos deben tener degree impar (estos nodos son recorridos una vez cuando se empieza y termina, y en el medio del recorrido, cada vez q se entra a uno se debe salir, por tanto su paridad del degree no varía)

Supongamos que en $G$ exactamente 2 nodos son de degree impar. Sean $x$, $y$ dichos nodos, al agregar la arista $x,y$ se cumple que en el grafo todos los nodos son de degree par y por tanto el grafo es euleriano $\implies$ existe un ciclo euleriano, y dicho ciclo pasa por la arista $x,y$ exactamente una vez $\implies$ existe un camino que empieza por $x$ y termina en $y$ que recorre todas las aristas del grafo a excepto $x,y$, por lo cual, al eliminarla esto no se afecta y dicho camino sigue existiendo, el cual, es un camino euleriano

## Problema 9

> La longana más larga posible en el dominó es de 51 fichas.

En el ejercicio estamos tratando de formar la cadena válida más larga con fichas de dominó de 9.

Nótese que en el dominó de 9 hay en total 55 fichas, las cuales podemos ver como aristas de un grafo k10 (porque todos los números se relacionan en cada ficha con los otros), y tendríamos 10 vértices, cada uno de los cuales con 9 aristas.

Estamos buscando un camino Euleriano, pero como todos los vértices tienen grado 9 es imposible, por lo que, si retiramos 4 aristas, obtendríamos que 8 vértices tendrían grado par, y por tanto, 2 serían impares, lo cual es condición necesaria y suficiente para garantizar que exista un camino euleriano.

## Problema 10

> Sea $G$ conexo tal que toda arista está contenida en un número impar de ciclos. Pruebe que $G$ es euleriano.

Para demostrar que $G$ es euleriano basta probar que todos los vértices tienen degree par.

Supongamos que existe un vértice $u$ con degree impar, luego, sean sus vértices adyacentes $v_1, v_2, \ldots, v_k$ con $k$ impar.

### `Vía 1`

Construyamos un grafo $G^*$ con estos vértices tal que, por cada cíclo en $G$ que pase por las aristas $(v_i,u),(u,v_j)$ le agregamos la arista $(v_i,v_j)$ al grafo $G^*$. Nótese que en $G^*$ ocurre que para cada par de vértices pueden haber varias aristas entre ellos, y debido a la forma de construir este grafo se cumple que, por cada ciclo que pase por la arista $v_i,u$ se le suma 1 al degree de $v_i$ en $G^*$. Luego, como cada arista tiene una cantidad impar de ciclos en $G$ se cumple que en $G^*$ todos los vértices tienen degree impar, y como hay una cantidad impar de vértices esto es imposible.

Por tanto como $\not \exists \  G^* \implies \not \exists \ u$ vértice con degree par en $G$ y por tanto todos los vértices tienen grado par.

### `Vía 2`

Construyamos un grafo $G^*$ con estos vértices $v_i$ y con $u$, y por cada ciclo que pase por una arista $(v_i,u)$ o $(u,v_i)$ agreguemos esa arista al grafo $G^*$.

Nótese que nuestro nuevo grafo puede tener múltiples aristas entre dos vértices, y que, si es posible que $u$ en $G$ tenga degree impar y cada arista pertenezca a una cantidad impar de ciclos implica que en $G^*$, como $u$ es adyacente a una cantidad impar de vértices y cada uno le aporta una cantidad impar de aristas, entonces su degree será impar, sin embargo esto no se cumple, ya que, por cada ciclo que pase por una arista $(v_i,u) \implies$ también debe pasar o haber pasado por una arista $(u,v_j)$ y por tanto le suma 2 al degree de $u \implies$ en $G^*$ $u$ tienen degree par.

Por tanto, en $G$ no existen vértices con degree impar $\implies G$ es euleriano.

## Problema 11

> Si $G_1$ y $G_2$ son grafos obtenidos de $G$ con $n \geq 3$ agregando iterativamente pares de vértices no adyacentes tales que sus degrees sumen al menos n, entonces $G_1 = G_2$.

Supongamos que:

- $G_1$ es el grafo formado por añadir las aristas $E=\{e_1, e_2, \ldots, e_n\}$
- $G_2$ es el grafo formado por añadir las aristas $A=\{a_1, a_2, \ldots, a_m\}$

Sabemos que $E,A$ son secuencias válidas de aristas añadidas. Probemos que $A=E$. Sea $a_i$ una arista cualquiera de $A$, se cumple que al añadir las aristas de $E$ en $G_1$, como $A$ es una secuencia válida de aristas, en cualquier momento es necesario para formar la clausura añadir la arista $a_1$, y una vez añadida esta es necesario añadir la arista $a_2$ `and so on` hasta añadir la arista $a_i$. Análogamente se demuestra que si $E$ es una secuencia de aristas válidas para formar la clausura, es necesaro en $G_2$ añadir dichas aristas para formar la clausura.

## Problema 12

> Si $G$ orden 3 o mayor. Pruebe que $G$ es hamiltoniano si solo si $cl(G)$ también lo es.

Si $G$ es hamiltoniano entonces $cl(G)$ también lo es, ya que $\forall v \in V$ se cumple que $deg(v)$ en $G$ es menor o igual que $deg(v)$ en $cl(G)$. Demostremos que si $cl(G)$ entonces $G$ lo es.

Tomemos dos vértices adyacentes $u$ y $v$ en $cl(G)$ (sabemos que es hamiltoniana) que no sean adyacentes en $G$, se cumple que $deg(v)+deg(u) \ge n$, y eliminemos la arista $(u,v)$ del grafo. Producto del **Teorema de Bondy Chvatal** se cumple que el grafo resultante es hamiltoniano.

Haciendo esto por cada par de vértices adyacentes en $cl(G)$ (por lo que dichos vértices cumplen que  $deg(v)+deg(u) \ge n$), se cumple que después de cada operación el grafo resultante será cada vez más parecido a $G$ y será hamiltoniano, hasta obtener $G$ por completo.

## Teorema de Bondy Chvatal

> Sea $G$ un grafo con $u,v$ dos vértices no adyacentes tales que $deg(u) + deg(v) ≥ n$. Entonces $G$ es hamiltoneano si y solo si $G + (u,v)$ es hamiltoneano.

Si $G$ es hamiltoniano, al agregar una arista seguirá siendo hamiltoniano.

Supongamos que $G + (u,v)$ es hamiltoneano, por tanto existe un ciclo de hamilton, y al eliminar la arista $(u,v)$ se cumple que existe un camino de hamilton $P=\{u=v_1,v_2,\ldots,v_n=v\}$.

Como $deg(u) + deg(v) \ge n$ y la arista $(u,v)$ no existe $\implies$ $u,v$ tienen en $P$ dos vértices en común y se cumple que existen $v_{i-1},v_i$ tal que las aristas $(u,v_i)$ y $(v_{i-1},v)$ existen en el grafo. (demostrado intra 2do 2023).

Por tanto, al eliminar la arista $(u,v)$ existe un ciclo en el grafo y es $\{v_1, v_i, \ldots, v_n, v_{i-1}, \ldots, v_2\}$.

## Problema 14

> Pruebe que $K_{n,n+1}$ es no hamiltoniano para todo $n\geq 1$.

Supongamos que el grafo $G = K_{n,n+1}$ es hamiltoniano, y sean $u,v$ dos vértices de conjuntos distintos.

Nótese que si quitamos la arista $(u,v)$ existe en el grafo un camino hamiltoniano $P=\{u=v_1,v_2, \ldots, v_n, \ldots, v_{2n+1}=v \}$ donde los vértices impares se encuentran en un subconjunto y los pares en otro. Sin pérdida de generalidad sea $u \in A_n$ perteneciente al subconjunto con $n$ elementos y $v\in A_{n+1}$. Como $P$ lo comenzamos en $u$ y $|A_n| \lt |A_{n+1}|$ se cumple que es imposible pasar por todos los nodos una sola vez, ya que en cada momento hay que seleccionar un vértice distinto en un subconjunto distinto, y el conjunto por el que empezamos tiene menos vértices que el otro.

## Problema 15

> Sea $G$ un subgrafo abarcador de $K_{n,n}(n\geq 2)$ cuyas particiones son $V_1$ y $V_2$. Sean $u\in V_1$ y $v\in V_2$ tales que $d(u)+d(u)\gt n$. Pruebe que $G$ es hamiltoniano si solo si $G+uv$ también lo es.

Si $G$ es hamiltoniano, al agregar una arista seguirá siendo hamiltoniano.

Supongamos que $G + (u,v)$ es hamiltoneano, por tanto existe un ciclo de hamilton, y al eliminar la arista $(u,v)$ se cumple que existe un camino de hamilton $P=\{u=u_1, v_1, u_2, v_2, \ldots,u_n, v_n=v\}$.

Como $d(u)+d(u)\gt n$ significa que existe $i$ tal que las aristas $(u_i,v)$ y $(u,v_{i+1})$ existen en el grafo. Para demostrar esto tomemos los vértices en el orden de $P$ por parejas $\implies$ son $\frac{n-2}{2}$ parejas, quitando la primera y la última que es donde se encuentran $u$ y $v$, luego, entre dichos vértices deben seleccionar más de $n-2$ para ser adyacentes a un vértice, luego, por Principio del Palomar se cumple que en una pareja deben existir vértices adyancentes, y por la forma de escoger las parejas se cumple lo que queríamos demostrar. Por último, como las aristas $(u_i,v)$ y $(u,v_{i+1})$ existen en el grafo, teniendo en cuenta el orden de los vértices en $P$ obtenemos el ciclo.

$$
\cdots
$$

## Problema 13

> Si $G$ es conexo, bipartito y regular de grado $k$ entonces es 2-conexo.

## Problema 16

> Pruebe que el grafo de Petersen es no hamiltoniano.
> ![grafo de Petersen](image.png)
