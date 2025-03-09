---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---

# Support Vector Machine (SVM)
---
Le __Support Vector Machines__ (__SVM__) sono [[Modelli Parametrici|modelli parametrici di macchine learning]]  allenate con [[Algoritmi di learning supervisionato|strategie supervisionate]], è il primo modello che direttamente dalla [[Statistical Learning Theory (SLT)|statistical learnuing theory]] e fa structural risk minimization (SRM). 

le __Support Vector Machines__ (__SVM__) sono essenzialmente [[Modelli lineari con LMS|modello lineare]] ma si usa un problema di ottimizazione ad hoc per fare [[Statistical Learning Theory (SLT)|Structural Risk Minimization]]



Si assume che il data set sia $TR=\{\mathbf{x}_i,d_i\}$ con $d_i = \{-1,1\}$ e $\mathbf{w},\mathbf{x} \in \mathbb{R}^n$ e che i dati siano __[[linearmente separabili|linearmente separabili]]__, e si quindi vuole risolvere un [[Algoritmi di learning supervisionato|problema di classificazione]]. 
L'obiettivo __SVM__ è cerca un [[Piano cartesiano|iperpiano]] di dimensione $n+1$   della forma: $$g(\mathbf{x})=\mathbf{w}^T\mathbf{x}+b$$dove $\mathbf{w}$ e $b$ soni __parametri liberi__ tale che la __superfice di separazione__ definito da: $$g(\mathbf{x})=\mathbf{w}^T\mathbf{x}+b=0$$ ovvero un iperpiano dimensione $n$, massimizzi il __margine di separazione__ $\rho$. Ovvero massimizzi la distanza __minima__ tra $g(x)=0$ è i datapoint. 
I datapoint con distanza minimi sono detti __Support Vector__ $x^(s)$.
![[IMG - Support Vector Machine (SVM) Optimal Hyperplane 2D.png]]



nei  [[Modelli lineari con LMS|modello lineare]] non tutte le ipotesi $h$ sono uguali infatti con diversi ipotesi $h_1,\dots,h_n$ possiamo vedere che hanno tutti __margini__ diversi 
![[928BFB8C-963B-4554-B5B1-2F43868FCBDC.jpeg]]
Questo __margine__ può essere visto come una __safe-zone__, 
Aggiungendo un puto e assumendo che i dati vengono messi nel lato corretto della classificazione, se il punto è al di fuori del **margine** la soluzione rimane invariata.


L'ipotesi usata per la classificazione è la seguente: $$
h_\mathbf{w}(\mathbf{x})=
\begin{cases}
g(x) \geq 0 \quad \text{for } d_i = +1 \\  
g(x) < 0 \quad \text{for } d_i = -1
\end{cases} \ \ \ or \ \ h_\mathbf{w}(\mathbf{x}) = sign(g(\mathbf{x})) 
$$ è quindi una __Linear Threshold Unit__ (LTU) esattamente come i [[Modelli lineari con LMS|modelli lineari]]. 
>[!tip]- 
> [visualizzazione del iperpiano](https://www.desmos.com/3d/almdww7cpj?lang=it)



#### Distanza dalla superfice di separazione
Siano $\mathbf{w}_0$ e $b_o$ i parametri __ottimali__ per la __SVM__ questi definiscono l __iper piano ottimale__ e la __funzione discriminante__ $$g(\mathbf{x})=\mathbf{w}_{o}^T\mathbf{x}+b_{o}$$ogni input $\mathbf{x}$ puo essere riscritto come:
$$\mathbf{x}=\mathbf{x}_{p}+r\frac{\mathbf{w}_{o}}{||\mathbf{w}_{o}||}$$
- Dove $\mathbf{x}_{p}$ è la [[Applicazione lineare - Proiezione Ortogonale|proiezione ortogonale]] di $\mathbf{x}$ sull'__iperpiano ottimale__
- $r$ è la [[distanza euclidea|distanza euclidea]] di $\mathbf{x}_p$ dal dall'__iperpiano ottimale__, dove  il segno indica la direzione

Per definizione abbiamo che $\mathbf{x}_{p}$ appartiene all'__superfice di separazione__ quindi si ha 
che $g(\mathbf{x}_{p})=0$  possiamo usare questo per trovare la relazione :$$
\begin{array}{}
  g_o(\mathbf{x}) &=& \mathbf{w}_{o}^T\mathbf{x} + b_{o}    & =& 
  \mathbf{w}_{o}^T \left( \mathbf{x}_{p}+r\cfrac{\mathbf{w}_{o}}{\|\mathbf{w}_{o}\|_2} \right) + b_{o} \\  
&= &  \mathbf{w}_{o}^T\mathbf{x}_{p} + b_{o} +r\cfrac{\mathbf{w}^T\mathbf{w}_{o} }{ \|\mathbf{w}_{o}\|_2 }  & =& g_o(\mathbf{x}_{p}) + r \cfrac{\|\mathbf{w}_{o}\|_2^\cancel{ 2 }}{\cancel{ \|\mathbf{w}_{o}\|_2 }} \\  
&=&  r \|\mathbf{w}_{o}\|_2
\end{array}
$$o equivalentemente: $r=\cfrac{g(\mathbf{\mathbf{x}})}{\|\mathbf{w}_{o}\|_2}$ 

Mentre la distanza dell'origine dall'iperpiano è $\cfrac{b_{o}}{||\mathbf{w}_{o}||_2}$ e se vale che se 
- $b_{o}>0$ l'origine è nella parte positiva.
- $b_{o}<0$ l'origine è nella parte positiva.
- $b_{o} =0$ l'origine è appartenente alla __decision surface__.
![[IMG - SVM distanza di un punto dal iper piano ottimo.png]]


Considerando l ipotesi formulata come  $$\begin{cases}
\mathbf{w}_o^T\mathbf{x}_{i}+b_o \geq 0 \text{ if } d_{i}=+1 \\
\mathbf{w}_o^T\mathbf{x}_{i}+b_o \leq 0 \text{ if } d_{i}=-1
\end{cases}$$si possono scalare vettori $\mathbf{w}$ e $b$ in modo che valga$$\begin{cases}
\mathbf{w}_o^T\mathbf{x}_{i}+b_o \geq +1 \text{ if } d_{i}=+1 \\
\mathbf{w}_o^T\mathbf{x}_{i}+b_o \leq -1 \text{ if } d_{i}=-1
\end{cases}$$ e per la proprietà di __scaling freedom__ dei modelli lineari questo __rescaling__ non cambia la __superfice di separazione__ $g(\mathbf{x})=0$.
Una formulazione equivalente ma piu compatta è la seguente  $$d_{i}(\mathbf{w}_o^T\mathbf{x}_{i}+b_o)\geq 1$$. Con l'ipotesi cosi formulata si ha che per i punti più vicini alla __superfice di separazione__ detti __support vector__ $x^{(s)}$ con $d^{(s)}$ vale che $$d^{(s)}(\mathbf{w}_o^Tx^{(s)}+b_o)= 1$$
![[IMG - SVM supportVector.png]]

Applicando la distanza algebrica trovata precedentemente ai vettori di supporto otteniamo che $$r=\cfrac{g(\mathbf{x}^{(s)})}{\|\mathbf{w}_o\|_2}=d^{(s)}\cfrac{1}{\|\mathbf{w}_o\|_2}$$ dove $d^{(s)}$ è il segno e indica la classe positiva o negativa. Da questo si puo definire il la __Margin Width__ ottimo $\rho$ come $$\rho=2r=\cfrac{2}{\|\mathbf{w}_o\|_2}$$ dove il $2r$ viene dal fatto che la dimensione del margine è simmetrica rispetto alla __separation surface__. Siccome vogliamo massimizzare $\rho$ questa relazione ci dice che trovare $\rho$ ottimo significa minimizzare $\|\mathbf{w}_o\|_2$ quindi si fa qualcosa di simile alla [[Modelli lineari con LMS#Tikhonov regulation (ridge regression)|regolarizzazione con Tikonov]]


#### VC-Dimension
il __VC-dimension__ delta [[Statistical Learning Theory (SLT)|SLT]] è l inverso del margine ovvero decresce come l aumentare del margine con questo si può quindi controllare la complessità del modello


### Espressione formale del problema di apprendimento 
Per massimizzare il margine $\rho$ e quindi minimizzare $\|\mathbf{w}\|_2$ si puo formulare il problema come problema di [[Problemi di ottimizzazione convessi|ottimizzazione convessa]] $$\begin{cases}
\min \cfrac{\|\mathbf{w}\|^2_2}{2}  \\
d_p(\mathbf{w}^T\mathbf{x}_p+b) \geq 1 & \forall p=1,\dots,l 
\end{cases}$$
La funzione obiettivo $\Phi(\mathbf{w})$ è [[Funzioni Convesse-Concave|convessa]] in $\mathbf{w}$ e il __vincolo__ è lineare in $\mathcal{w}$, Quindi esiste sicuramente almeno __un minimo__ che è __globale__. 

Per risolvere questo problema si usa il [[Metodo di ottimizzazione vincolata con moltiplicatori di Lagrange|metodo dei moltiplicatori Lagrangiani]] e quindi si usa la __funzione lagrangiana__ come $$\mathbf{J}(\mathbf{w},b,\alpha)= \cfrac{\|\mathbf{w}\|^2_2}{2} - \sum^\ell_{i=1}\alpha_i (d_i(\mathbf{w}^T\mathbf{x}_i+b)-1)$$ dove $\alpha_i \ \ \ i=1,\dots,\ell$ sono detti __moltiplicatori Lagrange__ e sono variabile non negative. La soluzione del problema di ottimizzazione iniziale corrisponde ai __punti di sella__ della funzione $\mathbf{J}(\mathbf{w},b,\alpha)$.  
I __punti di sella__ per $\mathbf{J}(\mathbf{w},b,\alpha)$ sono i punti per cui vale che le soluzioni di $\mathbf{J}(\mathbf{w},b,\alpha)=0$ sono reali e di segno opposto.  
il __punti di sella__ ricercato è quello che __minimizza__ $\mathbf{w},b$ e __massimizza__ $\alpha$ 

Per cercare questo punto di sella si impongono die condizioni di ottimalità $$\begin{array}{}
\displaystyle \frac{\partial J(\mathbf{w}, b, \alpha)}{\partial \mathbf{w}} = 0  \\\
\displaystyle \frac{\partial J(\mathbf{w}, b, \alpha)}{\partial b} = 0 
\end{array}$$ e sviluppando le [[derivate|derivate]] otteniamo $$\begin{aligned} 
\frac{\partial J(\mathbf{w}, b, \alpha)}{\partial \mathbf{w}} &= \frac{\partial }{\partial \mathbf{w}} \left( \frac{\|\mathbf{w}\|^2_2}{2} - \sum^\ell_{i=1}\alpha_i (d_i(\mathbf{w}^T\mathbf{x}_i+b)-1) \right) \\ &= \frac{\partial }{\partial \mathbf{w}}  \frac{\|\mathbf{w}\|^2_2}{2} - \frac{\partial }{\partial \mathbf{w}}\sum^\ell_{i=1}( 
 \alpha_i  d_i\mathbf{w}^T\mathbf{x}_i+   \alpha_i d_ib- \alpha_i) \\ &= \mathbf{w} - \sum^\ell_{i=1} \alpha_i d_i \mathbf{x}_i =0
\end{aligned}$$ mentre rispetto $b$ abbiamo si ha che$$\begin{aligned}
\frac{\partial J(\mathbf{w}, b, \alpha)}{\partial b} &= \frac{\partial }{\partial b} \left( \frac{\|\mathbf{w}\|^2_2}{2} - \sum^\ell_{i=1}\alpha_i (d_i(\mathbf{w}^T\mathbf{x}_i+b)-1) \right) \\ &= \frac{\partial }{\partial b}  \frac{\|\mathbf{w}\|^2_2}{2}  - \frac{\partial }{\partial b}\sum^\ell_{i=1}( 
 \alpha_i  d_i\mathbf{w}^T\mathbf{x}_i+   \alpha_i d_ib- \alpha_i)  \\ &=  - \sum^\ell_{i=1} \alpha_i d_i
\end{aligned}
$$e sostituendole nelle __condizioni ti ottimalità__ otteniamo che devono essere vere le due relaziono $$
 \mathbf{w} = \sum^\ell_{i=1} \alpha_i d_i \mathbf{x}_i \ \ \ \ \ \ \  
\ \ \ \ \ \  \sum^\ell_{i=1} \alpha_i d_i = 0
$$

Per le  [[Karush–Kuhn–Tucker conditions (KKT)|KKT conditions]] si ha nei __punti di sella__ vale che $$\alpha_i(d_i(\mathbf{w}^T\mathbf{x}_i+b) -1) = 0$$ puo valere che $\alpha_i \neq 0$ e quindi vale che 
- Se $\alpha_i > 0$, allora $d_i (\mathbf{w}^T \mathbf{x}_i + b) = 1$ e $\mathbf{x}_i$ è un __vettore di supporto__.  
- Se  $\mathbf{x}_i$ non è un __vettore di supporto__, allora $\alpha_i = 0$.
e quindi per calcolare $\mathbf{w}$  e $b$ possiamo considerare solo l insieme $\ell_s$ dei __vettori di supporto__.




Siccome il problema di ottimizzazione che abbiamo ha una __obiettivo convessa__ e __vincoli lineari__ possiamo formulare il suo [[Problemi di ottimizazione - Dualità|problema duale]] che ha gli stessi __valori ottimi__ di $\mathbf{w}$ e $b$ ma esprime la sua funzione obiettivo in funzione dei moltiplicatori di Lagrange. Per fare ciò si espande la lagrangiana $$\mathbf{J}(\mathbf{w},b,\alpha)= \cfrac{\mathbf{w}^T\mathbf{w}}{2} - \sum^\ell_{i=1} 
 \alpha_i  d_i\mathbf{w}^T\mathbf{x}_i -  b\sum^\ell_{i=1}\alpha_i d_i + \sum^\ell_{i=1}\alpha_i$$ e applicando le condizione di ottimalità $\sum^\ell_{i=1}\alpha_i d_i=0$ si ottiene che il terzo termine si annullano, e applicando $\mathbf{w} = \sum^\ell_{i=1} \alpha_i d_i \mathbf{x}_i$ si puo espandere il secondo termine e il primo. Otteniamo $$\mathbf{w}^T\mathbf{w}= \sum^\ell_{i=1} 
 \alpha_i  d_i\mathbf{w}^T\mathbf{x}_i=
 \sum^\ell_{i=1} \sum^\ell_{j=1}  \alpha_i \alpha_j d_i d_j \mathbf{x}_i^T  \mathbf{x}_j$$ perciò si puo riformulare come $$
 \begin{array}{}
Q(\alpha) &  = & \displaystyle\cfrac{1}{2}\sum^\ell_{i=1} \sum^\ell_{j=1}  \alpha_i \alpha_j d_i d_j \mathbf{x}_i^T  \mathbf{x}_j - \sum^\ell_{i=1} \sum^\ell_{j=1}  \alpha_i \alpha_j d_i d_j \mathbf{x}_i^T  \mathbf{x}_j  + \sum_i^\ell \alpha_i& \\
 & = &\displaystyle    \sum_i^\ell \alpha_i- \frac{1}{2}\sum_{ij}^\ell\alpha_i\alpha_j d_id_j \mathbf{x}_i \mathbf{x}_j

\end{array}
 $$ dove $\alpha_i$ e $a_j$ sono tutte non negative.
 
 Allora si puo definire il [[Problemi di ottimizazione - Dualità|problema duale]] come $$
\begin{cases}
\displaystyle\max_\alpha \sum_i^l \alpha_i- \frac{1}{2}\sum_{ij}^l\alpha_i\alpha_jd_id_j (\mathbf{x}_i \mathbf{x}_j) \\
\displaystyle \sum_i^l\alpha_iy_i=0  \\
\alpha_i\geq 0
\end{cases}$$dove la funzione obiettivo è [[Funzioni Convesse-Concave|concava]] quindi sicuramente un __massimo__ ed è __sicuramente globale__.
Questo formulazione dipende solo dai dati di training e non dal vettore $\mathbf{w}$ in questo caso il costo computazionale scala con il numero di dati $\ell$ invece che con il numero di dimensioni $n$ del input.

risolvendo il __problema duale__ otteniamo i __Moltiplicatori Lagrangiani__ $\alpha_{o,i}$ e possono essere usati per calcolare $\mathbf{w}, b$ ovvero la __decision surface__, siccome $\alpha_{o,i}$ è non zero solo dove il vettore è di supporto abbiamo che $$\mathbf{w}  = \sum_i^{\ell_s}\alpha_{o,i} d_i\mathbf{x}_i $$ e $b$ per essere calcolato utilizza $\mathbf{w}$ quindi si ha$$\begin{array}{} 
b & = &1-\mathbf{w}^T\mathbf{x}^{(s)}  \\
 & = & \displaystyle 1 - \sum_i^{\ell_s}\alpha_{o,i} d_i\mathbf{x}_i^T\mathbf{x}^{(s)}   \end{array}$$
![[E2FD362E-4D60-4934-83E3-E2027FF8AFE6.jpeg]]


una risolto il problema duale per usare il modello no c è bisogno di calcolare esplicitamente il vettore $\mathbf{w}_o$ infatti$$\mathbf{w}_o\mathbf{x} + b_o=0 \iff\sum^\ell_{i=1} \alpha_{o,i} d_i \mathbf{x}^T_i \mathbf{x} +b_o=0$$ e quindi puo fare classificazione usando direttamente il dato di input prendendo il segno.



# Miglioramento della generalizzazione
---
Con le SVM si fissa l'errore di training per problemi linearmente separabili. Minimizzare la norma di $\mathbf{w}$ è equivalente a minimizzare la VC-dimension e quindi minimizzare il termine $\epsilon$ (VC-confidence) nella [[Statistical Learning Theory - Vapnik|STL]].

*Teorema di Vapnik:*
	Sia $D$ il diametro della palla più piccola che si trova attorno agli esempi di training $\{\mathbf{x}_{i}\}_{i=1}^N$.
	Per la classe di iperpiani di separazione descritta da dall'equazione $\mathbf{w}^T\mathbf{x}+b=0$, il limite superiore della VC-dimension è : $$VC \leq \min \left( \left \lceil   \frac{D^2}{\rho^2} \right \rceil , m_o \right) + 1$$

Dove $\left \lceil   \frac{D^2}{\rho^2} \right \rceil= \text{Radios}^2||\mathbf{w}||^2$

![[Pasted image 20250210173926.png]]
 Non ho capito




### Tolleranza agli errori 
fin ad ora si è parlato di _Hard Margin_ ovvero i punti sono sempre correttamente classificati. si può rilassare questa ipotesi e permettere un po’ di rumore  e fornire margini piu grandi detto _Soft margin_. si fa introducendo una _Slack-variables_ 
![[CFFAB0D2-2ABE-48F2-9926-3C46BD49A973.jpeg]]


Problema primale con tolleranza
$$\begin{cases}
\min \frac{\|\boldsymbol w\|^2}{2} + C\cdot \sum_p\xi_p \\
(\boldsymbol w^T\boldsymbol x_P+b)y_p \geq 1-\xi_p & \forall p=1,\dots,l 
\end{cases}$$
dove 
- $C$: è un iperparametro definito dal utente
	- _basso_ $C$: sono permessi molto errori sul $TS$, possibile _underfitting_
	- _alto_ $C$: sono permessi pochi errori sul $TS$,margine piccolo, possibile _overfitting_
ma si perde l approssimazione del SRM dei margini




## Kernel: passa ad un modello più flessibili 
si utilizzano i _kernel_ per fare la _liner basis expansion_  del modello in modo da poter classificare correttamente anche casi non [[Linearmente Separabili|linearmente separabili]] 

si mappano i data point da u no spazio dove i dati non sono linearmente separabili il un _feature space_ dove questi sono linearmente separabili 
![[C4A28AD4-0704-4A15-BC1A-8E441D8DEC98.jpeg]]
questo ci permette di gestire i casi non linearmente separabili ma con un modello che cresce molto si può facilmente finire in overfitting o in un modello _computazionalmente infattibilie_

abbiamo quindi che l ipotesi che come
$$h_w(\boldsymbol x) = sign\left(\sum_kw_k\phi_x(\boldsymbol x)\right)$$
per risolvere questo problema di regolarizzazione del modello si introducono i _Kernel_. con questo approccio la complessità resta bassa a prescindere della dimensione del _feature space_


![[17332ADF-4A0C-4EE5-ABF1-2B1C70530AA0.jpeg]]
$$h_w(\boldsymbol x) = sign \left(\sum_{p\in SV}\alpha_py_pK(\boldsymbol x_p,\boldsymbol x) \right) $$
ovvero si può implicitamente gestire il _feature space_ con una _kernel function_

##### Definizione Kernel function
un _Kernel function_ $K:\mathbb{R}^n\times\mathbb{R}^n \rightarrow \mathbb{R}$ è una funzione che dato un [[Hilbert Space|Hilbert space]] $X^m$ e una funzione $\phi:\mathbb{R}^n\rightarrow X^m$ esiste tale che 
$$K(\boldsymbol x_i,\boldsymbol x_j) = \phi(\boldsymbol x_i)^T\phi(\boldsymbol x_j)$$
si utilizza $K$ per calcolare il [[Prodotto Vettoriale (Cross product)|prodotto vettoriale]] direttamente in _feature space_ 


alcuni dei kernel piu usati sono:
1. _lineare_: $K(\boldsymbol x_i,\boldsymbol x_j)$
	- Mapping $\phi: x\rightarrow \phi$ dove $\phi(x)=x$
2. _Polinomiale_: di potenza $p:K(\boldsymbol x_i,\boldsymbol x_j)=(1+\boldsymbol x_i^T\boldsymbol x_j)^k$
	- Mapping $\phi: x\rightarrow \phi$ dove $\phi(x)$ ha dimensione esponenziale in $k$
3. _RBF_ (radial-basis function) guassiana: $K(\boldsymbol x_i,\boldsymbol x_j)=e^{-\cfrac{\|x_i-x_j\|^2}{2\sigma^2}}$
	- Mapping $\phi: x\rightarrow \phi$ dove $\phi(x)$ ha dimensione infinita
	- $\sigma$ è un iperparamentro 
		- _basso_ $\sigma$ : i punti sono classificati ugualmente solo se sono molto vicini tra di loro 

RBF è una scelta molto popolare può essere usata per fare decision boundry intorno a ogni punto del TR. infatti è molto potente per classificare correttamente su TR ma è molto prono a _overfitting_





