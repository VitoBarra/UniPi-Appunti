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
Le __Support Vector Machines__ (__SVM__) sono [[Modelli Parametrici|modelli parametrici di macchine learning]]  allenate con [[Algoritmi di learning supervisionato|strategie supervisionate]], è il primo modello che direttamente dalla [[Statistical Learning Theory (SLT)|statistical learnuing theory]] e fa [[Statistical Learning Theory (SLT)|structural risk minimization (SRM)]]. 

le __Support Vector Machines__ (__SVM__) sono essenzialmente [[Modelli lineari con LMS|modello lineare]] ma si usa un problema di ottimizzazione ad hoc per fare [[Statistical Learning Theory (SLT)|Structural Risk Minimization]]



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

Considerando l'ipotesi formulata come  $$\begin{cases}
\mathbf{w}_o^T\mathbf{x}_{i}+b_o \geq 0 \text{ if } d_{i}=+1 \\
\mathbf{w}_o^T\mathbf{x}_{i}+b_o \leq 0 \text{ if } d_{i}=-1
\end{cases}$$si possono scalare vettori $\mathbf{w}$ e $b$ in modo che valga$$\begin{cases}
\mathbf{w}_o^T\mathbf{x}_{i}+b_o \geq +1 \text{ if } d_{i}=+1 \\
\mathbf{w}_o^T\mathbf{x}_{i}+b_o \leq -1 \text{ if } d_{i}=-1
\end{cases}$$ e per la proprietà di __scaling freedom__ dei modelli lineari questo __rescaling__ non cambia la __superfice di separazione__ $g(\mathbf{x})=0$.
Una formulazione equivalente ma piu compatta è la seguente  $$d_{i}(\mathbf{w}_o^T\mathbf{x}_{i}+b_o)\geq 1$$. Con l'ipotesi cosi formulata si ha che per i punti più vicini alla __superfice di separazione__ detti __support vector__ $x^{(s)}$ con $d^{(s)}$ vale che $$d^{(s)}(\mathbf{w}_o^Tx^{(s)}+b_o)= 1$$
![[IMG - SVM supportVector.png]]
Applicando la distanza algebrica trovata precedentemente ai vettori di supporto otteniamo che $$r=\cfrac{g(\mathbf{x}^{(s)})}{\|\mathbf{w}_o\|_2}=d^{(s)}\cfrac{1}{\|\mathbf{w}_o\|_2}$$ dove $d^{(s)}$ è il segno e indica la classe positiva o negativa. Da questo si puo definire il la __Margin Width__ ottimo $\rho$ come $$\rho=2r=\cfrac{2}{\|\mathbf{w}_o\|_2}$$ dove il $2r$ viene dal fatto che la dimensione del margine è simmetrica rispetto alla __separation surface__. Siccome vogliamo massimizzare $\rho$ questa relazione ci dice che trovare $\rho$ ottimo significa minimizzare $\|\mathbf{w}_o\|_2$ quindi si fa qualcosa di simile alla [[Modelli lineari con LMS#Tikhonov regulation (ridge regression)|regolarizzazione con Tikonov]]




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
 \alpha_i  d_i\mathbf{w}^T\mathbf{x}_i -  b\sum^\ell_{i=1}\alpha_i d_i + \sum^\ell_{i=1}\alpha_i$$ e applicando le condizione di ottimalità $\sum^\ell_{i=1}\alpha_i d_i=0$ si annulla il terzo termine, e applicando $\mathbf{w} = \sum^\ell_{i=1} \alpha_i d_i \mathbf{x}_i$ si puo espandere il primo e il secondo. Espandiamo il mprimo termine come: $$\mathbf{w}^T\mathbf{w}= \sum^\ell_{i=1} 
 \alpha_i  d_i\mathbf{w}^T\mathbf{x}_i=
 \sum^\ell_{i=1} \sum^\ell_{j=1}  \alpha_i \alpha_j d_i d_j \mathbf{x}_i^T  \mathbf{x}_j$$ e perciò si puo riformulare come $$
 \begin{array}{}
Q(\alpha) &  = & \displaystyle\cfrac{1}{2}\sum^\ell_{i=1} \sum^\ell_{j=1}  \alpha_i \alpha_j d_i d_j \mathbf{x}_i^T  \mathbf{x}_j - \sum^\ell_{i=1} \sum^\ell_{j=1}  \alpha_i \alpha_j d_i d_j \mathbf{x}_i^T  \mathbf{x}_j  + \sum_i^\ell \alpha_i& \\
 & = &\displaystyle    \sum_i^\ell \alpha_i- \frac{1}{2}\sum_{ij}^\ell\alpha_i\alpha_j d_id_j \mathbf{x}_i \mathbf{x}_j

\end{array}
 $$ dove $\alpha_i$ e $a_j$ sono tutte non negative.
 
 Allora si puo definire il [[Problemi di ottimizazione - Dualità|problema duale]] come $$
\begin{cases}
\displaystyle\max_\alpha \sum_i^\ell \alpha_i- \frac{1}{2}\sum_{ij}^\ell\alpha_i\alpha_jd_id_j (\mathbf{x}_i \mathbf{x}_j) \\
\displaystyle \sum_i^\ell\alpha_iy_i=0  \\
\alpha_i\geq 0
\end{cases}$$dove la funzione obiettivo è [[Funzioni Convesse-Concave|concava]] quindi sicuramente un __massimo__ ed è __sicuramente globale__.
Questo formulazione dipende solo dai dati di training e non dal vettore $\mathbf{w}$ in questo caso il costo computazionale scala con il numero di dati $\ell$ invece che con il numero di dimensioni $n$ del input.

risolvendo il __problema duale__ otteniamo i __Moltiplicatori Lagrangiani__ $\alpha_{o,i}$ e possono essere usati per calcolare $\mathbf{w}, b$ ovvero la __decision surface__, siccome $\alpha_{o,i}$ è non zero solo dove il vettore è di supporto abbiamo che $$\mathbf{w}  = \sum_i^{\ell_s}\alpha_{o,i} d_i\mathbf{x}_i $$ e $b$ per essere calcolato utilizza $\mathbf{w}$ quindi si ha$$\begin{array}{} 
b & = &1-\mathbf{w}^T\mathbf{x}^{(s)}  \\
 & = & \displaystyle 1 - \sum_i^{\ell_s}\alpha_{o,i} d_i\mathbf{x}_i^T\mathbf{x}^{(s)}   \end{array}$$
![[E2FD362E-4D60-4934-83E3-E2027FF8AFE6.jpeg]]

una risolto il problema duale per usare il modello no c è bisogno di calcolare esplicitamente il vettore $\mathbf{w}_o$ infatti$$\mathbf{w}_o\mathbf{x} + b_o=0 \iff\sum^\ell_{i=1} \alpha_{o,i} d_i \mathbf{x}^T_i \mathbf{x} +b_o=0$$ e quindi puo fare classificazione usando direttamente il dato di input prendendo il segno.



# VC-dimension dell SVM
---
 Fissando l'errore di training, nella __SVM__ Minimizzare la $\|\mathbf{w}\|$ è equivalente a minimizzare la [[Statistical Learning Theory (SLT)|VC-dimension]] e quindi a minimizzare __VC-confidence__ $\epsilon$ in $$R \leq R_{emp}+\epsilon\left (\frac{1}{l},VC,\frac{1}{\delta}\right)$$ e quindi si fa [[Statistical Learning Theory (SLT)|Structura risk minimization]] automatica.
 
Si puo dare un upper bond preciso alle __SVM__ grazie al **Teorema di Vapnik** 

**Teorema di Vapnik**:
Sia
-  $D$ il diametro della palla più piccola che si trova attorno agli esempi di training $\{\mathbf{x}_{i}\}_{i=1}^\ell$.
- l equazione del superfice di separazione $\mathbf{w}^T\mathbf{x}+b=0$
**Allora** il limite superiore della __VC-dimension__ è : $$VC \leq \min \left( \left \lceil   \frac{D^2}{\rho^2} \right \rceil , n \right) + 1$$

Dove e $n$ è la dimensione del input space  e vale che $$ \left\lceil    \frac{D^2}{\rho^2} \right\rceil= \left\lceil  \frac{D^2}{\left(\cfrac{2}{\|\mathbf{w}\|}\right)^2}  \right\rceil= \text{Radios}^2||\mathbf{w}||^2$$

### SVM Soft Margin
Nella **SVM soft margin** si rilassa l'assunzione di avere pattern [[linearmente separabili|linearmente separabili]] il che permette di trattare dati più complessi ma si perde la garanzia di avere $0$ errore di classificazione in training. Si vuole quindi cercare un **iperpiano** che minimizzi la probabilità di errore di classificazione, mediata sull'insieme di addestramento.
 
Per fare ciò si rinuncia al vincolo: $$d_p(\mathbf{w}^T\mathbf{x}_p+b) \geq 1$$e per trattare i punti che rendono il problema non [[Linearmente Separabili|linearmente separabile]] viene introdotto un nuovo insieme di variabili scalari non negative $\xi_i$ dette **slack** $$d_{i}(\mathbf{w}^T\mathbf{x}_{i}+b)\geq 1-\xi_i$$le variabili $\xi_i$ misurano la deviazione di un punto dati dalla condizione ideale (il vecchio vincolo) di separabilità dei pattern. Infatti si ha che:
- Con $0<\xi_i\leq 1$ il punto dati cade all'interno della **margine di separazione**, ma dal lato corretto della **decision surface** (immagine sinistra)
- Con $\xi_i \geq 1$, il punto cade dal lato sbagliato della **decision surface** (immagine destra)
Con questo nuovo vincolo I **vettori di supporto** sono quei punti dati che soddisfano  $$d_{i}(\mathbf{w}^T\mathbf{x}_{i}+b)= 1-\xi_i$$![[IMG - SVM Soft Margin.png]]
![[IMG - SVM - effetto dello slack.png]]
si puo stimare quanto si devia dalla soluzione linearmente separabile con $$\sum^\ell_i\xi_i$$si puo quindi formulare il [[Problemi di ottimizzazione|problema di ottimizazione primale]] con **Soft Margin** come
$$\begin{cases}
\displaystyle\min \frac{\|\mathbf{w}\|^2}{2} + C\cdot \sum^\ell_i\xi_i \\
(\mathbf{w}^T\mathbf{x}_i+b)d_i \geq 1-\xi_i \\
\xi_i \geq 0 
\end{cases}$$
dove $C$: è un iperparametro definito dal utente è vale che 
- _basso_ $C$: sono permessi molto errori sul $TS$, possibile _underfitting_
- _alto_ $C$: sono permessi pochi errori sul $TS$, margine piccolo, possibile __overfitting__.
questo modello non fa piu [[Statistical Learning Theory (SLT)|Structural Rrisk Minimization]].

Si puo riformulare il problema nella sua forma [[Problemi di ottimizazione - Dualità|duale]] come$$ 
\begin{cases}
\displaystyle \sum_{i=1}^{\ell} \alpha_i - \frac{1}{2} \sum_{i=1}^{\ell} \sum_{j=1}^{\ell} \alpha_i \alpha_j d_i d_j \mathbf{x}_i^T \mathbf{x}_j  \\
\displaystyle \sum_{i=1}^{\ell} \alpha_i d_i = 0 \\
 0 \leq \alpha_i \leq C 
\end{cases}
$$ In questa forma duale non compaiono ne le variabile $\xi_i$ ne i moltiplicatori lagrangiani associati a queste ultime. questo problema è simile al duale del __Hard Margin__ ma c è un vincolo piu stringente ovvero $0 \leq \alpha_i \leq C$







## Kernel Macchine 
Grazie al [[Teorema di copertura (Cover Theorem)|teorema di copertura]] sappiamo che in dimensione piu alta è piu probabile che i dati siano linearmente separabili. Quindi si mappano i __data point__ da uno spazio a bassa dimenzione dove i dati non sono linearmente separabili in un __feature space__ dove questi sono probabilmente __[[linearmente separabili|linearmente separabili]]__ 
![[C4A28AD4-0704-4A15-BC1A-8E441D8DEC98.jpeg]]
in generale questo approccio puo essere __computazionalmente infattibile__ è rende i modelli prono ad __overfitting__ se non regolarizato, questo avviene siccome la complessità del modello aumenta con l aumentare della dimenzionalita della espansione LBE.

 per risolvere questi due problemi si utilizzano i __kernel__ per fare la __[[Linear Basis Expansion (LBE)|liner basis expansion]]__  del modello in modo da poter classificare correttamente anche casi non [[Linearmente Separabili|linearmente separabili]] 
 


Sia $\Phi: \mathbb{R}^{m_0} \to \mathbb{R}^{m_1}$ una [[Funzioni|funzione]] definita come $$\Phi(\mathbf{x}) = (\phi_0(\mathbf{x}) = 1, \phi_1(\mathbf{x}), \dots, \phi_{m_1}(\mathbf{x}))^T$$ dove ogni $\phi_i(\mathbf{x})$ è detto __feature vector__ 
allora possiamo formulare il problema come nella versione **Hard Margin** ma il set di training ora diventa:$$
TR = \{ (\Phi(\mathbf{x}_i), d_i) \}_{i=1}^{N}
$$e incorporando il bias nei pesi $w_0 = b$ si ha che la superfice di separazione ora espressa come:$$ \mathbf{w}^T \Phi(\mathbf{x}) = 0 $$è questa è [[Linear Basis Expansion (LBE)|linear basis expantion]], con le seguenti proprietà:
1. La dimensione dello spazio trasformato può essere molto grande.
2. La complessità del modello dipende dal margine, non direttamente dalla dimensione dello spazio.



seguendo gli stessi ragionamenti fatti per il problema __hard Marign__ otteniamo che $\mathbf{w}$ è una __[[Combinazioni Lineari|combinazione lineare]]__ dei __feature vector__ dei punti di training:$$\mathbf{w} = \sum_{i=1}^{\ell} \alpha_i d_i \Phi(\mathbf{x}_i)$$Quindi, l'equazione dell'iperpiano diventa:$$
\sum_{i=1}^{\ell} \alpha_i d_i \underbrace{\Phi^T (\mathbf{x}_i) \Phi(\mathbf{x})}_{\text{dot product}} = 0
$$
- Il [[prodotto scalare|prodotto scalare]] $\Phi^T(\mathbf{x}_i) \Phi(\mathbf{x})$ avviene in **feature space**.
- Il calcolo esplicito di $\Phi(\mathbf{x})$ potrebbe essere intrattabile in termini computazionali.

Sotto certe condizioni, **non è necessario valutare direttamente** $\Phi(\mathbf{x})$, non è neanche necessario **conoscere esplicitamente lo feature space**
Questo è possibile grazie a una funzione che calcola direttamente il [[prodotto scalare|prodotto scalare]] in feature space definito dalla funzione **inner product kernel function**:$$k : \mathbb{R}^{m_0} \times \mathbb{R}^{m_0} \to \mathbb{R}$$è definita come:$$k(\mathbf{x}_i, \mathbf{x}) = \Phi^T(\mathbf{x}_i) \Phi(\mathbf{x})$$questa è una funzione **simmetrica**, ossia vale: $k(\mathbf{x}_i, \mathbf{x}) = k(\mathbf{x}, \mathbf{x}_i)$ è questo è detto __Kernel trick__. Possiamo organizzare i *inner product kernel function* tra le immagini dei pattern di addestramento in una matrice $\ell \times \ell$ chiamata **matrice del kernel**:$$
K =
\begin{pmatrix}
k(\mathbf{x}_1, \mathbf{x}_1) & \dots & k(\mathbf{x}_1, \mathbf{x}_\ell) \\
k(\mathbf{x}_2, \mathbf{x}_1) & \dots & k(\mathbf{x}_2, \mathbf{x}_\ell) \\
\vdots & \ddots & \vdots \\
k(\mathbf{x}_\ell, \mathbf{x}_1) & \dots & k(\mathbf{x}_\ell, \mathbf{x}_\ell)
\end{pmatrix}
$$ o equivalentemente:$$K = \{ k(\mathbf{x}_i, \mathbf{x}_j) \}_{(i,j)=1}^{N}$$e poiché il kernel è una funzione di prodotto interno nello spazio delle feature, la matrice del kernel è **[[Matrici quadrate|simmetrica]]**.


Non per tutte le funzioni di __kernel__ $\Phi$ si riesce a definire la funzione *inner product kernel function* $k$. Infatti lo si puo fare solo per quelle che hanno una matrice dei kernel $K$ [[Matrici Definite|semi-definita positiva]]  è questo è un caso speciale del [[Teorema di Mercer|teorema di Mercer]]

Siano $k_1$ e $k_2$ due funzioni kernel definite su $\mathbb{R}^{m_o} \times \mathbb{R}^{m_o}$. Le seguenti combinazioni di kernel sono anch'esse __funzioni kernel__ valide:
- **Somma di kernel** $k_1(\mathbf{x}, \mathbf{y}) + k_2(\mathbf{x}, \mathbf{y})$
- **Moltiplicazione per uno scalare positivo**: $\alpha k_1(\mathbf{x}, \mathbf{y}) \quad \forall \alpha \in \mathbb{R}_+$
- **Prodotto di kernel**: $k_1(\mathbf{x}, \mathbf{y}) k_2(\mathbf{x}, \mathbf{y})$
Queste proprietà garantiscono che possiamo costruire nuovi kernel combinando kernel noti.

Alcuni dei kernel piu usati sono:
1. __Polinomiale__: di potenza $k(\mathbf{x}_i,\mathbf{x}_j)=(\mathbf{x}_i^T\mathbf{x}_j+1)^p$ dove $p$ è un **iper-parametro**.
	- il **feature space** ha dimensionalità pari a $p$
2. **RBF** (**radial-basis function**) anche detta **guassiana**: $k(\mathbf{x}_i,\mathbf{x}_j)=e^{-\cfrac{\|x_i-x_j\|^2}{2\sigma^2}}$ dove $\sigma$ è un iperparamentro
	- il mapping è in un **feature space** di dimenzionalita  $\infty$ quindi molto complesso e puo portare ad overfitting. 
3. **Two layer perceptron** $k(\mathbf{x}_i,\mathbf{x}_j)=\tanh(\beta_0\mathbf{x}^T\mathbf{x}_i+\beta_1)$ dove $\beta_0>0$ e $\beta_1<0$ sono **iper-parametri** 
	- Per questo tipo di kernel si riesce a definire l __inner product__ solo per certe scelte di $\beta_0$ e $\beta_1$

Si puo usare la matrice dei kernel per definire problemi primali e duali della SVM semplicemente sostituendo $K(x_i,x_j)$ a $x_i^Tx_j$ mentre per predire la classe di un $\mathbf{x}$ mai visto dal modello si usa l'ipotesi: $$h_w(\boldsymbol x) = sign \left(\sum_{i\in SV}\alpha_iy_iK(\mathbf{x},\mathbf{x}_i) +b \right)$$





Si puo vedere la SVM come avente un architettura simile alle [[Reti Neurali (NN)|rete neurale]] ma il funzionamento dei neuroni è diverso, ogni peso non è libero e deve sottostare ai vincoli della SVM.  
![[IMG - SVM come Rete neurale.png]]
Ogni neurone prima del output è il valore di un kernel.






