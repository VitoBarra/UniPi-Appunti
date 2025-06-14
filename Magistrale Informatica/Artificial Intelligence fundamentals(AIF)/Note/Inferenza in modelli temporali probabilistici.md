---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza in modelli temporali probabilistici
---
La **inferenza** [[Modelli temporali probabilistici | modelli temporali probabilistici]] si articola in cinque task: filtraggio, previsione, smoothing, spiegazione più probabile.
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
