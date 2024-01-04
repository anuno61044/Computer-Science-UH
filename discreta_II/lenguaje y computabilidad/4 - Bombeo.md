# Pumping Lemma

##### (O Lema del Bombeo para los amigos)

> Sea $L$ un lenguaje regular. Existe entonces una constante $n$ (que depende de $L$) tal que para toda cadena $w$ perteneciente a $L$ con $|w| ≥ n$, podemos descomponer $w$ en tres cadenas, $w = xyz$, tales que:
>
> 1. $|y| \gt \empty$ .
> 2. $|xy| \le n$.
> 3. Para todo $k ≥ 0$, la cadena $xy^kz$ también pertenece a $L$.

Es decir, siempre podemos hallar una cadena no vacía y no demasiado alejada del principio de $w$ que pueda *“bombearse”*; es decir, si se repite y cualquier número de veces, o se borra (el caso en que $k = 0$), la cadena resultante también pertenece al lenguaje L.

## Ejercicio 1

> Determine si el lenguaje $\{a^nb^m | n = 2m\}$ es regular

Supongamos que el lenguaje es regular, entonces $\exist n \ | \ \forall w \in L$ se cumple que $w=xyz$ con $|xy| \le n$ y $|y| \gt 0$.

Tomemos la cadena $w = a^{2n}b^n \in L$, luego por el **Lema del Bombeo** se cumple que $w = xyz$ donde $|xy| \le n \implies xy \subseteq a^n$, por lo que $y$ está compuesto solo por $a$ y no es vacío, luego, siendo $|y| = m$, como $xz \in L$ por el **Lema del Bombeo** resulta que la cadena $a^{2n-m}b^n \in L$ con $m \gt 0 \implies$ esta cadena no pertence al lenguaje, lo cual es una contradicción, por tanto el lenguaje $L$ no es regular.

> 2. $\{x \in \{a,b,c\}^*\  | \ x$ es un palíndromo, $x=rev(x)\}$

Supongamos que el lenguaje es regular, entonces por el **Lema del Bombeo** $\exist n \ | \ \forall w \in L$ se cumple que $w=xyz$ con $|xy| \le n$ y $|y| \gt 0$.

Tomemos la cadena $w = 0^n110^n$, de la cual, dado que $|xy| \le n \implies xy \subseteq 0^n$, por lo que, según el lema la cadena $xy^2z \in L$, lo cual genera una contradicción porque, dado que $|y| \gt 0 \implies xy^2z = 0^p110^n$ donde $p > n \implies$ no pertenece a $L$, contradición, por lo que $L$ no es regular.

## Ejercicio 10

> \* Determine si el lenguaje $\{0^n | n$ es un cubo perfecto $\}$ es regular.

Supongamos que el lenguaje es regular, entonces por el **Lema del Bombeo** $\exist n | \forall w \in L$ se cumple que $w = xyz$ con $|xy| \le n$ y $|y| \gt \empty$.

Sea la cadena $w = 0^{(n+1)^3} = 0^{n^3}0^{3n^2}0^{3n}0 = 0^n0^{n^3}0^{3n^2}0^{2n}0$. Como $|xy| \le n \implies xy \subseteq 0^n$.

Según el lema, la cadena $w' = xy^kz \in L \ \ \forall k \in \Z$, por lo que, haciendo $k=0$ se cumple que $xz \in L$, y suponiendo que $x=0^q$ donde $q < n$ (porque $|y| > 0$) $\implies 0^{n^3}0^{3n^2}0^{2n}0^q0 \in L$, cumpliéndose que $n^3 < n^3 + 3n^2 + 2n+q + 1 < (n+1)^3 \implies n^3 + 3n^2 + 2n+q + 1$ no es un cubo perfecto, por lo que la cadena $w' \not \in L$, lo cual es una contradicción, y por tanto $L$ no es regular

## Ejercicio 17

> \*\* Determine si el lenguaje del conjunto de cadenas de la forma $0^{i}1^{j}$ tal que $mcd(i,j)=1$ es regular.

Supongamos que el lenguaje es regular, entonces por el **Lema del Bombeo** $\exist n \ | \ \forall w \in L$ se cumple que $w=xyz$ con $|xy| \le n$ y $|y| \gt 0$.

Tomemos la cadena $w=0^n1^p$ con $p$ el mayor primo más cercano a $n$. Si $w=xyz$ entonces siendo $n=m+r$ y $q > 0$ se cumple que:

- $x = 0^{m-q}$
- $y = 0^q$
- $z = 0^r1^p$

Luego, si existe $i$ tal que al bombear $i$ veces la subcadena $y$ se cumple que $w = 0^{n+q(i-1)}1^p$ no pertenece al lenguaje entonces el lenguaje $L$ no es regular, por lo que debe cumplirse que $n+q(i-1) \equiv 0 \ mod(p) \implies q(i-1) \equiv -n \ mod(p)$.

Recordemos que una ecuación de congruencia lineal $ax \equiv b \ mod(n)$ tiene solución $\iff \ mcd(a,n) | b$. Como $n < p$ y $q < n \implies q < p \implies mcd(q,p)=1$  por lo que existe $i$ tal que se cumple que $n+q(i-1) \equiv 0 \ mod(p)$ por lo que la cadena no pertenece al lenguaje $\implies L$ no es regular.
