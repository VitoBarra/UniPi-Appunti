---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# ODE - Sistemi
---
Un **sistema di [[Ordinary Differential Equation (ODE)|ODE]]** di ordine $n$ in $\mathbb{R}^m$ è un’[[Equazioni differenziali|equazione differenziale]] **vettoriale**. In forma **esplicita**
$$\mathbf{y}^{(n)}(x)=\mathbf{f}\big(x,\mathbf{y},\mathbf{y}',\dots,\mathbf{y}^{(n-1)}\big)$$
dove $\mathbf{y}(x)\in\mathbb{R}^m$ e $\mathbf{f}:\mathbb{R}\times(\mathbb{R}^m)^n\to\mathbb{R}^m$.  Si puo definire equivalermene la forma **implicita**$$\mathbf{F}\big(x,\mathbf{y},\mathbf{y}',\dots,\mathbf{y}^{(n)}\big)=\mathbf{0},$$con $\mathbf{F}:\mathbb{R}\times(\mathbb{R}^m)^{n+1}\to\mathbb{R}^m$, quando il sistema può essere risolto rispetto alla derivata di ordine massimo.  

Una **soluzione** è una funzione $\mathbf{y}:I\to\mathbb{R}^m$ di classe $C^n$ che **soddisfa il sistema** per ogni $x\in I$.

Un **sistema** si dice **decoupled** (disaccoppiato) se ogni equazione dipende solo dalla propria variabile e dalle sue derivate, cioè se$$y_i^{(n)}(x)=f_i\big(x,y_i,y_i',\dots,y_i^{(n-1)}\big),\qquad i=1,\dots,m.$$
In tal caso il sistema si riduce a $m$ equazioni scalari indipendenti, Mentre si dice **coupled** (accoppiato) quando almeno una componente $f_i$ dipende anche da altre componenti $y_j$ con $j\neq i$ o dalle loro derivate.

In termini geometrici, un sistema decoupled genera un flusso nello spazio delle fasi che si fattorizza come prodotto di flussi unidimensionali indipendenti; l’accoppiamento introduce interazioni tra le componenti e rende la dinamica multidimensionale.


Per lo studio **qualitativo e geometrico** dei sistemi dinamici è conveniente ricondurre qualunque sistema di ordine $n$ a una forma standard del **primo ordine**. Introducendo il vettore di stato
$$\mathbf{z}=(\mathbf{y},\mathbf{y}',\dots,\mathbf{y}^{(n-1)})\in\mathbb{R}^{mn}$$
il sistema diventa equivalente a
$$\mathbf{z}'(x)=\mathbf{f}(\mathbf{z}(x),x)$$
dove $\mathbf{f}:\mathbb{R}^{mn}\times\mathbb{R}\to\mathbb{R}^{mn}$ è un [[Spazi Vettoriali|campo vettoriale]]; nel caso autonomo $\mathbf{z}'=\mathbf{f}(\mathbf{z})$.

La riduzione al primo ordine non cambia il contenuto dell’equazione ma permette di descrivere l’evoluzione del sistema come un **flusso** nello spazio delle fasi $\mathbb{R}^{mn}$. Lo **spazio delle fasi** è lo spazio i cui punti rappresentano lo stato completo del sistema (valori delle variabili e delle loro derivate fino all’ordine $n-1$). Ogni soluzione è una traiettoria nello spazio delle fasi e il campo vettoriale assegna in ogni punto la direzione locale di evoluzione.

Ha quindi senso focalizzarsi sul caso del primo ordine in $\mathbb{R}^m$
$$\mathbf{y}'(x)=\mathbf{f}(\mathbf{y}(x),x)$$
dove $\mathbf{y}(x)\in\mathbb{R}^m$ è il vettore delle variabili di stato e $\mathbf{f}:\mathbb{R}^m\times\mathbb{R}\to\mathbb{R}^m$; nel caso autonomo $\mathbf{y}'=\mathbf{f}(\mathbf{y})$.

Comportamenti dinamici possibili dipendono dalla struttura del campo vettoriale e dalla posizione nello spazio delle fasi.
- **Convergenza a un equilibrio**: esistono stati $\mathbf{y}^*$ tali che le soluzioni con condizioni iniziali in un intorno tendono a $\mathbf{y}^*$ per $x\to+\infty$. Questo avviene tipicamente quando gli [[Autovettori e Autovalori|autovalori]] della [[Jacobiana di una funzione|Jacobiana]] hanno parte reale negativa.
- **Divergenza**: le soluzioni si allontanano dall’equilibrio o crescono senza limite. Può verificarsi quando la [[Jacobiana di una funzione|Jacobiana]] presenta autovalori con parte reale positiva.
- **Oscillazioni**: soluzioni periodiche o quasi-periodiche. In presenza di autovalori complessi della [[Jacobiana di una funzione|Jacobiana]] si osservano orbite chiuse o spirali.
- **Dinamiche non lineari complesse**: possono emergere attrattori, biforcazioni o comportamento caotico; la dinamica globale non è deducibile dalla sola linearizzazione locale.

Le traiettorie del sistema sono curve nello spazio delle fasi e la direzione del moto in ogni punto è data dal vettore $\mathbf{f}(\mathbf{y},x)$; l’evoluzione è interpretabile come un flusso che trasporta le condizioni iniziali.

La **linearizzazione locale** attorno a un equilibrio $\mathbf{y}^*$ consiste nell’approssimare il sistema non lineare con uno lineare nelle sue vicinanze. Scrivendo $\mathbf{y}=\mathbf{y}^*+\delta\mathbf{y}$ e sviluppando $\mathbf{f}$ al primo ordine si ottiene
$$\frac{d\,\delta\mathbf{y}}{dx}=J(\mathbf{y}^*)\,\delta\mathbf{y}$$
dove $J$ è la matrice [[Jacobiana di una funzione|Jacobiana]] del campo $\mathbf{f}$, $J_{ij}=\frac{\partial f_i}{\partial y_j}$. La stabilità locale dell’equilibrio è determinata dagli [[Autovettori e Autovalori|autovalori]] di $J(\mathbf{y}^*)$.

Un sistema è detto **stiff** quando gli autovalori della [[Jacobiana di una funzione|Jacobiana]] hanno parti reali con moduli molto diversi. Se $\lambda=a+ib$ è un autovalore, la parte reale è $\operatorname{Re}(\lambda)=a$ e determina la velocità di crescita o decadimento locale: a ciascun autovalore è associata una scala caratteristica
$$\tau\sim\frac{1}{|\operatorname{Re}(\lambda)|}.$$
Quando alcuni autovalori hanno $|\operatorname{Re}(\lambda)|$ molto grandi (tipicamente negativi) e altri molto piccoli, coesistono dinamiche che si smorzano rapidamente e dinamiche lente; le scale temporali risultano quindi fortemente separate.