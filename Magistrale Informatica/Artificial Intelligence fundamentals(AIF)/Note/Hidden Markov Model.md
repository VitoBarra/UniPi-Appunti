---
Course: "[[Generative and Deep Learning (GDL)]]"
Corse 1: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
  - GDL
Area:
topic:
SubTopic:
---

# Hidden Markov Model
---
L’**Hidden Markov Model** (HMM) è un [[Modelli temporali probabilistici|modello probabilistico temporale]]  in cui il processo sottostante è descritto da una singola [[Variabili Aleatorie (Casuali)|variabile casuale discreta]] $X_t$, che rappresenta lo stato nascosto del sistema al tempo $t$. Gli stati possibili di $X_t$ costituiscono l’insieme delle configurazioni del mondo osservato, mentre le variabili di evidenza $E_t$ forniscono le osservazioni parziali o rumorose di tali stati. 
Questa restirzione permette di fare delle implementazioni specializzate della framework generico di [[Modelli temporali probabilistici|inferenza con modelli probabilistici temporali]].

il **modello di transizione** definito da $\mathcal{P}(X_t \mid X_{t-1})$, descrive la probabilità di passare da uno stato $i$ a uno stato $j$ e viene rappresentato da una matrice quadrata $T$ di dimensione $S \times S$, con elementi $T_{ij} = \mathcal{P}(X_t = j \mid X_{t-1} = i)$. 

il **modello sensoriale** definito come $\mathcal{P}(e_t \mid X_t)$, specifica la probabilità di osservare l’evidenza $e_t$ dato lo stato $X_t$, e viene rappresentato da una [[Matrici quadrate|matrice diagonale]] $O_t$, i cui elementi diagonali $(O_t)_{ii}$ corrispondono a $\mathcal{P}(e_t \mid X_t = i)$.  

La rappresentazione matriciale consente di formulare le equazioni di inferenza in modo compatto e computazionalmente efficiente. La procedura di **filtering** aggiorna la distribuzione a posteriori sullo stato corrente in base alla nuova evidenza, secondo l’equazione:$$
f_{1:t+1} = \alpha \, O_{t+1} T^{\top} f_{1:t}
$$dove $f_{1:t}$ rappresenta il messaggio in avanti $\mathcal{P}(X_t \mid e_{1:t})$ e $\alpha$ è un fattore di normalizzazione.  

L’**algoritmo backward** calcola invece il messaggio all’indietro $b_{k+1:t}$, che incorpora l’influenza delle osservazioni future, attraverso:

$$
b_{k+1:t} = T O_{k+1} b_{k+2:t}
$$

L’**algoritmo forward–backward**, combinando i due messaggi, fornisce la distribuzione smoothed $\mathcal{P}(X_k \mid e_{1:t})$ per ogni istante $k$. Tuttavia, tale approccio richiede spazio proporzionale alla lunghezza della sequenza osservata.  

Una formulazione alternativa consente di ottenere lo **smoothing** in spazio costante, propagando simultaneamente i messaggi forward e backward in un’unica passata, grazie alla trasformazione inversa delle equazioni di filtraggio. Questo approccio richiede che la matrice di transizione $T$ sia invertibile e che il modello sensoriale non contenga elementi nulli, condizione che garantisce la validità della moltiplicazione inversa $O_t^{-1}$.  

In un contesto di inferenza online, si adotta lo **smoothing a ritardo fisso (Fixed-Lag Smoothing)**, che consente di stimare la distribuzione smoothed per uno stato $X_{t-d}$, mantenendo un ritardo $d$ costante rispetto al tempo corrente $t$. L’idea centrale consiste nel mantenere e aggiornare due strutture: il messaggio forward $f$ e una matrice di trasformazione backward $B$, che sintetizza l’effetto congiunto delle osservazioni più recenti.  

La matrice $B$ è definita come il prodotto cumulativo delle trasformazioni di transizione e osservazione:

$$
B_{t-d+1:t} = \prod_{i=t-d+1}^{t} T O_i
$$

Essa consente di trasformare il messaggio backward più recente in quello relativo a uno stato precedente. L’aggiornamento incrementale di $B$ avviene secondo la relazione:

$$
B_{t-d+2:t+1} = O_{t-d+1}^{-1} T^{-1} B_{t-d+1:t} T O_{t+1}
$$

che permette di incorporare le nuove evidenze man mano che arrivano, senza rieseguire l’intera sequenza di moltiplicazioni.  

L’algoritmo operativo per lo [[Modelli temporali probabilistici|smoothing]] a ritardo fisso è sintetizzato nello schema seguente:
```pseudo
\begin{algorithm}
\caption{Fixed-Lag Smoothing}
\begin{algorithmic}
\Function{Fixed-Lag-Smoothing}{$e_t, hmm, d$}
    \State \textbf{returns} a distribution over $X_{t-d}$
    \State \textbf{inputs:} $e_t$, the current evidence for time step $t$
    \State $hmm$, a hidden Markov model with $S \times S$ transition matrix $T$
    \State $d$, the length of the lag for smoothing
    \State \textbf{persistent:} $t$, the current time, initially 1
    \State $f$, the forward message $\mathcal{P}(X_t \mid e_{1:t})$, initially $hmm$.Prior
    \State $B$, the $d$-step backward transformation matrix, initially the identity matrix
    \State $e_{t-d:t}$, double-ended list of evidence from $t-d$ to $t$, initially empty
    \State \textbf{local variables:} $O_{t-d}, O_t$, diagonal matrices containing the sensor model information
    \State add $e_t$ to the end of $e_{t-d:t}$
    \State $O_t \gets$ diagonal matrix containing $\mathcal{P}(e_t \mid X_t)$
    \If{$t > d$}
        \State $f \gets$ \Call{Forward}{$f, e_{t-d}$}
        \State remove $e_{t-d-1}$ from the beginning of $e_{t-d:t}$
        \State $O_{t-d} \gets$ diagonal matrix containing $\mathcal{P}(e_{t-d} \mid X_{t-d})$
        \State $B \gets O_{t-d}^{-1} T^{-1} B T O_t$
    \Else
        \State $B \gets B T O_t$
    \EndIf
    \State $t \gets t + 1$
    \If{$t > d + 1$}
        \Return \Call{Normalize}{$f \times B \mathbf{1}$}
    \Else
        \Return null
    \EndIf
\EndFunction
\end{algorithmic}
\end{algorithm}
```
Questo procedimento permette di mantenere la complessità temporale indipendente dalla lunghezza totale della sequenza, aggiornando in modo efficiente la stima smoothed con ogni nuova osservazione.





# Hidden Markov chains
---
Hidden Markov chains (o Hidden Markov Models, HMM) sono modelli **probabilistici con variabili latenti** progettati per descrivere sequenze di osservazioni generate da uno stato nascosto che evolve nel tempo.

Il modello assume due tipi di variabili:
- una sequenza di **stati latenti** $Z_1,\dots,Z_T$
- una sequenza di **osservazioni** $X_1,\dots,X_T$

Gli stati latenti rappresentano il processo nascosto che evolve nel tempo mentre le osservazioni sono le variabili osservabili generate dagli stati.

La struttura probabilistica del modello è definita da due assunzioni principali:
- **Markov property** sugli stati nascosti  
- **conditional independence** delle osservazioni dato lo stato corrente

Formalmente:

- proprietà di Markov del primo ordine  
$P(Z_t \mid Z_{1:t-1}) = P(Z_t \mid Z_{t-1})$

- indipendenza condizionata delle osservazioni  
$P(X_t \mid Z_{1:t},X_{1:t-1}) = P(X_t \mid Z_t)$

Questo implica che lo stato corrente dipende solo dallo stato precedente e che ogni osservazione dipende solo dallo stato latente nello stesso tempo.

Il modello può essere rappresentato come un graphical model dinamico:

$$
Z_1 \rightarrow Z_2 \rightarrow Z_3 \rightarrow \dots \rightarrow Z_T
$$

$$
Z_t \rightarrow X_t
$$

Questa struttura induce una fattorizzazione della distribuzione congiunta della sequenza:

$$
P(X_{1:T}, Z_{1:T})
=
P(Z_1)
\prod_{t=2}^{T} P(Z_t \mid Z_{t-1})
\prod_{t=1}^{T} P(X_t \mid Z_t)
$$

dove:
- $P(Z_1)$ è la **distribuzione iniziale degli stati**
- $P(Z_t \mid Z_{t-1})$ è la **transition distribution**
- $P(X_t \mid Z_t)$ è la **emission distribution**

In forma parametrica il modello è definito da tre componenti:
- distribuzione iniziale   $\pi_i = P(Z_1 = i)$
- matrice di transizione tra stati   $A_{ij} = P(Z_t = j \mid Z_{t-1} = i)$
- distribuzione di emissione  $B_j(x) = P(X_t = x \mid Z_t = j)$

Le Hidden Markov chains sono quindi **modelli generativi** per sequenze temporali in cui la dipendenza temporale è modellata tramite una catena di Markov sugli stati latenti mentre le osservazioni sono generate da tali stati.




### Inferenza in HMM


La **inferenza**[[Modelli temporali probabilistici | modelli temporali probabilistici]] si articola in cinque task: filtraggio, previsione, smoothing, spiegazione più probabile.
Ciascuno di essi si basa sulla stima delle distribuzioni di [[Probabilita condizionata| probabilità condizionate]], che descrivono l’evoluzione delle variabili di stato nel tempo in funzione dell’evidenza osservata.


#### Filtering
Il **filtraggio**, o stima dello stato, consiste nel calcolo della distribuzione a posteriori $\mathcal{P}(X_t \mid e_{1:t})$, cioè la probabilità dello stato corrente data l’evidenza accumulata fino al tempo $t$. Tale distribuzione rappresenta la ***belief state***, ovvero la conoscenza dell’agente sullo stato del mondo al tempo presente. Il processo di **filtraggio** si realizza in forma ricorsiva, aggiornando la stima precedente in base alla nuova osservazione.
La formulazione generale del passo di aggiornamento è data da:
$$\mathbf{P}(X_{t+1} \mid e_{1:t+1}) = f(e_{t+1},\mathbf{P}(X_t \mid e_{1:t}))$$
per una qualsiasi funzione $f$ che in particolare possiamo ottenerla come: $$
\begin{aligned}
\mathcal{P}(X_{t+1} \mid  e_{1:t+1}) &= \mathcal{P}(X_{t+1} \mid  e_{1:t}, e_{t+1}) \quad \text{(dividing up the evidence)} \\
&= \alpha \mathcal{P}(e_{t+1} \mid  X_{t+1}, e_{1:t}) \mathcal{P}(X_{t+1} \mid  e_{1:t})  \quad \text{(using Bayes' rule, given } e_{1:t}\text{)} \\
&= \alpha \underbrace{\mathcal{P}(e_{t+1} \mid  X_{t+1})}_{\text{update}} \underbrace{\mathcal{P}(X_{t+1} \mid  e_{1:t})}_{\text{prediction}} \quad \text{(by the sensor Markov assumption)}
\end{aligned}
$$
dove $\alpha$ è una costante di normalizzazione, l update è l aggiornamento delle percezzioni sul nuovo stato e la predizione è il nuovo stato date le evidenze precedenti. Sostituendo la parte di predizione[[Probabilita condizionata| condizionando]] con tutti gli stati precedenti possibili otteniamo$$
\begin{aligned}
\mathcal{P}(X_{t+1} \mid  e_{1:t+1}) &= \alpha \mathcal{P}(e_{t+1} \mid  X_{t+1}) \sum_{x_t} \mathcal{P}(X_{t+1}, x_t, e_{1:t})  \\
&=\alpha \mathcal{P}(e_{t+1} \mid  X_{t+1}) \sum_{x_t} \mathcal{P}(X_{t+1} \mid  x_t, e_{1:t}) \mathcal{P}(x_t \mid  e_{1:t})\\
&= \alpha \underbrace{\mathcal{P}(e_{t+1} \mid  X_{t+1})}_{\text{sensor model}}  \sum_{x_t} \underbrace{\mathcal{P}(X_{t+1} \mid  x_t)}_{\text{transition model}} \underbrace{\mathcal{P}(x_t \mid  e_{1:t})}_{\text{recursion}} \quad \text{(Markov assumption)e}
\end{aligned}
$$L’insieme delle operazioni ricorsive puo essere interpretata come un messaggio filtrato $f_{1:t}$ che viene propagato attraverso la sequenza temporare e quindi $$f_{1:t+1}=FORWARD(f_{1:t}, e_{t+1})$$ Il filtraggio quindi implementa una stima incrementale in **[[Complessita|tempo e spazio costante]]**, indipendentemente dalla lunghezza della sequenza.


#### Previsione
il **task** di **previsione** vuole preddirre lo stato $k$ step avanti rispetto al ultimo dato. la soluzione deriva direttamente dal **filtraggio**, limitandosi a propagare la distribuzione di stato senza considerare nuove osservazioni. La sua formulazione è $$\mathcal{P}(X_{t+k+1} \mid e_{1:t}) = \sum_{x_{t+k}} \mathcal{P}(X_{t+k+1} \mid x_{t+k}) \mathcal{P}(x_{t+k} \mid e_{1:t})$$identico a prima ma senza il **sensor model** e dipende unicamente dal modello di transizione. In generale, dopo un numero sufficientemente elevato di passi, la distribuzione predetta tende a una ***stationary distribution***, che rappresenta il punto fisso del [[Markov chains|processo di Markov]]. Il tempo necessario al raggiungimento di tale stato è detto ***mixing time***. Piu incerto è il modello di transizione piu il **mixing time** è breve. 

##### verosomiglianza del evidenza
Oltre al filtraggio e alla previsione, è possibile calcolare la verosimiglianza della sequenza di evidenze $\mathcal{P}(e_{1:t})$, utile per confrontare diversi modelli temporali. A tal fine, si definisce il messaggio di verosimiglianza $\ell_{1:t}(X_t) = \mathcal{P}(X_t, e_{1:t})$, che segue la stessa ricorsione del filtraggio. La verosimiglianza complessiva è poi ottenuta come$$L_{1:t} = \mathcal{P}(e_{1:t}) = \sum_{x_t} \ell_{1:t}(x_t)$$Un problema pratico rilevante è l’underflow numerico, poiché le probabilità dei messaggi tendono a valori molto piccoli con l’aumentare di $t$.


##### Smoothing
Lo **smoothing**, estende il filtraggio consentendo di calcolare la distribuzione di uno stato passato $\mathcal{P}(X_k \mid e_{1:t})$, con $0 \leq k < t$, incorporando così l’intera sequenza di evidenze fino al presente. La decomposizione di tale distribuzione è
$$
\begin{aligned}
\mathcal{P}(X_k | e_{1:t}) &= \mathcal{P}(X_k \mid  e_{1:k}, e_{k+1:t}) \\
&= \alpha \mathcal{P}(X_k \mid  e_{1:k})\mathcal{P}(e_{k+1:t} \mid  X_k, e_{1:k}) \quad \text{(using Bayes' rule, given } e_{1:k}\text{)} \\
&= \alpha \mathcal{P}(X_k \mid  e_{1:k})\mathcal{P}(e_{k+1:t} \mid  X_k) \quad \text{(using conditional independence)} \\
&= \alpha f_{1:k} \times b_{k+1:t}.
\end{aligned}
$$dove $f_{1:k}$ rappresenta il messaggio in avanti e $b_{k+1:t}$ il messaggio all’indietro. Quest’ultimo è definito come e può essere calcolato ricorsivamente tramite$$
\begin{aligned}
b_{k+1:t} &=&\\
\mathcal{P}(e_{k+1:t} \mid X_k) &= \sum_{x_{k+1}} \mathcal{P}(e_{k+1:t} \mid X_k, x_{k+1}) \mathcal{P}(x_{k+1} \mid X_k) \quad \text{(conditioning on } X_{k+1}\text{)} \\
&= \sum_{x_{k+1}} \mathcal{P}(e_{k+1:t} \mid x_{k+1}) \mathcal{P}(x_{k+1} \mid X_k) \quad \text{(by conditional independence)} \\
&= \sum_{x_{k+1}} \mathcal{P}(e_{k+1}, e_{k+2:t} \mid x_{k+1}) \mathcal{P}(x_{k+1} \mid X_k) \\
&= \sum_{x_{k+1}} \underbrace{\mathcal{P}(e_{k+1} \mid x_{k+1})}_{\text{sensor model}} \underbrace{\mathcal{P}(e_{k+2:t} \mid x_{k+1})}_{\text{recursion}} \underbrace{\mathcal{P}(x_{k+1} \mid X_k)}_{\text{transition model}}
\end{aligned}
$$
L’inizializzazione avviene con $b_{t+1:t} = 1$. La combinazione dei due messaggi permette la costruzione dell’algoritmo ***forward–backward***, in cui la fase di propagazione in avanti viene seguita da una propagazione all’indietro e fa lo smoothing in [[complessita|complessita]] $O(t)$ 
```pseudo
\begin{algorithm}
\caption{Forward-Backward}
\begin{algorithmic}
\Function{FORWARD-BACKWARD}{ev, prior}
    \State \textbf{returns} a vector of probability distributions
    \State \textbf{inputs:} ev, a vector of evidence values for steps $1,\ldots,t$
    \State  prior, the prior distribution on the initial state, $\mathcal{P}(X_0)$
    \State \textbf{local variables:} fv, a vector of forward messages for steps $0,\ldots,t$
    \State  b, a representation of the backward message, initially all 1s
    \State  sv, a vector of smoothed estimates for steps $1,\ldots,t$
    \State $fv[0] \gets prior$
    \For{$i = 1$ to $t$}
        \State $fv[i] \gets$ \Call{FORWARD}{$fv[i - 1], ev[i]$}
    \EndFor
    \For{$i = t$ down to $1$}
        \State $sv[i] \gets$ \Call{NORMALIZE}{$fv[i] \times b$}
        \State $b \gets$ \Call{BACKWARD}{$b, ev[i]$}
    \EndFor
    \Return $sv$
\EndFunction
\end{algorithmic}
\end{algorithm}
```

L’algoritmo costituisce un caso particolare del metodo di [[Inferenza con bayesian network - Clustering|propagazione nei polytree]], con la stessa efficienza computazionale.

Dal punto di vista pratico, due limiti principali emergono: la complessità spaziale, che cresce linearmente con la lunghezza della sequenza, e la difficoltà di aggiornamento online. Una soluzione comune consiste nello *fixed-lag smoothing*, in cui si calcola $\mathcal{P}(X_{t-d} \mid e_{1:t})$ per un ritardo fisso $d$, aggiornando in tempo costante a ogni nuova osservazione.



#### determinazione della sequenza piu probabile
La **task determinazione della sequenza di stati più probabile**, data una sequenza di osservazioni, consiste nel calcolare l’argomento che massimizza la probabilità congiunta condizionata, cioè $$\arg\max_{x_{1:t}} \mathcal{P}(x_{1:t} \mid e_{1:t})$$Tale problema viene risolto sfruttando la [[Markov chains|proprietà di Markov]], che consente di esprimere la dipendenza temporale in forma ricorsiva, in modo analogo al filtraggio ma sostituendo l’operatore di somma con un massimo. Si definisce quindi il messaggio 

$$m_{1:t} = \max_{x_{1:t-1}} \mathcal{P}(x_{1:t-1}, X_t, e_{1:t})$$ 

da cui deriva la relazione ricorsiva $$
\begin{aligned}
m_{1:t+1} &= \max_{x_{1:t}} P(x_{1:t}, X_{t+1}, e_{1:t+1}) \\
&= \max_{x_{1:t}} P(x_{1:t}, X_{t+1}, e_{1:t}, e_{t+1}) \\
&= \max_{x_{1:t}} P(e_{t+1} \mid x_{1:t}, X_{t+1}, e_{1:t}) P(x_{1:t}, X_{t+1}, e_{1:t}) \\
&= P(e_{t+1} \mid X_{t+1}) \max_{x_{1:t}} P(X_{t+1} \mid x_t) P(x_{1:t}, e_{1:t}) \\
&= P(e_{t+1} \mid X_{t+1}) \max_{x_t} P(X_{t+1} \mid x_t) \max_{x_{1:t-1}} P(x_{1:t-1}, x_t, e_{1:t})
\end{aligned}
$$ in $m_{i:t+1}$ ci sarà la probabilità della sequenza piu probabile. Questa formulazione costituisce la base dell’algoritmo di **Viterbi**, che permette di individuare in tempo lineare la sequenza di stati più probabile, memorizzando per ciascuno stato il puntatore alla transizione che massimizza la probabilità cumulata. Durante il processo, le probabilità tendono a ridursi progressivamente, rendendo necessario l’impiego di tecniche di stabilizzazione numerica: è possibile normalizzare i valori a ogni passo, poiché $\max(c x, c y) = c \cdot \max(x, y)$, oppure operare nel dominio logaritmico, trasformando i prodotti in somme, dato che la funzione logaritmica è monotona e conserva l’ordinamento delle massime probabilità.



______
---
---
Hidden Markov Models (HMM) sono [[Modelli temporali probabilistici|modelli probabilistici temporali]] con **variabili latenti** utilizzati per descrivere sequenze di osservazioni generate da uno stato nascosto che evolve nel tempo secondo una [[Markov chains|catena di Markov]].

Il modello introduce due sequenze di [[Variabili Aleatorie (Casuali)|variabili casuali]]:

- una sequenza di **stati nascosti** $X_1,\dots,X_T$
- una sequenza di **osservazioni** $E_1,\dots,E_T$

Gli stati rappresentano il processo non osservabile che evolve nel tempo mentre le osservazioni costituiscono evidenze parziali o rumorose dello stato reale del sistema.

La struttura probabilistica del modello è definita da due ipotesi fondamentali.

**Proprietà di Markov sugli stati**

$$
\mathcal{P}(X_t \mid X_{1:t-1}) = \mathcal{P}(X_t \mid X_{t-1})
$$

lo stato corrente dipende soltanto dallo stato precedente.

**Indipendenza condizionata delle osservazioni**

$$
\mathcal{P}(E_t \mid X_{1:t},E_{1:t-1}) = \mathcal{P}(E_t \mid X_t)
$$

ogni osservazione dipende esclusivamente dallo stato nello stesso istante.

La struttura grafica risultante è un [[Graphical model|modello grafico dinamico]] della forma

$$
X_1 \rightarrow X_2 \rightarrow \dots \rightarrow X_T
$$

$$
X_t \rightarrow E_t
$$

Questa struttura induce la fattorizzazione della distribuzione congiunta

$$
\mathcal{P}(X_{1:T},E_{1:T}) =
\mathcal{P}(X_1)
\prod_{t=2}^{T} \mathcal{P}(X_t \mid X_{t-1})
\prod_{t=1}^{T} \mathcal{P}(E_t \mid X_t)
$$

Il modello è quindi completamente specificato da tre componenti.

**Distribuzione iniziale**

$$
\pi_i = \mathcal{P}(X_1 = i)
$$

**Modello di transizione**

$$
T_{ij} = \mathcal{P}(X_t = j \mid X_{t-1} = i)
$$

che descrive la dinamica temporale della catena di Markov.

**Modello di emissione o sensoriale**

$$
\mathcal{P}(E_t \mid X_t)
$$

che descrive il processo di generazione delle osservazioni a partire dagli stati.

Quando lo spazio degli stati è discreto con $S$ stati possibili, il modello di transizione è rappresentato da una [[Matrici quadrate|matrice quadrata]] $T \in \mathbb{R}^{S\times S}$ mentre il modello sensoriale può essere rappresentato da una matrice diagonale

$$
O_t =
\begin{pmatrix}
\mathcal{P}(e_t\mid X_t=1) & & \\
& \ddots & \\
& & \mathcal{P}(e_t\mid X_t=S)
\end{pmatrix}
$$

La rappresentazione matriciale consente di esprimere in modo compatto le operazioni di inferenza.

---

## Classificazione dei problemi di inferenza

Dato un HMM e una sequenza di osservazioni $e_{1:t}$, i principali task di inferenza riguardano la stima degli stati nascosti.

### Filtering

Il **filtraggio** consiste nel calcolare la distribuzione a posteriori dello stato corrente

$$
\mathcal{P}(X_t \mid e_{1:t})
$$

che rappresenta la **belief state**, cioè la conoscenza dell’agente sullo stato del sistema al tempo $t$.

La procedura si realizza ricorsivamente combinando **predizione** e **aggiornamento sensoriale**.

$$
\mathcal{P}(X_{t+1} \mid e_{1:t+1})
=
\alpha
\mathcal{P}(e_{t+1} \mid X_{t+1})
\sum_{x_t}
\mathcal{P}(X_{t+1} \mid x_t)
\mathcal{P}(x_t \mid e_{1:t})
$$

In forma matriciale il messaggio forward

$$
f_{1:t} = \mathcal{P}(X_t \mid e_{1:t})
$$

viene aggiornato secondo

$$
f_{1:t+1} = \alpha \, O_{t+1} T^{\top} f_{1:t}
$$

Il filtraggio ha complessità **tempo e spazio costante** rispetto alla lunghezza della sequenza.

---

### Prediction

Il problema di **previsione** consiste nel stimare uno stato futuro dato l’evidenza osservata

$$
\mathcal{P}(X_{t+k} \mid e_{1:t})
$$

La previsione si ottiene propagando la distribuzione filtrata attraverso il modello di transizione

$$
\mathcal{P}(X_{t+k+1} \mid e_{1:t})
=
\sum_{x_{t+k}}
\mathcal{P}(X_{t+k+1} \mid x_{t+k})
\mathcal{P}(x_{t+k} \mid e_{1:t})
$$

Per un numero sufficientemente grande di passi la distribuzione tende alla **stationary distribution** della [[Markov chains|catena di Markov]].

---

### Likelihood dell’evidenza

È possibile calcolare la probabilità della sequenza osservata

$$
\mathcal{P}(e_{1:t})
$$

definendo il messaggio di verosimiglianza

$$
\ell_{1:t}(X_t) = \mathcal{P}(X_t,e_{1:t})
$$

che segue la stessa ricorsione del filtraggio.

La verosimiglianza totale è

$$
\mathcal{P}(e_{1:t}) = \sum_{x_t} \ell_{1:t}(x_t)
$$

In sequenze lunghe si verifica spesso **underflow numerico**, per cui si utilizzano normalizzazioni o rappresentazioni logaritmiche.

---

### Smoothing

Lo **smoothing** calcola la distribuzione di uno stato passato utilizzando tutta l’evidenza disponibile

$$
\mathcal{P}(X_k \mid e_{1:t}) \quad k < t
$$

Questa distribuzione può essere scomposta in due messaggi

$$
\mathcal{P}(X_k \mid e_{1:t})
=
\alpha
f_{1:k}
\times
b_{k+1:t}
$$

dove

- $f_{1:k} = \mathcal{P}(X_k \mid e_{1:k})$ è il **forward message**
- $b_{k+1:t} = \mathcal{P}(e_{k+1:t} \mid X_k)$ è il **backward message**

Il messaggio backward soddisfa la ricorsione

$$
b_{k+1:t}
=
\sum_{x_{k+1}}
\mathcal{P}(e_{k+1} \mid x_{k+1})
\mathcal{P}(x_{k+1} \mid X_k)
b_{k+2:t}
$$

L’inizializzazione è

$$
b_{t+1:t} = 1
$$

La combinazione dei due messaggi produce l’algoritmo **forward–backward**, che calcola simultaneamente tutte le distribuzioni smoothed.

---

### Fixed-Lag Smoothing

Nel contesto di inferenza online si utilizza spesso lo **smoothing a ritardo fisso**, che stima

$$
\mathcal{P}(X_{t-d} \mid e_{1:t})
$$

mantenendo un ritardo costante $d$.

Si mantengono due strutture:

- il messaggio forward $f$
- una trasformazione backward cumulativa

$$
B_{t-d+1:t} = \prod_{i=t-d+1}^{t} T O_i
$$

L’aggiornamento incrementale è

$$
B_{t-d+2:t+1}
=
O_{t-d+1}^{-1} T^{-1} B_{t-d+1:t} T O_{t+1}
$$

Questo permette di eseguire lo smoothing con **spazio costante**.

---

### Sequenza di stati più probabile

Un problema diverso dall’inferenza marginale consiste nel trovare la sequenza di stati più probabile dato l’evidenza

$$
\arg\max_{x_{1:t}} \mathcal{P}(x_{1:t} \mid e_{1:t})
$$

Definendo il messaggio

$$
m_{1:t} =
\max_{x_{1:t-1}}
\mathcal{P}(x_{1:t-1},X_t,e_{1:t})
$$

si ottiene la ricorsione

$$
m_{1:t+1}
=
\mathcal{P}(e_{t+1}\mid X_{t+1})
\max_{x_t}
\mathcal{P}(X_{t+1}\mid x_t)
m_{1:t}
$$

Questa formulazione conduce all’algoritmo **Viterbi**, che calcola la sequenza più probabile tramite **programmazione dinamica**.

---

## Interpretazione del modello

Gli HMM sono quindi **modelli generativi per sequenze temporali** in cui

- la dipendenza temporale è modellata tramite una [[Markov chains|catena di Markov]] sugli stati latenti
- le osservazioni sono generate da distribuzioni condizionate allo stato
- l’inferenza sugli stati nascosti viene realizzata tramite propagazione di messaggi forward e backward

Questa struttura costituisce uno dei casi fondamentali di inferenza in [[Modelli temporali probabilistici|modelli probabilistici temporali]] e rappresenta una specializzazione efficiente della propagazione nelle [[Bayesian network|reti bayesiane dinamiche]].