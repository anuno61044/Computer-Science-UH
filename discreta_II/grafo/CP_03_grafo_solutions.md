# Soluciones CP3 Coloreo

## Problema 1.1

> Demuestra que $\mathcal{X}(K_n) = n$ para todo $n \in \mathbb{N}$

Procedamos por inducción, demostremos que para todo clique de $n$ vértices se cumple que su número cromático es $n$.

Caso base $n=0, n=1$, cuyos números cromáticos son 0 y 1 respectivamente.

Supongamos que un clique de $k$ vértices tiene como número cromático $k$, nótese que al agregar un vértice, para formar un clique este debe conectarse a los $k$ vértices, y por tanto, no puede ser coloreado de uno de esos $k$ colores porque es adyacente a esos vértices, entonces requiere un nuevo color y el cloque resultante tiene como número cromático $k+1$

Nótese que $K_n$ es un clique de $n$ vértices, por lo que $\mathcal{X}(K_n) = n$

## Problema 1.2

> Demuestra que $\mathcal{X}(C_n) = 2$ si $n$ es par y $\mathcal{X}(C_n) = 3$ si $n$ es impar

La coloración en ambos se obtiene alternando dos colores entre vértices adyacentes, excepto cuando $n$ es impar, ocurriendo que en el último vértice a colorear, el anterior es de un color y el primero coloreado de otro, por lo tanto este debe tener un nuevo color.

## Problema 1.3

> Demuestra que $\mathcal{X}(P_n) = 2$ para todo $n \geq 2$

El coloreo se obtiene alternando de un color a otro con 2 colores.

## Problema 2

> Sea $\mathcal{G}$ un grafo tal que $\mathcal{X(G)} = k$. Demuestre que existen al menos k vértices en $\mathcal{G}$ con grado mayor o igual que $k - 1$.

Sabemos que $\mathcal{X(G)} = k$, por tanto tiene un subgrafo $H$ que es $k$-crítico, el cual cumple que al menos tiene $k$ vértices (porque es $k$ coloreable) y además $\delta(H) \ge k-1$, por tanto todos sus $k$ vértices tienen grado $k-1$ o superior.

Para demostrar esto último ($\delta(H) \ge k-1$ en un $k$ crítico) supongamos lo contrario, que existe un vértice $u$ con $deg(u) \le k-2$, al eliminar el vértice, el grafo resultante es $k-1$ coloreable, y al añadirlo nuevamente, como es adyacente a $k-2$ vértices a lo sumo, basta con colorearlo con el color $k-1$, por tanto, el grafo resultó en que no era $k$ crítico

## Problema 3

> Sea $G$ un grafo conexo  de orden $n$ y tamaño $m \leq n$. Prueba que $G$ es 3-coloreable.

Si es conexo de orden $n$ y tamaño $m \leq n \implies$ o es un árbol o es un ciclo.

En caso que el grafo sea un árbol se cumple que es 2-coloreable, ya que, teniendo en cuenta las profundidades en el árbol tomando a un vértice como raíz, a cada una le asignamos uno de ds colores alternadamente.

En caso que sea un ciclo ya probamos que o es 2-coloreable o 3-coloreable.

## Problema 4.1

> Sea $\mathcal{G}$ un grafo de orden n. Demuestre que: 
> 
> $$n \leq \mathcal{X(G)} * \mathcal{X(G^C)} \leq (\frac{n + 1}{2})^2$$

Nota: sea $\alpha(G)$ el mayor número de vértices independientes y $\omega(G)$ la cardinalidad del mayor clique.

Sea $\mathcal{X(G)}=k \implies n=n_1+n_2+\cdots+n_k$ donde $n_i$ representa la cantidad de vértices que poseen el color $i$. Nótese que $\forall i \implies n_i \le \alpha(\mathcal{G})$, o sea, cada conjunto de vértices 1 coloreable en el grafo son menores que la cantidad de vértices independientes, y por tanto $n \le k\times \alpha(\mathcal{G})$.

Sin embargo, el mayor conjunto independiente en el grafo $G$ equivale al mayor clique en el grafo complemento, por lo que, $\alpha(\mathcal{G}) = \omega(\mathcal{G^c})$

$$n \le k \times \omega(\mathcal{G^c})$$

Luego, sabemos que el número cromático de un grafo es mayor o igual que el mayor de todos los cliques contenidos en este, por tanto:

$$n \le k \times \omega(\mathcal{G^c}) \le k \times \mathcal{X(G^c)} =\mathcal{X(G)} \times \mathcal{X(G^c)}$$

Demostremos ahora que $\mathcal{X(G^c)}+\mathcal{X(G)} \le n+1$. Supongamos lo contrario, entonces, siendo $\mathcal{X(G^c)}=k_1$ y $\mathcal{X(G)}=k_2$ se cumple que:

$$k_1+k_2 \gt n+2$$

Tomemos en cada uno un subgrafo $k_1$ crítico en $\mathcal{G}$ y $k_2$ crítico en $\mathcal{G^c}$, y analicemos que, por propiedad de grafo $k$ crítico se cumple que:

- En $\mathcal{G}$ existen $k_1$ vértices con $deg \ge k_1-1$
- En $\mathcal{G^c}$ existen $k_2$ vértices con $deg \ge k_2-1$

Como $k_1+k_2 \gt n+2$ significa que hay al menos un vértice que cumple con ambas condiciones en $\mathcal{G}$ y $\mathcal{G^c}$, pero sabemos que para todo vértice se cumple que: $deg_{\mathcal{G}}(u)+deg_{\mathcal{G^c}}(u)=n-1$, o sea, la cantidad de vértices adyacentes en el grafo y en su complemento de cualquier vértices abarca a todos los demás vértices, más sin embargo, por el razonamiento anterior se cumple que existe un vértice $v$ tal que en $\mathcal{G}$ ocurre que $deg(v)\ge k_1-1$ y en $\mathcal{G^c}$ que $deg(v)\ge k_2-1$, luego:

$$deg_{\mathcal{G}}(v)+deg_{\mathcal{G^c}}(v) \ge k_1+k_2-2 \gt n+2-2=n$$

Contradicción, por tanto $k_1+k_2 \le n+1$. Luego, por media aritmética-media geométrica se cumple que:

$$\sqrt{k_1\times k_2} \le \frac{k_1+k_2}{2} \le \frac{n+1}{2}$$

$$\implies k_1\times k_2 \le (\frac{n + 1}{2})^2$$

$$\therefore n \leq \mathcal{X(G)} \times \mathcal{X(G^C)} \leq (\frac{n + 1}{2})^2$$

## Problema 4.2

> Sea $\mathcal{G}$ un grafo de orden n. Demuestre que: 
> 
> $$2 \sqrt{n} \leq \mathcal{X(G)} + \mathcal{X(G^C)} \leq n + 1$$

Sabemos por el ejercicio anterior que $\mathcal{X(G)} + \mathcal{X(G^C)} \leq n + 1$ por lo que bastaría probar que $2 \sqrt{n} \leq \mathcal{X(G)} + \mathcal{X(G^C)}$.

Sin embargo, por las desigualdades anteriores se cumple que: 

- $n \leq \mathcal{X(G)} * \mathcal{X(G^C)}$
- $2\times \sqrt{\mathcal{X(G)} * \mathcal{X(G^C)}} \le\mathcal{X(G)} + \mathcal{X(G^C)}$

Y uniendo ambas desigualdades obtenemos que $2 \sqrt{n} \leq \mathcal{X(G)} + \mathcal{X(G^C)}$.

## Problema 6

> Sea $\mathcal{G}$ un grafo de orden $n$ y $\delta(\mathcal{G}) \geq d$. Demuestra que $\mathcal{X(G)} \geq \frac{n}{n - d}$.

Basta con demostrar que $(n-d) \times \mathcal{X(G)} \geq n$.

Sabemos del **Problema 4** que $\alpha(\mathcal{G})\times\mathcal{X(G)} \geq n$. Supongamos que $\alpha(\mathcal{G}) \gt (n-d)$, entonces existe un conjunto independiente $I$ de vértices tal que $|I| \gt (n-d)$ y por tanto, fuera de ellos hay una cantidad de vértices menor que $d \implies$ para todos los vértices en $I$ se cumple que son adyacentes a al menos un vértice de dicho conjunto, porque $\delta(\mathcal{G}) \geq d$, por tanto no son independientes.

Luego, se cumple que $(n-d) \ge \alpha(\mathcal{G})$, por lo que:

$$(n-d) \times \mathcal{X(G)} \geq n$$

$$\cdots$$

## Problema 5

> Demuestre que para todo grafo $\mathcal{G}$ de tamaño $m$ se cumple que $\omega (\mathcal{G}) \leq \mathcal{X(G)} \leq \frac{1}{2}(1 + \sqrt{8m + 1})$.



## Problema 7

> Demuestra que si $d_1$, $d_2$, ... , $d_n$ es la secuencia no creciente de grados de un grafo $\mathcal{G}$ entonces $\mathcal{X(G)} \leq 1 + \max_{1 \leq i \leq n}\{min(d_i, i - 1)\}$.

## Problema 8

> Sea $\mathcal{G}$ un grafo donde todo par de ciclos de longitud impar tiene al menos un vértice común. Demuestre que $\mathcal{X(G)} \leq 5$.