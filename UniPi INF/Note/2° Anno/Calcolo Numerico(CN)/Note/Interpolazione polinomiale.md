---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Interpolazione polinomiale
---
per l'interpolazione polinomiale si intende l approssimazione in continuo di due dati discreti.
![[Pasted image 20230515170753.png]]
le spezzate che collegano i punti sono le approssimazioni che riusciamo ad ottenere con l _interpolazione Lineare_. 

#### Teorema di esistenza e unicità
_sia_ $\Pi_{n}$ lo [[Spazio Vettoriale|spazio vettoriale]] dei [[Polinomi|polinomi]] di grado massimo $n$ a _coefficienti Reali_ e $\Phi = \{\phi_{0}(x),\dots,\phi_{n}(x)\}$ una base di $\Pi_{n}$. 
- Assegnati $\mathcal{S} =(x_{i},y_{i}) \in \mathbb{R}^{2}, 0 \leq i \leq n$ si hanno $n+1$ punti con $x_{i} \not = x_{j}$.
	- praticamente è una funzione discontinua definita solo in alcuni punti.
_allora_ esiste ed è unico un polinomio $P(x) \in \Pi_{n}$ tale che
$$p(x_{k}) = \sum^n_{i=0}\alpha_{i}\phi_{i}(x_{k})=y_{k} \ \ \ \ \  0\leq k \leq n$$
tale polinomio è detto _polinomio di interpolazione_ sui punti $(x_{i},y_{i})\in \mathbb{R}^{2} \ \ 0 \leq i \leq n$
##### Dimostrazione
segue dalle condizioni del teorema la costruzione di un sistema lineare
$$\begin{bmatrix}
\phi_{0}(x_{0})  & \cdots & \cdots  & \phi_{n}(x_{0})  \\
\phi_{0}(x_{1})  & \cdots & \cdots  & \phi_{n}(x_{1})  \\
\vdots  & \vdots  & \vdots  & \vdots  \\
\phi_{0}(x_{n})  & \cdots & \cdots  & \phi_{n}(x_{n})
\end{bmatrix} 
\begin{bmatrix}
a_{0} \\
a_{1} \\
\vdots  \\
a_{n}
\end{bmatrix} =
\begin{bmatrix}
y_{0} \\
y_{1} \\
\vdots \\
y_{n}
\end{bmatrix}
$$
da qui per dimostrare esistenza e unicità ci basta dimostrare che la matrice dei coefficienti $\mathcal{V}(\mathcal{S},\Phi)$ sia [[Matrice inversa|invertibile]].
uno dei modi è provare che il [[Nucleo|nucleo]] di $\mathcal{V}(\mathcal{S},\Phi) = \{0\}$. e quindi
(sia) $\boldsymbol \beta = [\beta_{0},\dots,\beta_{n}]^{T}$ un _vettore del nucleo_. definizione di nucleo si ha che $$\mathcal{V}(\mathcal{S},\Phi)\boldsymbol \beta =0$$
da qui abbiamo che il [[Polinomi|polinomi]] $b(x)= \sum^{n}_{i=0}\beta_{i}\phi_{i}(x)$ si deve annullare in $n+1$ punti _distinti_.
ma siccome $\Phi$ è una base per $\Pi_{n}$ questo _è possibile_ $\iff \beta_{0} = \dots =\beta_{n} = 0$ 

### Basi utilizzabili per l interpolazione
la rappresentazione e il calcolo dei _coefficienti_ $\alpha_{i}$ dipendendo dalla [[Base di uno spazio vettoriale|base]] $\Phi$ scelta per $\Pi_{n}$
1. se $\phi_{j} = x^{j}, \ \ 0 \leq j\leq n$  si sta utilizzando la _base canonica_ dei polinomi e si ha $$\mathcal{V}(\mathcal{S},\Phi)=\begin{bmatrix}
1  & \cdots & \cdots  & x_{0}^n  \\
1  & \cdots & \cdots  & x_{1}^n  \\
\vdots  & \vdots  & \vdots  & \vdots  \\
1  & \cdots & \cdots  &  x_{n}^n
\end{bmatrix} 
$$ed è chiamatati _matrice di Vandermonde_ il calcolo dei coefficienti con questa matrice è generalmente [[Tipi di Errore nel calcolo numerico#Errore Inerente|mal condizionata]] e la risoluzione del sistema lineare richiede $O(n^{3})$ operazioni aritmetiche
2. se $\phi_{0} = 1,\phi_{j} = \prod^{j-1}_{i=0}(x-x_{i}), \ \ 0 \leq j\leq n$  si ha che la matrice $\mathcal{V}(\mathcal{S},\Phi)$ è [[Tipi di matrice quadrata|triangolare inferiore]] $$(\mathcal{V}(\mathcal{S},\Phi))_{h+1,k+1}=
\begin{cases} 
\prod_{i=0}^{k-1}(x_{h}-x_{i})  &  \text{if }\ h\geq k\\
0&  \text{if }\ h< k
\end{cases} 
$$i _polinomio di interpolazione_ $p(x)$ risultate con questa matrice è detto in _forma di Newton_ e il calcolo dei coefficienti è generalmente [[Tipi di Errore nel calcolo numerico#Errore Inerente|mal condizionata]] e la risoluzione del [[Sistemi lineari e lineari omogenei|sistema lineare]] richiede $O(n^{2})$ operazioni aritmetiche
3. se $\phi_{j} = L_{j} = \prod^n_{i=0,i\not=j} \cfrac{x-x_{i}}{x_{j}-x_{i}},\ \ \  0 \leq k\leq n$ allora si ha che $\mathcal{V}(\mathcal{S},\Phi) = I_{n}$ $$(\mathcal{V}(\mathcal{S},\Phi))_{h+1,k+1}= L_{k}(x_{h})=
\begin{cases} 
1  &  \text{if }  h= k\\
0 & \text{altrimenti}  
\end{cases} 
$$i _polinomio di interpolazione_ $p(x)=\sum^{n}_{j=0}f(x_{j})L_{j}(x)$ risultate con questa matrice è detto in _forma di Lagrange_. e il calcolo dei coefficienti $a_{j}=y_{j}$ è [[Tipi di Errore nel calcolo numerico#Errore Inerente|ottimamente condizionato]] e _non_ richiede operazioni aritmetiche


in contesti applicativi solitamente non si é interessati alla valutazione dei coefficenti ma a quella del polinomio in punti diversi da i punti già disponibili (_detti anche nodi_)  indicati con $\hat{x}$. nella _forma di langrange_ si ha che 
$$P(\hat{x}) = \sum^{n}_{j=0}f(x_{j})L_{j}(\hat{x}) =\sum^{n}_{j=0}\left(f(x_{j})\prod^n_{i=0,i\not=j} \cfrac{\hat{x}-x_{i}}{x_{j}-x_{i}}\right) = \prod_{i=0}^{n}(\hat{x}-x_{i})\sum^{n}_{j=0} \frac{y_{j}}{\omega_j(\hat{x}-x_{j})}$$
con $\omega_{j}=\prod^{n}_{i=0\ i\not=j}(x_{j}-x_{i}), 0\leq j\leq n$ se i pesi $\omega_{j}$ sono _precomputati_ computare $P(\hat{x})$ costa $O(n)$ operazioni aritmetiche




### Resto del interpolazione Polinomiale
le tecniche di interpolazione consentono di approssimare $f$ a partire dai punti conosciuti. siccome è un approssimazione abbiamo bisogno di un modo per misurare l errore. 
si utilizza a questo scopo il _resto del interpolazione Polinomiale_ definito come
$$r(\hat{x})= f(\hat{x}) -p(\hat{x})$$
#### Teorema del resto del interpolazione polinomiale
_sia_ $f:[a,b]\rightarrow \mathbb{R}$ e siano  $a\leq x_{0}< x_{1} <\dots <x_{n} \leq b$ , $n+1$  _nodi distinti_  e $p(x)$ il [[Polinomi|polinomio]] di interpolazione sui punti $\mathcal{S}= \{(x_{i},f(x_{i})) \in \mathbb{R}^{2}, 0 \leq i\leq n\}$
_se_ $f \in C^{n+1}([a,b])$ 
_allora_ vale che il resto 
$$\forall \hat{x}\in [a,b]\ \  \exists\hat{\xi}\in [a,b] . r(x)= \frac{f^{(n+1)}(\hat{\xi})}{(n+1)!}\prod^{n}_{i=0}(\hat{x}-x_{i})$$
##### Dimostrazione
- per il caso $\hat{x}=x_{i}$ si ha che $r(\hat{x})=f(x_{i})-p(x_{i})=0$ per le _condizioni di interpolazione_ e in oltre $\prod^{n}_{i=0}(\hat{x}-x_{i}) =\prod^{n}_{i=0}(x_{i}-x_{i}) = 0$ quindi la relazione è verificata per $\forall\hat{\xi}\in[a,b]$
- per il caso $\hat{x}\not =x_{i}$ si consideri la seguente funzione ausiliaria$$h(x) = f(x)-p(x)-\frac{f(\hat{x})-p(\hat{x})}{\prod^{n}_{j=0}(\hat{x}-x_{j})}\prod^{n}_{i=0}(x-x_{i})$$questa vale $h(x_{i})=0,\ 0 \leq i \leq n$ e $h(\hat{x})=0$. pertanto la funzione si annulla in almeno $n+2$ _punti distinti_ (gli $n+1$ punti di $\mathcal{S}$ + $\hat{x}$). dal [[Teorema di Rolle|teorema di rolle]] segue che $h'(x)$ si annulla in $n$ punti distinti in $[a,b]$ e _interando_ il ragionamento abbiamo che $h^{(n+1)}(x)$ si annulla in almeno $1$ punto detto $\hat{\xi}$ pertanto$$0 =h^{(n+1)}(\hat{\xi}) =f^{(n+1)}(\hat{\xi})-\cfrac{f(\hat{x})-p(\hat{x})}{\prod^{n}_{i=0}(\hat{x}-x_{i})}(n+1)! $$questo siccome $p(x)$ _è un polinomio di grado_ $\leq n$ la seconda parte un polinomio di grado $n+1$. 
	da qui si può procedere per raggiungere la tesi.$$\begin{array}{}
f^{(n+1)}(\hat{\xi})-\cfrac{f(\hat{x})-p(\hat{x})}{\prod^{n}_{i=0}(\hat{x}-x_{i})}(n+1)!  & = & 0 \\
  \cfrac{f(\hat{x})-p(\hat{x})}{\prod^{n}_{i=0}(\hat{x}-x_{i})}(n+1)!& =& f^{(n+1)}(\hat{\xi}) \\
 f(\hat{x})-p(\hat{x})(n+1)!& =& (f^{(n+1)}(\hat{\xi}))\prod^{n}_{i=0}(\hat{x}-x_{i})&  \\
f(\hat{x})-p(\hat{x})  & = & \cfrac{f^{(n+1)}(\hat{\xi})}{(n+1)!}\prod^{n}_{i=0}(\hat{x}-x_{i})
\end{array}$$
#### Studio del resto
si può studiare il resto per capire come si comporta
posto 
$$M_{n+1} = \max_{{x\in[a,b]}}(|f^{(n+1)}(x)|)$$
si ha 
$$r_{max}= \max_{x\in [a,b]}|r(x)| \leq \max_{x \in [a,b]}\left|\prod^{n}_{i=0}(x-x_{i})\right| \cfrac{M_{n+1}}{(n+1)!} $$
consideriamo il caso di nodi $x_{i}$ equidistanti con passo $h$, cioè $x_{i} = x_0+ih$ per $i =0,\dots,n$. Ponendo $x=x_{0}+th$ si ha
$$r_{max} \leq \max_{t\in[0,n]}|\pi_{n}(t)|h^{n+1}\cfrac{M_{n+1}}{(n+1)!}, \ \text{dove} \ \pi_{n}(t)=\prod_{i=0}^{n}(t-i)$$
se $f^{(n+1)}(x)$ non _varia molto_ si può studiare da solo il comportamento di $\pi_{n}(t)$ i cui zeri sono $1,\dots,n$. si nota che
- $\cfrac{n}{2}$ è il punto di simmetria per $|\pi_{n}(t)|$
- i massimi di $|\pi_{n}(t)|$ _crescono_ in ogni intervallo $(i,i+1)$ quando ci si allontana dal centro del intervallo.
- il massimo a gli estremi cresce in maniera esponenziale al crescere di $n$
da questo studio possiamo dire che conviene usare il _polinomio di interpolazione_ per approssimare $f(x)$ solo per _bassi_ $n$  e per $x$ vicini al _centro del intervallo_
![[Pasted image 20230516004029.png]]
![[Pasted image 20230516004036.png]]


> [!example]- Esempi la funzione di Runge
$$f(x)=\frac{1}{1+x^{2}}, \ \ x \in[a,b]=[-5,5]$$
sia $p(x)$ il polinomio di interpolazione sui nodi $x_{i}=a+\frac{i(b-a)}{n} , \ \ \ i=0,\dots,n$ 
si ottiene disegnando la funzione e i valori approssimati 
per $n=5$
![[Pasted image 20230516004320.png]]
per $n =10$
![[Pasted image 20230516004432.png]]

