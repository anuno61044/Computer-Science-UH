# Soluciones Grafo 1

## Problema 1

> Demuestre que en un grafo la cantidad de vértices de grado impar es par.

Sabemos que $\sum_{v \in V}d[v] = 2|E|$, por tanto, si la suma de los degree de los vértices de un grafo es par $\implies$ no puede haber una cantidad impar de vértices con degree impar, porque la suma daría impar.

## Problema 2

> Demuestre que para cualquier número de personas, no es posible que todas conozcan una cantidad distinta de personas.

Nota: tenemos en cuenta que la relación conocer es simétrica y no reflexiva

Supongamos que tenemos $n$ personas, de las cuales cada una de ellas conoce a al menos una persona (las personas que tienen 0 conocidos no aportan nada, y el problema en cuestión sería equivalente a hacer el análisis con una persona menos). Nótemos que la persona que menos conocidos tiene cuenta con 1 conocido, y la persona que más conoce cuenta con $n-1$, luego, por principio de las casillas existen al menos dos personas entre las $n$ del grupo que tienen la misma cantidad de conocidos.

## Problema 3

> Demuestre que si $G$ y $H$ son isomorfos por un isomorfismo $f$, entonces el $deg(v)$ vértice de G es igual al $deg(f(v))$ vértice de H. 

Sea $S_G = \{u \in V_G: v,u \in E_G\}$ y $S_H = \{f(u) \in V_H: f(v),f(u) \in E_H\}$. Nótese que $|S_G| = d[v]$ y $|S_H| = d[f(v)]$, luego, por definición de grafos isomorfos, si $u,v \in E_G \implies f(u),f(v) \in E_H$, entonces se cumple que $|S_G| \le |S_H| \implies d[v] \le d[f(v)]$.

Análogamente se demuestra que $d[f(v)] \le d[v]$ utilizando el isomorfismo inverso $f^{-1}: H$ -> $G$

## Problema 3.1

> Demuestre que si dos grafos son isomorfos, entonces, tienen la misma cantidad de aristas.

Utilizando la definición de grafos isomorfos, si $u,v \in E_G \implies f(u),f(v) \in E_H$, se puede demostrar que $|E_G| \le |E_H|$ y luego con el isomorfismo inverso que $|E_H| \le |E_G| \implies |E_G| = |E_H|$

## Problema 4

> 4. Demuestre que las siguientes definiciones son equivalentes:
>     1. $G$ es un grafo acíclico y conexo
>     2. $G$ es acíclico y $|E| = n-1$
>     3. $G$ es conexo y $|E| = n-1$
>     4. $G$ es conexo pero si se suprime una arista cualquiera, deja de serlo
>     5. $G$ no tiene ciclos, pero si se añade una arista entre vértices no adyacentes, entonces se crea exactamente uno
>     6. Todo par de vértices de G está conectado

Para demostrar la equivalencia de estas proposiciones demostremos que:

$$1 \implies 2 \implies 3 \implies 4 \implies 5 \implies 6 \implies 1$$

> **Lema 1**: Al añadir una arista a una componente conexa acíclica se crea un ciclo.

Sea $u,v$ la arista que será añadida (por tanto antes de la operación no existe). Como es una componente conexa acíclica, para cada par de vértices existe un camino que los une, luego, existe un camino de $u$ a $v$ que pasa por al menos dos aristas, al añadir la arista $u,v$ se cumple que ahora hay dos caminos disjuntos en vértices (sin contar a $u$ y $v$) que unen a $u$ y $v$ $\implies$ existe un ciclo.

> $1 \implies 2$

Partimos de que $G$ es un grafo acíclico y conexo. Sea el grafo $G$ con solo sus $n$ vértices, por lo que inicialmente tenemos $n$ componentes conexas. Nótese que al agregar una arista, esta unirá dos componentes conexas, ya que no puede pasar que la arista sea añadida a una componente conexa porque en ese caso se crearía un ciclo (por Lema 1). Por tanto, para garantizar que el grafo $G$ continue siendo acíclico se deben unir las $n$ componentes conexas con $n-1$ aristas, luego de esto el grafo quedaría conexo y no pueden haber más aristas por añadir porque $G$ dejaría de ser acíclico.

> $2 \implies 3$

Se cumple que $G$ es acíclico y $|E| = n-1$. Siguiendo una idea similar a la anterior, al quitar las $n-1$ aristas resultan $n$ componentes conexas, y al colocarlas, el número de componentes conexas por cada arista disminuye en 1 (por Lema 1), por tanto, al colocarlas todas quedará una componente conexa $\implies G$ es conexo y por hipótesis cuenta con $n-1$ aristas.

> $3 \implies 4$

Sea $G$ conexo y $|E| = n-1 \implies$ para todo par de vértices en $G$ se cumple que existe solo un camino entre ellos, por tanto, al eliminar la arista $u,v$ se cumple que no existe un camino de $u$ a $v \implies$ las componentes conexas de $u$ y $v$ son distintas.

> $4 \implies 5$

$G$ es conexo pero si se suprime una arista cualquiera, deja de serlo $\implies$ es acíclico. Luego, al añadir una arista entre vértices no adyacentes se cumple que existen dos caminos disjuntos entre estos vértices, por tanto, existe un ciclo.

$$\cdots$$

## Problema 5

> Demuestre que si $C$ es un clique e $I$ es un conjunto independiente, $|C\cap I|\leq 1$.

Supongamos que $C$ e $I$ no tienen vértices en común, entonces $|C\cap I|= 0$. Demostremos que si tienen vértices en común debe ser solo 1.

Supongamos que tienen $k$ vértices en común, con $k \gt 1$, luego, como dichos $k$ vértices pertenecen a $C \implies$ están conectados entre si, pero como pertenecen a $I \implies$ no están conectados entre si, contradicción. Por tanto $|C\cap I|\leq 1$

## Problema 9

> Demuestre que si para todo par de vértices no adyacentes $v,w$ se cumple que $deg(v)+deg(w) \geq n-1$, entonces $G$ es conexo

Supongamos que existen dos componentes conexas, y de cada una seleccionamos un vértice $u$ y $v$. Nótese que $deg(u) + deg(v) \le n-2$ y como para todo par de vértices no adyacentes $v,w$ se cumple que $deg(v)+deg(w) \geq n-1$ entonces significa que al menos uno de los dos vértices está conectado a alguno de la otra componente conexa, lo cual, las conectaría en una sola $\implies G$ es conexo.

## Problema 10

> Demuestre que si $\Delta$(G) + $\delta(g)\geq n-1$, entonces $D(G) \leq 4$

Nótese que si $\Delta$(G) + $\delta(g)\geq n-1$ significa que la suma de los degree de cualquier par de vértices del grafo lo cumple, por tanto, para todos los vértices o están conectados con el vértice $\Delta$(G) o tienen con él un adyacente en común. Por tanto, la mayor de todas las distancias entre un par de vértices será a lo sumo a través de un vértice conectado a $\Delta$(G), o sea, de $v$ a $u$ es necesario pasar por $v'$, luego a $\Delta$(G), luego a $u'$ y finalmente llegar a $u$, lo cual, resulta en un camino de tamaño 4, y este es el caso extremo, por tanto $D(G) \leq 4$

## Problema 11

> Demuestre que la cantidad de componentes conexas de $G$ es mayor igual que $n - m$

Nótese que si eliminamos todas las aristas y las añadimos una a una ocurre que se conectarán a lo sumo dos cmponentes conexas distintas, por lo que el número de componentes conexas en cada paso se mantiene o disminuye en 1. Como inicialmente teníamos 0 aristas y $n$ vértices $\implies$ teníamos $n$ componentes conexas $\implies CC(0) = n-0$ y en el paso $k$ se cumple que $CC(k) \ge n-k$, lo cual demuestra el ejercicio.

## Problema 12

> Demuestre que en todo grafo con al menos 6 vértices, entonces $\alpha \geq 3$ o $\omega \geq 3$

Supongamos que hay más de 2 componentes conexas, basta tomar un vértice de cada una y tendremos un conjunto independiente $\omega \geq 3$.

En caso de haber dos, por Principio de las Casillas existe una que tiene al menos 3 vértices, si de ellos hay dos que no están conectados, al tomarlos junto a uno de la otra CC tendríamos un $\omega \geq 3$, si no existen dos vértices que no están conectados entonces tenemos un clique que cumple que $\alpha \geq 3$.

Supongamos que el grafo es conexo Si existe un ciclo de tamaño 3 ya se cumple que $\alpha \geq 3$. Sea $\Delta(G) > 2$, si el vértice de mayor degree está conectado a más de 2 vértices y ninguno de estos está conectado con otro obtendremos  $\alpha \geq 3$, y si existen al menos dos que están conectados entonces $\omega \geq 3$. Sea $\Delta(G) \le 2$, como el grafo es conexo $\implies \Delta(G) = 2$, . . .

## Problema 13

> Demuestre que si $\sum_{i \in V(G)} {deg(i)\choose2} \gt {n \choose 2}$ G 

Nótese que $\sum_{i \in V(G)} {deg(i)\choose2}$ cuenta todos los posibles caminos de longitud 2 que existen en el grafo y ${n \choose 2}$ cuentos los posibles pares de nodos del grafo. Como se cumple que $\sum_{i \in V(G)} {deg(i)\choose2} \gt {n \choose 2}$ entonces por Principio de las Casillas existen al menos dos caminos de longitud dos cuyos extremos son iguales, por tanto, obtendríamos un ciclo de tamaño 4.

## Problema 14

> Demuestre que $G$ es conexo o su complemento lo es.

Supongamos que $G$ no es conexo $\implies$ tiene $k > 1$ componentes conexas. Sea $CC[0]$ una de ellas, nótese que para cada nodo de $CC[0]$ se cumple que no está conectado con ningún nodo de las otras componentes conexas, por lo que en el grafo complemento si estaría conectado. Basta analizar ahora la conectividad en el grafo complemento de los nodos de $CC[0]$, y vemos que cada uno de ellos se encuentra conectado con los nodos de otra componente conexa, que a su vez están conectados con los nodos de $CC[0]$, por tanto, entre ellos también estarán conectados.

## Problema 15

> Demuestre que si $v$ es punto de articulación de un grafo G conexo, entonces al quitar $v$, la cantidad de componentes conexas es a lo
sumo $deg(v)$.

Sabemos que $v$ es punto de articulación, por lo que al eliminarlo aumenta el número de componentes conexas en el grafo. 

Supongamos que al hacer esa operación la cantidad de componentes conexas resulta en más de $deg(v)$, luego, al conectar $v$ como antes, cada una de esas componentes conexas no estaban unidas entre ellas, sino a través de $v$, y como hay más de $deg(v)$ significa que $deg(v)$ es ahora mayor de lo que era antes, contradicción.

## Problema 16

> Demuestre que si $\delta(G) \geq 3$ existe un ciclo de longitud par.

Tomemos $w$ como el camino más largo del grafo, cuyos extremos son $w[0]$ y $w[k]$ (el camino tiene longitud $k$). Nótese que $w[0]$ debe tener al menos dos aristas más, y dichas no pueden estar conectadas con nodos externos al camino porque sino $w$ no sería el camino más largo. Al conectar $w[0]$ con algún nodo del camino se forma al menos un ciclo, como debemos conectar dos supongamos que los dos ciclos evidentes que se forman tienen longitud par, y sean esos ciclos:

- $w[0], w[1], \ldots, w[i], w[0]$
- $w[0], w[1], \ldots, w[j], w[0]$

Como los ciclos supusimos que eran impares, entre el nodo $w[i]$ y el nodo $w[j]$ hay una cantidad par de nodos, por lo que, el ciclo siguiente es de tamaño par:

$w[0], w[i], \ldots, w[j], w[0]$

## Problema 18

> Demuestre que si $m \geq \frac{(n-1)*(n-2)}{2} +1$, entonces G es conexo.

Demostremos que la mayor cantidad de aristas que debe tener un grafo para que no sea conexo es menor o igual que $m \geq \frac{(n-1)*(n-2)}{2} +1$.

Supongamos que tenemos más de dos componentes conexas, luego, podemos unir dos de ellas con una arista y el grafo segirá siendo no conexo, por lo que la cantidad de aristas no es la mayor.

Tenemos dos componentes conexas densas (o sea que cada una no admite más aristas) $C1$ y $C2$, supongamos que $|V(C1)| \ge |V(C2)|$, luego, si tomamos un nodo de $C2$, lo extraemos y agregamos a $C1$ con la cantidad de aristas necesarias para seguir manteniendo la densidad de la componente conexa nos damos cuenta que la cantidad de aristas del grafo aumenta, y esto se puede seguir haciendo hasta que quede una componente conexa de un nodo y el resto de nodos en la otra, en cuyo caso, la cantidad de aristas sería máxima y tendríamos $\frac{(n-1)*(n-2)}{2}$ aristas, por lo que, al agregar una más nos aseguramos que el grafo sea conexo.

## Problema 19

> Demuestre que todo arbol con vértices de grado $k$ tiene al menos $k$ vértices de grado 1.

Sea $v$ un vértice de grado $k$ y tomémoslo como raíz del árbol y se cumple que $v$ tiene $k$ hijos. Como todo árbol es acíclico, descendiendo por cada vértice del árbol llegamos a un nodo hoja, el cual tiene grado 1, por tanto, tendríamos $k$ vértices de grado 1.

## Problema 20

> Demuestre que si G es un grafo sin vértices aislados que no tiene subgrafo inducido con exactamente 2 aristas, entonces G es un grafo completo.

Supongamos que $G$ tiene más de una componente conexa, si tomamos dos nodos de cada una que estén conectados entre ellos (ya que no tiene nodos aislados) vemos que consituyen un subgrafo inducido con exactamente dos aristas, lo cual incumple la condición inicial.

Por tanto, $G$ es conexo, luego, tomemos dos nodos que no estén conectados entre ellos, por hipótesis cada uno se encuentra conectado a al menos otro nodo porque no existen nodos aislados, y si tomamos esos nodos y un nodo al cual cada uno se encuentra conectado (pueden ambos estar conectados al mismo nodo), el subgrafo inducido por dichos nodos tendría exactamente dos aristas $\implies$ para todo par de nodos se cumple que deben estar conectados por una arista $\implies G$ es completo.

## Problema 21

> Demuestre que todo grafo $G$ contiene un subgrafo bipartito $G'$ tal que $|E(G')| \geq \frac{|E(G)|}{2}$

Procedamos por inducción en la cantidad de vértices.

Supongamos que en un grafo de $k$ vertices se cumple, luego, en un grafo de $k+1$, al eliminar un vértice podemos encontrar un subgrafo de este que cumpla la condición, luego, al agregar el vértice removido, lo podemos ubicar en uno de los dos conjuntos de la bipartición, supongamos que este vértice aporta $e$ aristas, luego, tomamos el conjunto que menos vértices adyacentes tenga y lo insertamos ahí, e insertamos también en la bipartición todas las aristas de dicho vértice hacia el otro conjunto, las cuales serán $\ge \frac{e}{2}$ (notemos que en la bipartición se encuentran todos los vértices del grafo para garantizar que se cumpla la condición)

$$........$$

## Problema 7

> Demuestre que $G$ existe una cadena cerrada de Euler si y sólo si todos sus vértices tienen grado par.

Sabemos que:

- una cadena es un camino que no repite vértices
- una cadena de Euler es una cadena que abarca todas las aristas del grafo
- una cadena cerrada es una cadena que comienza y termina en el mismo vértice

Supongamos que existe un vértice de grado impar, luego, dicha cadena cerrada de Euler debe comenzar en este vértice porque debe abarcar todas las aristas sin repetición, pero como es cerrada debe terminar en el vértice, sin embargo, como tiene degree impar esto no es posible, contradición.

## Problema 17

> Demuestre que si $n \geq 9$, entonces $\alpha(G) \geq 4$ o $\omega(G) \geq 3$.




