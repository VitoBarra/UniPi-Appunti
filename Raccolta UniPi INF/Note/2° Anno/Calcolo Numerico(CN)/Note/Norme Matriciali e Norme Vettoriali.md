---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Norme Matriciali e Norme Vettoriali
---
I principali problemi dell’algebra lineare numerica concernono la risoluzione di sistemi lineari ed il calcolo di [[Autovettori e Autovalori|autovalori e/o autovettori]] di matrici. Studiarne il _condizionamento_ significa misurare la sensibilità del problema considerato rispetto a perturbazioni dei dati forniti in ingresso. per fare cio bisogna disporre di strumenti per _valutare la distanza tra vettori e matrici_. gli autovettori e gli autovalori di un matrice potrebbero essere complessi quindi abbiamo bisogno di strumenti che lavorano su  $\mathbb{F}^n$e $\mathbb{F}^{n\times n}, n \geq 1$, con $\mathbb{F} \in \{\mathbb{R},\mathbb{C}\}$.

## Norma vettoriale
si dice norma vettoriale su $\mathbb{F}^n \in \{\mathbb{R}^n,\mathbb{C}^n\}$ una [[Funzioni|Funzione]] $f:\mathbb{F}^n \rightarrow \mathbb{R}$ che soddisfa le sequenze proprietà
1. (positivita) $\forall v \in. \mathbb{F}^n, \ f(v) \geq 0$ ed inoltre $f(v) =0 \iff v =0$
2. (linearita)$\forall v \in \mathbb{F}^n, \forall a \in \mathbb{F}, f(av) = |a|f(v)$
3. (diseguaglianza triangolare) $\forall v,z \in \mathbb{F}^n, f(v+z) \leq f(v) +f(z)$
se $f$ è una norma vettoriale su $\mathbb{F}^n$ indichiamo per comodità di notazione $f(v) = \|v\|$ 


### Distanza indotta
dalla norma vettoriale si puo costruire una distanza indotta $d:\mathbb{F}^n \times \mathbb{F}^n \rightarrow \mathbb{R}$
$$\forall v,z \in \mathbb{F}^n, \ d(v,z)= \|v-z \|$$
questa ha le _proprietà_ indotte dal fatto di usare una norma come definizione
1. (non negativita) $\forall v,z \in \mathbb{F}^n, d(v,r) \geq 0$ e $d(v,z)=0 \iff v=z$
2. (simmetria) $\forall v,z \in \mathbb{F}^n, d(v,z)=d(z ,v)$
3. ([[Diseguaglianza triangolare|diseguaglianza triangolare]]) $\forall v,z,e \in \mathbb{F}^n, d(v,z) \leq d(v,w)+d(w,z)$



## Esempi di norme
le seguenti funzioni $f(v),v=[v_1,\dots,v_n]^T \in \mathbb{F}^n$ sono norme su $\mathbb{F}^n$ dove $F^n \in \{\mathbb{R}^n,\mathbb{C}^n\}$
_norma euclidea_:
$$f(v)= \|v\|_2=\sqrt{\sum^n_{i=1} |v_i|^2}= \begin{cases}
	\sqrt{v^Tv}& if & \mathbb{F} = \mathbb{R} \\
	\sqrt{v^Hv}& if & \mathbb{F} = \mathbb{C}
\end{cases}$$
$H$ :trasposto coniugato ovvero se coefficienti complessi traspongo e faccio i coniugati dei numeri complessi 
_norma 1_:
$$f(v)= \|v\|_1= \sqrt{\sum_{i=1}^n}|v_i|$$
_norma infinito_:
$$f(v) = \|v\|_\infty = max_{1\leq i\leq n} |v_i|$$

### Teorema di equivalenza topologica delle norme
siano $\|\cdot\|$ e $\|\cdot\|’$ due norme su $\mathbb{F}^n$. Allora esistono costanti  $\alpha,\beta>0$ tali che 
$$\forall v \in \mathbb{F}^n\ \ \ \ \ \alpha\|v\|’ \leq \|v\| \leq \beta\|v\|’$$
qesto risultato implica che le proprietà topologiche di convergenza/divergenza di successioni e di continuità delle funzioni sono _invarianti_ risposto alla norma considerata


## Norme Matriciali 
si dice norma matriciale su $\mathbb{F}^{n\times n}$ una funzione $f:\mathbb{F}^{n \times n} \rightarrow \mathbb{R}$ che soddisfa le seguenti proprieta
1. $\forall A \in \mathbb{F}^{n\times n}, f(A)\geq, \ \  f(A)=0 \iff A =0$
2. $\forall A \in \mathbb{F}^{n\times n}, \forall \alpha \in \mathbb{F} , f(\alpha A)= |\alpha|f(A)$
3. $\forall A,B \in \mathbb{F}^{n \times n}, \ f(A+B) \leq f(A)+ f(B)$
4. $\forall A,B \in \mathbb{F}^{n \times n}, \ f(A\cdot B) \leq f(A)\cdot f(B)$
se $f$ è una norma vettoriale su $\mathbb{F}^{n\times n}$ indicata come $f(A) = \|A\|$


### Distanza matriciale indotta
dalla norma matriciale si puo indurre una distanza matriciale  $d:\mathbb{F}^{n\times n}\times \mathbb{F}^{n\times n} \rightarrow \mathbb{R}$ tra elementi di $\mathbb{F}^{n\times n}$ definita come
 $$\forall A,B \in \mathbb{F}^{n\times n} , d(A,B) = \|A-B\|$$
### norma matriciale indotta o compatibile con la norma vettoriale 
data una $\|\cdot\|$  una norma vettoriale su $\mathbb{F}^n$ si dice _norma matriciale indotta_ o compatibile con la _norma vettoriale_ la funzione $f:\mathbb{F}^{n\times n} \rightarrow \mathbb{R}$ definita da
$$\forall A \in \mathbb{F^{n \times n}}, \ \ f(A)=\smash{\displaystyle\max_{\{v \in \mathbb{F}^n:\|v\|=1\}}} \|Av\|$$


### Teorema compatibilità delle norme
Sia $\|\cdot\|_v$ una _norma vettoriale_ su $\mathbb{F}^n$ e sia $\|\cdot\|_m$ la _norma matriciale_ indotta vale
$$\forall A\in\mathbb{F}^n, \forall v \in \mathbb{F}, \ \ \|Av\|_v\leq\|A\|_m\|v\|_v$$
##### Dimostrazine
Se $v=0$ allora la relazione vale. assiemiamo pertanto che $v \not = 0$ si ha 
$$\left\|A\frac{v}{\|v\|} \right\| \leq \|A\|= \smash{\displaystyle\max_{\{z \in \mathbb{F}^n:\|z\|=1\}}}\|Az\|$$
e quindi la tesi segue la proprieta 2 delle norme vettoriali


### Teorema  norme matriciali indotte da norme vettoriali

Sia $A=(a_{i,j}) \in \mathbb{F^{n\times n}}$ si ha
$$
\begin{align}
\|A\|_\infty=max_{1\leq i\leq n} \sum^n_{j=1}|a_{i,j}| \\
\|A\|_1=max_{1\leq j\leq n} \sum^n_{i=1}|a_{i,j}|
\end{align}
$$
detto inoltre $p(B)$ il raggio spettrale di una matrice $B \in \mathbb{F}^{n\times n}$ definito come il modulo dell auto valore di modulo massimo di $B$
$$\forall B \in \mathbb{F}^{n\times n}, p(B)= max|\lambda_i|,\ \ \  \lambda_i, 1 \leq i \leq n, \text{autovalore di } B$$
_allora vale_
$$\|A\|_2=\sqrt{p(A^HA)}$$
Si osservi che mentre per la norma infinito e la norma 1 il calcolo si realizza facilmente con una sequenza finita di operazioni aritmetiche e confronti a partire dagli elementi della matrice, per la norma euclidea si richiede la risoluzione di un problema ausiliario (il calcolo del modulo dell’autovalore dominante di una matrice associata) di assai maggiore difficolta

noi siamo interessati a tutti e gli n autovalori potrebbero esisterne complessi 