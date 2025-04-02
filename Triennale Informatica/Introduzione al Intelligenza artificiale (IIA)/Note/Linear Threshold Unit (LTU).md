---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic:
---
# Linear Trashold Unit (LTU)
---
Il [[Modelli lineari con LMS|modello lineare]] anche  puo essere usato per la __[[Algoritmi di learning supervisionato|classificazione]]__ utilizzando l ipotesi  $h(\mathbf{w})=\mathbf{w}^T \boldsymbol x$

### Classificazione Binaria
Geometricamente possiamo vedere la classificazione come un _Iperpiano_

![[D83C8A5E-E4F9-46AD-BDF1-F31C5018F693.jpeg]]
![[F17F5BAE-D1D4-4EF9-8A3B-4BE196FB84FA.jpeg]]
possiamo decidere della classificazione con delle funzioni  utilizzando le _linear threshold unit (LTU)_
$$\begin{array}{}
h(x) = 
\begin{cases}
	1 & if & \boldsymbol w^t \boldsymbol x +w_0 \geq 0  \\ 
	0 & & otherwise
\end{cases} & 
	\begin{array}{}[0,1] \\
	\text{output range}
	\end{array}\\
h(x)= sign (\boldsymbol w^t \boldsymbol x+w_0) & \begin{array}{}[-1,1] \\
\text{output range}
\end{array}

\end{array}
$$
$w_0$ è detto _trashold_ infatti per enfatizzare si può riscrivere la prima __LTU__ come $\boldsymbol w^t \boldsymbol x  \geq -w_0$ 


l __Apprendimento__ definito come una ricerca
- _Dato_ : un Training Set  di $n$ del tipo $(x_p,y_p) \ p=1\dots n$ 
- _Trova_: $h_w(x)$ nella forma $\boldsymbol w$  che minimizza l expected loss sui dati di training
Si definisce una funzione _$Loss$_ come    $$E(w)= \sum_{p=1}^n(y_p-\boldsymbol x_p^T \boldsymbol w)^2= \|\boldsymbol y-\boldsymbol X\boldsymbol w \|^2 $$anche in questo caso possiamo usare l algoritmo di _[[#Gradient descent (local serach)|Gradient descent]]_.
l algoritmo puo essere visto come una regola di correzione. se un elemento viene mal classificato si aumentano o diminuiscono i parametri proporzionalmente a $\eta$ 
![[D71CEA55-0B20-46D7-8E28-A7C2F04F3877.jpeg]]
da qui si può espandere con cui che vale nel caso di regressione. 
 
quest i tipi di modelli danno una soluzione esatta solo quando i dati sono  [[Linearmente Separabili|lineramente separabili]], per superare questa problematica si può usare la [[Linear Basis Expansion (LBE)| linear basis expansion]] che permette di esmpimere decision baundry per complessi  
![[E0A08BCF-3CA8-42A6-A2F5-076F046AC0AA.jpeg]]


#### Classificazione multi classe

La classificazione multi-classe si affronta con la rappresentazione **1-of-K**, dove ogni classe è codificata come un vettore binario.  
Esempio:  $\{rosso, verde, blu\} → (0,0,1), (0,1,0), (1,0,0)$

Due strategie principali per risolvere questo problema sono:

1. **One-Versus-All (OVA)**:  
   - Si costruisce un classificatore binario per ogni classe. Ogni classificatore discrimina una classe dalle altre $K-1$.
   - In fase di addestramento, vengono creati  $K$  classificatori distinti. Ogni classificatore distingue una classe positiva da tutte le altre.
   - Per classificare un nuovo esempio, si eseguono tutti i $K$ classificatori e si sceglie la classe associata al classificatore con il valore più alto (più positivo).

2. **All-Versus-All (AVA)**:  
   - Si costruisce un classificatore binario per ogni coppia di classi, richiedendo $\frac{K(K-1)}{2}$ classificatori.
   - Ogni classificatore distingue tra due specifiche classi ignorando le altre.
   - Per classificare un esempio, si eseguono tutti i classificatori. La classe finale viene determinata tramite:
     - **Somma dei Valori**: La classe con la somma massima dei valori viene scelta.
     - **Votazione a Maggioranza**: La classe con il maggior numero di voti è selezionata.
   - Un vantaggio di AVA è che il dataset di addestramento per ogni classificatore è molto più piccolo rispetto a OVA.

Tuttavia, questi approcci presentano alcune problematiche:
- **Mascheramento**: Per un numero elevato di classi $K$, alcune classi possono essere oscurate o mascherate da altre.
- **Sofisticazione**: Esistono tecniche avanzate per migliorare le performance della classificazione multi-classe.
- **Modelli Multi-Output**: Alcuni modelli gestiscono direttamente problemi multi-classe senza la necessità di trasformarli in classificazioni binarie.


![[Pasted image 20241220032912.png]]