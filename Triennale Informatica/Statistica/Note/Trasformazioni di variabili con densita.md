---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Trasformazioni di variabili con densità
---
Sia $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] con valori in uno spazio continuo e sia $f$ una [[Funzioni|trasformazione]]; vogliamo studiare la variabile trasformata $Y=f(X)$ e capire come si ottiene la sua densita a partire da quella di $X$.

Questo e il problema generale delle **trasformazioni di variabili con densita**. In generale non e detto che $Y$ abbia densita, e anche quando la densita esiste non c'e una formula unica valida per ogni trasformazione. Un primo approccio consiste nel passare dalla _[[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]]_ di $Y$. Nel caso monodimensionale $$F_Y(y)=\mathcal{P}\{Y\le y\}=\mathcal{P}\{f(X)\le y\}$$e, se $F_Y$ e sufficientemente regolare, allora$$p_Y(y)=\dfrac{dF_Y(y)}{dy}$$

#### Regola del cambio di variabile
La **regola del cambio di variabile** e un'applicazione di questa idea nel caso in cui la trasformazione sia [[Applicazioni tra insiemi|invertibile e regolare]]. In tale contesto esiste una formula esplicita che esprime la densita della variabile trasformata in funzione della densita iniziale e della deformazione locale indotta da $f$.

Nel caso generale, se $X\in\mathbb{R}^n$, $Y=f(X)$ e $f:A\to B$ e invertibile con inversa regolare, allora la densita si trasforma secondo$$p_Y(y)=p_X(f^{-1}(y))\left|\det J_{f^{-1}}(y)\right|$$Il fattore $\left|\det J_{f^{-1}}(y)\right|$ ovvero il [[Determinante di una matrice|determinante]] della [[Jacobiana di una funzione|jacobiana]] misura come la trasformazione inversa deformi localmente aree o volumi. Questa e la forma naturale della regola in piu dimensioni, 

il caso **monodimensionale** si ottiene come sua specializzazione quando $n=1$, poiche in una dimensione il [[Jacobiana di una funzione|jacobiano]] coincide con la derivata. Se infatti $X$ e una variabile aleatoria reale con densita $p_X$, $f:A\to B$ e una [[Funzioni|funzione biunivoca]] tra intervalli aperti e $f,f^{-1}\in C^1$, allora la formula precedente diventa$$p_Y(y)=
\begin{cases}
p_X(f^{-1}(y))\left|\dfrac{df^{-1}(y)}{dy}\right| & y\in B \\
0 & y\notin B
\end{cases}$$Questa e quindi la forma **monodimensionale** della regola del cambio di variabile.

_Dimostrazione nel caso monodimensionale_: poiche una funzione biunivoca definita su un intervallo e necessariamente strettamente monotona, i casi possibili sono due: $f$ strettamente crescente oppure strettamente decrescente.

Caso strettamente _crescente_: vale che$$
\begin{array}{}
F_{Y}(y)  & = &  \mathcal{P}\{Y \leq y  \} & = & \mathcal{P}\{X \leq f^{-1}(y)  \} \\
 &  &  & = & F_{X}(f^{-1}(y))
\end{array}
$$e [[Derivate|derivando]] si ottiene $$p_{Y}(y)=p_{X}(f^{-1}(y))\cdot \frac{df^{-1}(y)}{dy}$$Caso strettamente _decrescente_: vale che$$
\begin{array}{}
\mathcal{P}\{ f(X) \leq y \}&=& \\
\mathcal{P}\{ X \geq f^{-1}(y) \}&=&1-F_{X}
\end{array}
$$per cui, [[Derivate|derivando]], si ottiene lo stesso risultato di prima ma con il segno meno:$$p_{Y}(y)=-p_{X}(f^{-1}(y))\cdot \frac{df^{-1}(y)}{dy}$$e quindi, unificando i due casi, comparc
;e naturalmente il valore assoluto della derivata dell'inversa. Si ottiene cosi l'enunciato generale.
![[IMG - Trasformazioni di variabili con densita visualizazione.png]]


