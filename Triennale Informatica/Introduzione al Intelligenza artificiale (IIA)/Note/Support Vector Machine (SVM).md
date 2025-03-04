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
la __Support Vector Macchine__ (SVM) è modello di [[Concetti generali del Machine Learning|machne learning]] che fonda la sua base teorica del [[Statistical Learning Theory (SLT)|SLT]] e ha i 2 seguenti obiettivi
1. Controllare la complessità del modello tramite un un approccio di ottimizzazione [[Problemi di ottimizzazione|problema di ottimizzazione]]
2. Espandere la flessibilità con una _Basis Expansion_ cosi come fatto nel [[Modelli lineari con LMS|modello lineare]]


### Approccio di ottimizzazione 
in un caso di classificazione con il [[Modelli lineari con LMS|modello lineare]] non tutte le ipotesi $h$ sono uguali
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
>a differenza del [[Modelli lineari con LMS|modelli lineare]] in questo abbiamo un errore pari a 0 se le regioni sono [[Linearmente Separabili|linearmente separabili]]

#### Proprietà
_Margin_:  è definito da $\frac{2}{\|\boldsymbol w\|}$  quindi 
- massimizzare il margine $\iff$ minimizzare $\|\boldsymbol w\| \iff$ minimizzare $\frac{\|\boldsymbol w\|^2}{2}$  
	- Dove $\|\boldsymbol w\|^2 = (\boldsymbol w^T \boldsymbol w)$

il _VC-Dim_ delta [[Statistical Learning Theory (SLT)|SLT]] è l inverso del margine ovvero decresce come l aumentare del margine 
- con questo fatto si può quindi controllare la complessità del modello

e quindi si conclude che l _iperpiano ottimale_ è quello che massimizza il margine e soddisfa il problema (sui [[Validation e Test di una modello di ML|dati di training]])

### Espressione formale del problema di apprendimento 
problema [[Problemi di ottimizzazione|problema primare di ottimizzazione]] 
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





# Support Vector Machines (SVM)

## **Concetti Fondamentali**

Le Support Vector Machines (SVM) sono modelli di apprendimento supervisionato utilizzati per la classificazione e la regressione. Il principio fondamentale è trovare un **iperpiano ottimale** che separi i dati massimizzando il margine tra le classi.

### **1. Iperpiano e Margine**

Dato un insieme di dati di addestramento $ {(x_i, y_i)} $ con $ y_i \in {-1, 1} $, una SVM cerca un iperpiano definito come:

w⋅x+b=0 w \cdot x + b = 0

Il margine è dato da:

2∣∣w∣∣\frac{2}{||w||}

L'obiettivo è massimizzare il margine risolvendo il problema di ottimizzazione:

min⁡w,b12∣∣w∣∣2\min_{w, b} \frac{1}{2} ||w||^2

soggetto a:

yi(w⋅xi+b)≥1,∀i. y_i (w \cdot x_i + b) \geq 1, \quad \forall i.

Un margine più ampio riduce l'overfitting e migliora la generalizzazione del modello.

### **2. Soft Margin (Per Dati Non Linearmente Separabili)**

Per gestire dati **non linearmente separabili**, si introduce una variabile di slack $\xi_i$ che permette la violazione del vincolo:

min⁡w,b,ξ12∣∣w∣∣2+C∑iξi\min_{w, b, \xi} \frac{1}{2} ||w||^2 + C \sum_{i} \xi_i

soggetto a:

yi(w⋅xi+b)≥1−ξi,∀i, y_i (w \cdot x_i + b) \geq 1 - \xi_i, \quad \forall i,

con $\xi_i \geq 0$ e $C$ parametro che bilancia la penalità delle violazioni.

Valori più alti di $C$ comportano un adattamento più preciso ai dati di training, aumentando il rischio di overfitting, mentre valori più bassi favoriscono un margine più ampio a discapito di errori di classificazione.

### **3. Kernel Trick e Trasformazione dello Spazio**

Quando i dati non sono linearmente separabili nello spazio originale, si utilizza una **funzione kernel** $ K(x_i, x_j) $ per mappare i dati in uno spazio di dimensione superiore dove diventano separabili:

K(xi,xj)=ϕ(xi)⋅ϕ(xj)K(x_i, x_j) = \phi(x_i) \cdot \phi(x_j)

Esempi di kernel comuni:

- **Lineare**: $ K(x_i, x_j) = x_i \cdot x_j $ (utile per problemi lineari semplici)
- **Polinomiale**: $ K(x_i, x_j) = (x_i \cdot x_j + c)^d $
- **Gaussiano (RBF)**: $ K(x_i, x_j) = e^{-\gamma ||x_i - x_j||^2} $
- **Sigmoide**: $ K(x_i, x_j) = \tanh(\alpha x_i \cdot x_j + c) $

La scelta del kernel ha un impatto significativo sulle prestazioni del modello e deve essere selezionata con cura in base alla distribuzione dei dati.

### **4. Support Vector Regression (SVR)**

L'estensione delle SVM alla **regressione** è nota come **Support Vector Regression (SVR)**. In questo caso, l'obiettivo è trovare una funzione che approssimi i dati minimizzando gli errori.

Il problema di ottimizzazione diventa:

$$min⁡w,b,ξ,ξ∗12∣∣w∣∣2+C∑i(ξi+ξi∗)\min_{w, b, \xi, \xi^*} \frac{1}{2} ||w||^2 + C \sum_{i} (\xi_i + \xi_i^*)$$

soggetto a:

$$yi−(w⋅xi+b)≤ϵ+ξi y_i - (w \cdot x_i + b) \leq \epsilon + \xi_i (w⋅xi+b)−yi≤ϵ+ξi∗ (w \cdot x_i + b) - y_i \leq \epsilon + \xi_i^* ξi,ξi∗≥0 \xi_i, \xi_i^* \geq 0$$

Dove:

- **$\epsilon$** definisce una soglia di errore accettabile.
- **$\xi_i, \xi_i^*$** sono variabili di slack per permettere violazioni della soglia.
- **$C$** controlla il trade-off tra complessità del modello ed errori.

SVR utilizza gli stessi **kernel** delle SVM per mappare i dati in uno spazio ad alta dimensionalità e adattare modelli non lineari.

### **5. Parametri Importanti**

- **C**: Controlla il trade-off tra massimizzazione del margine e minimizzazione degli errori.
- **$\gamma$ (per RBF Kernel)**: Determina l'influenza dei singoli punti campione.
- **$\epsilon$ (per SVR)**: Definisce la tolleranza per la regressione, influenzando la sparseness del modello.
- **Tipo di Kernel**: Definisce la mappatura dello spazio dei dati e la separabilità lineare nel nuovo spazio.

### **6. Applicazioni e Considerazioni Pratiche**

- **SVM per classificazione** è stato storicamente utilizzato con successo nel riconoscimento della scrittura (es. dataset MNIST con errore dello 0.8%).
- **SVR** è utile per problemi di regressione, come previsioni di mercato e modelli di serie temporali.
- La scelta dei parametri (C, kernel e iperparametri) è cruciale e spesso richiede **cross-validation**.
- Gli SVM possono essere inefficienti su dataset molto grandi (>20,000 campioni) a causa della complessità computazionale.
- SVM possono essere combinati con metodi di riduzione della dimensionalità come PCA per migliorare le prestazioni su dati ad alta dimensionalità.

## **Conclusioni**

Le SVM offrono un framework potente per la classificazione e la regressione, con solidi fondamenti teorici. Tuttavia, la scelta del kernel e degli iperparametri è critica per le prestazioni del modello.

L'uso di tecniche di ottimizzazione avanzate e l'integrazione con metodi di riduzione della dimensionalità possono migliorare l'efficienza computazionale, rendendo SVM ancora rilevante in molti contesti moderni.





----


---
# Support Vector Machines (SVM)

Le Support Vector Machines (SVM) sono un insieme di reti feed forward del tipo *kernel-learning method*.

L'obiettivo principale è trovare un iperpiano che separi al meglio le classi nei dati.


*DEF.*
Dato un insieme di dati di training, una SVM costruisce un iperpiano (superficie di decisione) in cui si vuole *massimizzare* il *margine di separazione* tra la classe positiva e negativa.

Si assume che il problema dato sia linearmente separabile e che le classi in cui si possono dividere i dati siano $d=\pm 1$ .
Detto ciò, l'iperpiano di separazione si definisce come $$\mathbf{w}^T\mathbf{x}+b=0$$
Dove $\mathbf{x}$ è il vettore di input e $\mathbf{w}$ è il vettore dei pesi.

#### Margine di separazione e iperpiano ottimale
---
Per ogni vettore $\mathbf{w}$ la distanza tra l'iperpiano di separazione ed il data point più vicino si chiama **Margine di separazione** $\rho$.
![[margin svm.png]]


L'obiettivo di una SVM è quello di cercare l'**iperpiano ottimale**  per cui il margine di separazione è massimizzato.
L'**iperpiano ottimale** è dato da $\mathbf{w}_{o}$ e $b_{o}$ che sono i valori ottimali del vettore dei pesi e del bias, e si definisce come : $$\mathbf{w}_{o}^T\mathbf{x}+b_{o}=0$$
Esistono diversi iperpiani che possono risolvere il problema ma l'iperpiano ottimale è unico.
#### Funzione discriminante
---
La funzione discriminante $g(\mathbf{x})$ è la misura algebrica della distanza del vettore di input $\mathbf{x}$ dall'iperpiano ottimale e si definisce come:
$$g(\mathbf{x})=\mathbf{w}_{o}^T\mathbf{x}+b_{o}$$
Da questa funzione si può riesprimere il vettore $\mathbf{x}$ come:
$$\mathbf{x}=\mathbf{x}_{p}+r\frac{\mathbf{w}_{o}}{||\mathbf{w}_{o}||}$$
Dove $\mathbf{x}_{p}$ è la proiezione di $\mathbf{x}$ sull'iperpiano ottimale ed $r$ è la distanza di $\mathbf{x}$ dall'iperpiano ottimale.
$r$ è positiva se $\mathbf{x}$ si trova nel lato positivo dell'iperpiano,  negativa se si trova nella parte negativa, e uguale a 0 s e si trova sull'iperpiano. 

Quindi per definizione, dato che $\mathbf{x}_{p}$ appartiene all'iperpiano, si ha 
che $g(\mathbf{x}_{p})=0$. 
Da ciò:
$$g(\mathbf{x}_{p})=\mathbf{w}_{o}^T\mathbf{x}_{p}+b_{o}=\mathbf{w}_{o}^T\left( \mathbf{x}_{p}+r\frac{\mathbf{w}_{o}}{||\mathbf{w}_{o}||}\right)+b_{o}=g(\mathbf{x}_{p})+r\frac{||\mathbf{w}_{o}||^2}{||\mathbf{w}_{o}||}=r||\mathbf{w}_{o}||$$
 
Quindi : $r=\frac{g(\mathbf{x}_{p})}{||w_{o}||}$ , e ciò è valido in generale e si ha : $$r=\frac{g(\mathbf{x})}{||\mathbf{w}_{o}||}$$
In particolare la distanza dell'origine dall'iperpiano è $\frac{b_{o}}{||\mathbf{w}_{o}||}$ e se $b_{o }>0$ l'origine è nella parte positiva dell'iperpiano, se <0 nella parte negativa e se =0 allora e sull'iperpiano.

![[geometrical view SVM.png]]

Date le condizioni dell'iperpiano:
$$\begin{cases}
\mathbf{w}^T\mathbf{x}_{i}+b \geq 0 \text{ if } d_{i}=+1 \\
\mathbf{w}^T\mathbf{x}_{i}+b \leq 0 \text{ if } d_{i}=-1
\end{cases}$$
si possono riscalare i vettori $\mathbf{w}$ e $\mathbf{b}$ in modo che i punti più vicini all'iperpiano soddisfino : $|g(\mathbf{x}_{i})|=|\mathbf{w}^T\mathbf{x}_{i}+b|=1$

Le condizioni si possono così riscrivere come:
$$\begin{cases}
\mathbf{w}^T\mathbf{x}_{i}+b \geq +1 \text{ if } d_{i}=+1 \\
\mathbf{w}^T\mathbf{x}_{i}+b \leq -1 \text{ if } d_{i}=-1
\end{cases}$$
Ed in forma più compatta: $d_{i}(\mathbf{w}^T\mathbf{x}_{i}+b)\geq 1\ \forall \ i=1,\dots,N$

### Support vector
---
I **support vector** sono quei vettori che si trovano esattamente sul margine di separazione, e sono quindi quelli più vicini all'iperpiano.

I support vector $\mathbf{x}^{(s)}$ soddisfano esattamente l'equazione:
$$d^{(s)}(\mathbf{w}^T\mathbf{x}^{(s)}+b)=1$$

![[support vectors.png]]

Per i support vector la funzione discriminante vale $\pm {1}$ a seconda del valore di $d^{(s)}$ e quindi la distanza algebrica dei SV dall'iperpiano è data da:
$$r=\frac{g(\mathbf{x}^{(s)})}{||\mathbf{w}_{o}||}=\begin{cases}
\frac{1}{||\mathbf{w}_{o}||}\text{  if } d^{(s)}=+1 \\
-\frac{1}{||\mathbf{w}_{o}||}\text{  if } d^{(s)}=-1
\end{cases}$$
Detto ciò si definisce il margine di separazione $\rho=2r=\frac{2}{||\mathbf{w}_{o}||}$

*OBIETTIVO SVM* : Massimizzare $\rho$ $\leftrightarrow$ Minimizzare $||\mathbf{w}_{o}||$


# Miglioramento della generalizzazione
---

Con le SVM si fissa l'errore di training per problemi linearmente separabili. Minimizzare la norma di $\mathbf{w}$ è equivalente a minimizzare la VC-dimension e quindi minimizzare il termine $\epsilon$ (VC-confidence) nella [[Statistical Learning Theory - Vapnik|STL]].

*Teorema di Vapnik:*
	Sia $D$ il diametro della palla più piccola che si trova attorno agli esempi di training $\{\mathbf{x}_{i}\}_{i=1}^N$.
	Per la classe di iperpiani di separazione descritta da dall'equazione $\mathbf{w}^T\mathbf{x}+b=0$, il limite superiore della VC-dimension è : $$VC \leq \min \left( \left \lceil   \frac{D^2}{\rho^2} \right \rceil , m_o \right) + 1$$

Dove $\left \lceil   \frac{D^2}{\rho^2} \right \rceil= \text{Radios}^2||\mathbf{w}||^2$

![[Pasted image 20250210173926.png]]
 Non ho capito

## Approccio elegante
---
Per i dati linearmente separabili posso esserci molteplici soluzioni e l'approccio di Vapnik propone un *iperpiano di separazione ottimale* massimizzando il margine fornendo :
- Una soluzione unica con zero errori per il classificatore binario 
	- non vale per il algoritmo di learning iterativo  del percettrone e non per la LMS
- Un approccio automatizzato della SRM che minimizza la VC-confidence come parte del processo di training. senza iperparametri nel caso di dati linearmente separabili
- L'uso di un solver della classe dei problemi quadratici vincolati con una forma duale 
- Una soluzione incentrata sui dati di training selezionati (i support vector)