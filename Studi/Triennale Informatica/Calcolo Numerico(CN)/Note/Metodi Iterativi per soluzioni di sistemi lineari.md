---
Course: Calcolo Numerico
topic: nota
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Metodi Iterativi per soluzioni di sistemi lineari
---
sono metodi per ricavare una [[Soluzioni di un sistema lineare|soluzione]] del [[Sistemi lineari e lineari omogenei|sistema lineare]] associato alla _matrice_ quando il [[Mosse di Gauss|metodo di Gauss]] non funziona bene per via della struttura della matrice che fa incorrere in un fenomeno di _Fill-in_

un esempio dove questo può succedere è la seguente matrice
$$
\begin{bmatrix}
? & ? & ? & ?\\
? & ? & 0 & 0 \\
? & 0 & ? & 0 \\
? & 0 & 0 & ?
\end{bmatrix}
$$
dove per _fill-in_ si intende la trasformazione degli elementi 0 in elementi diversi da zero dove qualche passo di gauss.
$$
\begin{bmatrix}
? & ? & ? & ? \\
0 & ? & ? & ? \\
0 & ? & ? & ? \\
0 & ? & ? & ?
\end{bmatrix}
$$
con ? numeri qualsiasi anche diversi

## Metodi interativi
sono _metodi iterativi_ per cercare [[Soluzioni di un sistema lineare|soluzioni di sistemi lineari]].
si cerca una sequenza di vettori $\boldsymbol{x}$ tale che $x^{(0)}$ ossia il vettore di partenza e 
- $\{x^{(k)}\}$ la sequenza di vettori 
-  per $\{x^{(k)}\}_{k\to \infty} \rightarrow x$ _soluzione_ di $Ax=b$
- $\lim_{k \to \infty}x^{(k)} = x \iff \lim_{k \to \infty}\|x^{(k)}-x\| = 0$ 
	- per via della [[Norme Matriciali e Norme Vettoriali#Teorema di equivalenza topologica delle norme|Teorema di equivalenza topologica delle norme ]] posso scegliere una _qualsiasi norma_.
- Criterio di arresto
	- _interazioni successive_: $$\|x^{(k+1)}-x^{k}\| < tol$$
	- _scarto_:$$\|Ax^{(k)}-b\| < tol$$

### Metodi basati su decomposizione di matrice
con questi classe di metodi posso scomporre la matrice del mio [[Sistemi lineari e lineari omogenei|sistema lineare]] $Ax=b$ come $A = M-N$ con $M,N$ due matrici. sotto l assunzione che $M$ sia [[Matrice inversa|invertibile]] e quindi $det(0)\not=0$ possiamo fare la seguente sequenza di passaggi logici
$$\begin{array}{}
(M-N)x =b &\iff \\
Mx-Nx=b &  \iff \\ 
Mx = Nx+b & \iff \\
x = M^{-1}Nx+M^{-1}b
\end{array}$$
nominiamo 
- _Matrice di iterazione_: $P = M^{-1}N$ con $P \in \mathbb{K}^{n\times n}$
- un vettore $q = M^{-1}b$ con $q\in \mathbb{K}$ 
e abbiamo la formula 
$$x =Px+q$$
da qui possiamo costruire un _metodo iterativo_ partendo da una relazione [[Induttività|Induttività]]
$$
\begin{cases}
x^{(0)} \in \mathbb{K}^n&\\
x^{(k+1)} = P x^{(k)}+q & k \geq 0
\end{cases}
$$
con $x^{(0)}$ scelto a piacere
si dice _metodo_ la successione di vettori ottenuto da questa relazione (le successioni cambiano se cambia il vettore iniziale $x^{(k)}$)

un metodo si dice _convergente_ se tutte le [[Successioni|successioni]]  che ottengo variando il vettore iniziale sono _convergenti_ ovvero a $x = A^{-1}b$  


#### Teorema della cosa giusta
_siano_ $Ax=b$ un [[Sistemi lineari e lineari omogenei|sistema lineare]] ,$\{x^{(k)}\}$ una successione di vettori e la _relazione sopra costruita_ $x^{(k+1)}=Px^{(k)}+q$ 
_se_ $\{x^{(k)}\}$ è _convergente_ 
_allora_ $$\lim_{k\to \infty} x^{(k)} =x$$ovvero se converge lo fa esattamente a $x$ la soluzione del sistema lineare 

##### Dimostrazione
impostando $g(x) = Px+q$ è $g: \mathbb{K}^n \rightarrow \mathbb{K}^n$ con $g$ [[Continuità di una funzione|continua]] 
1. per dimostrare la continuità di $g$ si utilizza la definizione e dobbiamo quindi mostrare che $\forall \varepsilon>0,\  \exists \delta>0: \  \forall x^{(k)},x: \| x^{(k)}-x\| < \delta \implies \|g(x^{(k)})-g(x)\| \leq \varepsilon$
$$
\begin{array}{}
\|g(x^{(k)})-g(x)\| &=\\
\|Px^{(k)}+q - (Px+q)\| & = \\
\|P(x^{(k)}-x)\| &\leq \\
\|P\|\|x^{(k)}-x\| & \leq \\
\|P\| \cdot\delta & =\\
\varepsilon 

\end{array}
$$
con $\delta = \cfrac{\epsilon}{\|P\|}$
1. ora possiamo dire che
	- $$
	\begin{array}{}
	x= \lim_{k\to \infty} x^{(k+1)} & =  & \text{dal ipotesi di convergenza}\\
	\lim_{k\to \infty}g(x^{(k)}) &=  &\text{dalla dalla definizione del metodo}\\
	g(\lim_{k \to \infty}x^{(k)}) & = & \text {dalla continuita di }g \\
	g(x) &= & \text{dal ipotesi di convergenza}\\
	Px+q & & \text{dalla definizione di } g
	\end{array} $$
>[!note]
>se $x^{(k)}$ converge $x$ è un [[Punti Fissi|punto fisso]] di $g$
 
questo ci dimostra che il _metodo iterativo_ porta effettivamente alla soluzione del sistema lineare


### Criterio di convergenza
#### 1. _Teorema_ Condizione Sufficiente:
l'metodo è _convergente_ se esiste una [[Norme Matriciali e Norme Vettoriali#norma matriciale indotta o compatibile con la norma vettoriale|norma matriciale indotta]] tale che $\|P\|<1$
##### Dimostrazione
preso $e^{(k)} = x^{(k)}-x$  il vettore d errore basta dimostrare che se $\exists \|P\| <1 \implies \lim_{k \to \infty} \|e_k\| =0$ e allora posso dire
$$
\begin{array}{}
e^{(k+1)} &= & \text{}\\ 
x^{(k+1)}-x &= & \text{per definizine di errore}\\
Px^{(k)}+q-(Px+q)& =& \text{per definizione di metodo}\\ 
P(x^{(k)}-x) &= & \\
Pe^{(k)} &= & \\
P(Pe^{(k-1)}) &=&P^{(k+1)}e^{(0)}
\end{array}
$$
sia la $\|\cdot\|$ la norma _vettoriale_ tale che $\|P\|<1$ allora
$$
\begin{array}{}
\| e^{(k+1)}\| = \|P^{k+1}e^{(0)}\| & \leq & \|P^{k+1}\|\cdot\|e^{(0)}\|  &\leq \\ 
\|P\| \cdot \|P^k\| \cdot \|e^{(0)}\| &\leq& \|P\|^{k+1}\cdot \|e^{(0)}\|
\end{array}$$
e allora possiamo scrivere 
$$0 \leq \|e^{(k+1)}\| \leq \|P\|^{k+1}\cdot\|e^{(0)}\|$$
- $0 \leq$ per le proprietà delle [[Norme Matriciali e Norme Vettoriali|norme]]
utilizzando il [[Teorema del confronto dei carabinieri|teorema dei carabinieri]]  siccome $\|P\|^{k+1}$ tende a $0$ possiamo dire che $\|e^{(k+1)}\|$ tende a $0$

#### 2. Teorema condizione necessaria (e sufficiente):
se il metodo è _convergente_ $\iff$ il [[Raggio spettrale|raggio spetrale]] della matrice di convergenza   $p(P)<1$. da questo si hanno i seguenti fatti
- Guardando il [[Determinante di una matrice|determinante]] $|det(P)| \geq 1$ allora esiste un [[Autovettori e Autovalori|autovalore]] di $P$ $|\lambda_i|  \geq 1 \implies$ _non converge_
	- il determinante è $\prod^n_{i=0}\lambda_i$
- Guardando la [[Traccia di una matrice|traccia]] $|tr(P)| \geq n$ allora esiste un [[Autovettori e Autovalori|autovalore]] di $P$     $|\lambda_i| \geq 1 \implies$ _non converge_
	- la traccia è $\sum^n_{i=0}\lambda_i$ 

##### Dimostrazione di necessita
si vuole dimostrare che un metodo _convergete_$\implies p(P)<1$

preso un _autovalore_ $\lambda = p(P)$  è sia $v$ il corrispondente _autovettore_.
per definizione di _autovalore_ osserviamo che vale
- $Pv = \lambda v$
- $v \not =0$
 
il metodo per _ipotesi_ converge e quindi lo fa per qualsiasi $x^{(0)} \in \mathbb{R}^n$ e quindi in particolare _converge_ con  $x^{(0)} = x+v$ dove 
- $x=A^{-1}b$  é la soluzione del _sistema lineare_
- $v$ é il vettore associato al _autovalore_
 
 per _ipotesi_ di convergenza $$e^{(k+1)}= P^{k+1} e^{(0)}=0 $$e usando la definizione di errore posso scrivere $e^{(0)} = x^{(0)}-x = x-x+v = v$ e quindi $$e^{(0)}=v$$Sostituendo ottengo $$e^{(k+1)}=P^{k+1}e^{(0)}= P^{k+1}v = \lambda^{k+1}v$$
per _ipotesi_ di convergenza abbiamo anche che 
$$\lim_{k\to\infty}\|e^{(k+1)}\|=0$$
allora mostriamo che deve essere vero
$$0 =\lim_{k\to\infty}\|e^{(k+1)}\| =\lim_{k\to\infty}\|\lambda^{k+1}v\| =\|v\|\lim_{k\to\infty}|\lambda|^{k+1}= 0 $$
il che si verifica $\iff \lambda < 1$

##### Lemma
sia $A \in \mathbb{R}^{n \times n}$ e il [[Raggio spettrale|raggio spetrale]] $P(A)<1 \implies \exists$ una [[Norme Matriciali e Norme Vettoriali|norma matriciale indotta]] tale che $\|A\|<1$  

##### Dimostrazione di sufficienza
si vuole dimostra che $p(P)<1 \implies$ metodo _convergente_. 
utilizzando il lemma so che esiste una _norma matriciale indotta_ tale che $\|P\|<1$ quindi sono verificate le ipotesi per la [[#^c2cecb|condizione di sufficienza]]