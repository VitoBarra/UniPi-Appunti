---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
tags:
  - IA
Area: 
topic: 
SubTopic:
---

# Support Vector Machine (SVM)
---
la __Support Vector Macchine__ (SVM) è modello di [[Machine Learning|machne learning]]  che fonda la sua base teorica ne  [[Statistical Learning Theory (SLT)|SLT]] e ha i 2 seguenti obiettivi
1. Controllare la complessità del modello tramite un un approccio di ottimizzazione [[Formulazione problema di programmazione di lineare|problema di ottimizzazione]]
2. Espandere la flessibilità con una _Basis Expansion_ cosi come fatto nel [[Modelli lineari (LMS)|modello lineare]]


### Approccio di ottimizzazione 
in un caso di classificazione con il [[Modelli lineari (LMS)|modello lineare]] non tutte le ipotesi $h$ sono uguali
infatti con diversi ipotesi $h_1,\dots,h_n$ possiamo vedere che hanno tutti _margini_ diversi 
![[928BFB8C-963B-4554-B5B1-2F43868FCBDC.jpeg]]
dove _Margine_ è definito come:  2 volte (una per lato ) la distanza tra tra l iperpiano di separazione e il più vicino _data point_ . 
questo margine puo essere interpretato come una _safezone_ ovvero una zone in cui se non vengono messi nuovi dati al interno la soluzione non cambia, A meno che non venga inserito classificato nel lato sbagliato  

matematicamente i _margini_ si identificano con dei _vettori di supporto_
![[6B965600-4229-4611-86FB-D8C8EF726359.jpeg]]

definendo questi si può passare a interpretare il problema di _apprendimento_ come:
## Apprendimento
trova $(\boldsymbol w,b)$ tale che tutti i punti siano classificati correttamente e che il margine sia massimizzato

$(\boldsymbol x_p,y_p)$ è classificato correttamente $\iff \begin{cases}\boldsymbol w^T\boldsymbol x_p +b \geq 0& if & y_p =1 \\ \boldsymbol w^T\boldsymbol x_p +b < 0 & if & y_p=-1\end{cases} \forall p$ 

>[!note]
>si può riscalare tutto grazie alla preposizione di libertà di scaling per che il punti piu vicino al iperpiano soddisfi $|\boldsymbol w^T \boldsymbol x_p+ b|= 1$ ovvero il vettore di supporto. e quindi si puo riscrivere 
> $\iff \begin{cases}\boldsymbol w^T\boldsymbol x_p +b \geq 1& if & y_p =1 \\ \boldsymbol w^T\boldsymbol x_p +b \leq -1 & if & y_p=-1\end{cases} \forall p$ 

$\iff (\boldsymbol w^T \boldsymbol x_p+b)y_p\geq 1 \ \ \forall p$ ovvero _tutti_ i punti sono correttamente classificati. 
>[!note]
>a differenza del [[Modelli lineari (LMS)|modelli lineare]] in questo abbiamo un errore pari a 0 se le regioni sono [[Linearmente Separabili|linearmente separabili]]

#### Proprietà
_Margin_:  è definito da $\frac{2}{\|\boldsymbol w\|}$  quindi 
- massimizzare il margine $\iff$ minimizzare $\|\boldsymbol w\| \iff$ minimizzare $\frac{\|\boldsymbol w\|^2}{2}$  
	- Dove $\|\boldsymbol w\|^2 = (\boldsymbol w^T \boldsymbol w)$

il _VC-Dim_ delta [[Statistical Learning Theory (SLT)|SLT]] è l inverso del margine ovvero decresce come l aumentare del margine 
- con questo fatto si può quindi controllare la complessità del modello

e quindi si conclude che l _iperpiano ottimale_ è quello che massimizza il margine e soddisfa il problema (sui [[Validazione e test di una modello di ML|dati di training]])

### Espressione formale del problema di apprendimento 
problema [[Formulazione problema di programmazione di lineare|problema primare di ottimizzazione]] 
$$\begin{cases}
\min \frac{\|\boldsymbol w\|^2}{2} \\
(\boldsymbol w^T\boldsymbol x_P+b)y_p \geq 1 & \forall p=1,\dots,l 
\end{cases}$$
La funzione obiettivo è [[Funzioni Convesse-Concave|convessa]] in $\boldsymbol w$ e quindi ha un unico minimo.

si può vedere anche la sua formula [[Dualità|duale]]  
$$\begin{cases}
\max \alpha \sum_i^l \alpha_i- \frac{1}{2}\sum_{ij}^l\alpha_i\alpha_jy_iy_j (\boldsymbol x_i \boldsymbol x_j) \\
 \sum_i^l\alpha_iy_i=0 & \alpha_i\geq 0
\end{cases}$$
si cerca l $\alpha_p \ \ \ p=1,\dots,l$  ([[Multipli di Lagrange|multipli lagrange]])  
che è [[Funzioni Convesse-Concave|concava]] quindi ha unico massimo
in questo caso il costo computazionale scala con il numero di dati $l$ invece che con il numero di dimensione $n$  

computato il problema duale possiamo calcolare $\alpha$ e con questa possiamo computare $(\boldsymbol w ,b)$ il _decision boundry_
$$\begin{array}
\boldsymbol w = \sum_P\alpha_p y_p\boldsymbol x_p & p=1,\dots,l \\
b=y_k-\boldsymbol w^T \boldsymbol x_k  & \text{for any } \alpha_y
\end{array}$$
con Ipotesi 
$$h(\boldsymbol x) = sign(\boldsymbol  w^T \boldsymbol x +b) = sign \left (\sum^l_{p=1} \alpha_py_p \boldsymbol  x^T_p \boldsymbol x +b\right) = sign \left (\sum_{p\in SV} \alpha_py_p \boldsymbol  x^T_p \boldsymbol x +b\right)$$
1. $\alpha <> 0 \iff$ _support vector_ ($\alpha_p \not=0 \implies \boldsymbol x_p$ è un vettore di supporto)
	1. la soluzione è spesso spara e formulata sono i termini di vettori di supporto , l iperpiano dipende solo da essi 
2. la soluzione risultante è una forma speciale che non necessita di calcolare esplicitamente $(\boldsymbol w, b)$   per classificare i punti 
![[E2FD362E-4D60-4934-83E3-E2027FF8AFE6.jpeg]]


### tolleranza agli errori 
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


### modello conclusivo
- abbiamo un modello dove si deve scegliere un _parametro_ $C$ per  il trade off per l errore e un _kernel_ $K$
	- si risolve il problema di ottimizzazione cercando $\alpha$
		- questo scala computazionalmente con il numero di dati non il _feature space dimension_
		- molto modulare: basta cambiare  funzione _kernel_
$$h(x) = sign\left(\sum_{p \in SV}\alpha_py_pK(\boldsymbol x_p,\boldsymbol x)\right)$$
