---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Evaluation Language Models
---
I modelli [[N-Grams Language Models|n-grams]] si possono valutare in due modi principali:
- valutazione estrinseca e intrinseca (perplexity)

### **Valutazione estrinseca (in-vivo)**

È l’unico modo per capire davvero se un miglioramento nel modello linguistico (o in un suo componente) porta benefici nel compito finale.

**Come confrontare due modelli, A e B:**

1. Inserisci ciascun modello in un compito reale (es. traduzione automatica, riconoscimento vocale, ecc.).
2. Esegui il compito e ottieni un punteggio per A e per B (es. numero di parole tradotte o trascritte correttamente).
3. Confronta l’accuratezza dei due modelli.

Tuttavia, questo tipo di valutazione è costoso, richiede tempo e non sempre si generalizza bene ad altri compiti o applicazioni

### **Valutazione intrinseca (perplessità)**

Misura la qualità del modello indipendentemente da una specifica applicazione.

**Vantaggi della perplessità:**

- Permette la back propagation (utile durante l’addestramento).
- Ha una chiara interpretazione semantica utile per l’elaborazione del linguaggio.
- Valuta direttamente la capacità del modello di **prevedere parole**.
- Non corrisponde sempre alla performance in applicazioni reali (un buon modello statistico non basta da solo).
- Fornisce un **indicatore unico e generale** per confrontare modelli linguistici.
- È utile sia per gli  [[N-Grams Language Models]] sia per [[Large Language Models (LLM)]].

Se si sta costruendo un modello per un compito specifico, il **set di test** deve riflettere il linguaggio di quel compito.
Se si vuole un modello generico, servirà una grande varietà di dati da domini diversi.
Non si devono includere frasi del **test set** nel training set altrimenti il modello assegnerà a quelle frasi probabilità troppo alte durante il test, falsando i risultati.
È importante usare il test set solo una volta. Se lo usiamo più volte, rischiamo di adattare inconsciamente il modello alle sue caratteristiche.
Per questo motivo, è fondamentale avere anche un **terzo set**, chiamato **validation set**, da usare durante lo sviluppo per test intermedi, lasciando il **test set finale** intatto per la valutazione conclusiva.


# Perplexity

La **perplessità** misura quanto è buono un [[Probabilistic Language models|modello linguistico]]. È definita come **l’inverso della probabilità** assegnata dal modello al set di test, **normalizzato per il numero di parole (o token)**.

**Intuizione di base:**

Un buon modello linguistico dovrebbe preferire frasi "reali", cioè simili a quelle che compaiono spesso nel linguaggio naturale.

- Frasi comuni o osservate frequentemente nel corpus ottengono probabilità **più alte**.
- Frasi rare o improbabili ottengono probabilità **più basse**.

Un buon modello è quello che assegna **probabilità più alta alla parola successiva effettivamente osservata**, e in generale a **tutte le parole del test set**.

Per confrontare due modelli linguistici, A e B:

- Si calcolano le probabilità assegnate da ciascun modello all’intero test set:  
    **Pₐ(test set)** e **Pᵦ(test set)**
- Il modello migliore è quello che assegna **una probabilità più alta**, cioè quello che è **meno sorpreso** dal testo di test.

La probabilità di un intero testo **diminuisce** all’aumentare della lunghezza del testo (più parole = più moltiplicazioni tra probabilità < 1).  
Per questo non è utile confrontare semplicemente le probabilità totali: serve una metrica **per parola**.

La **perplessità** è:

- L’**inverso della probabilità totale del test set**
- **Normalizzata** per il numero totale di parole

In formula:

$$\begin{array}
 & PP(W) = P(w_1,\dots,w_n)^{-\frac{1}{N}} = N\sqrt{\frac{1}{P(w_1,\dots,w_N)}} \\
 \text{chain rule} \rightarrow PP(W)=N\sqrt{\prod_{i=1}^N \frac{1}{P(w_i\mid w_1,\dots,w_{i-1})}} \\
\text{bigram} \rightarrow PP(W)=N\sqrt{\prod_{i=1}^N\frac{1}{P(w_i\mid w_{i-1})}}
\end{array}$$

Dove $N$ è il numero di parole nel test set.

Il **fattore di diramazione** (branching factor) rappresenta il **numero di possibili parole successive** che possono seguire una certa parola.  
Quindi, **più bassa è la perplessità** di un modello su un certo insieme di dati, **migliore** è il modello linguistico.

**Minimizzare la perplessità** equivale a **massimizzare la probabilità** del set di test secondo il modello.  
L’**inverso della probabilità** compare nella definizione originale di perplessità, derivata dalla **cross-entropia** nella teoria dell’informazione.  
La perplessità è **inversamente proporzionale alla probabilità**:
- **Intervallo di valori della probabilità**: $[0, 1]$
- **Intervallo di valori della perplessità**: $[1, ∞]$


#### Esempio
Consideriamo un linguaggio deterministico:  
**L = {red, blue, green}**  
→ ogni parola può essere seguita da "red", "blue" o "green"  
→ **fattore di diramazione = 3**

**Modello A:**

Tutte le parole hanno la stessa probabilità di seguire un’altra:  
$P(x|y) = 1/3$

Test set: **T = "red red red red blue"**

$$\text{Perplessità}_A(T) = P_A(\text{red red red red blue})^{-1/5} = \left(\left(\frac{1}{3}\right)^5\right)^{-1/5} = 3$$

**Modello B:**

Addestrato su un corpus dove "red" è molto frequente:

- **P(red) = 0.8**
- **P(blue) = P(green) = 0.1**

$$\text{Perplessità}_B(T) = (0.8 \cdot 0.8 \cdot 0.8 \cdot 0.8 \cdot 0.1)^{-1/5} \approx 1.89$$

→ Il modello B assegna **una probabilità maggiore** alla frase di test → quindi la **perplessità è minore** → modello migliore.

### **Perplessità, entropia e qualità del modello**

La perplessità fornisce un’idea della **complessità dello spazio linguistico**: in questo senso è collegata al concetto di **entropia**, che è una misura dell’informazione.

Un modello linguistico con **bassa perplessità** è meno "sorpreso" dai dati e fa **previsioni più sicure**.    
Tuttavia, **un miglioramento nella perplessità (valutazione intrinseca)** **non garantisce** un miglioramento in compiti reali come la traduzione o il riconoscimento vocale (**valutazione estrinseca**).

Nonostante ciò, la perplessità è spesso usata come metrica pratica, poiché **di solito è correlata** a miglioramenti nelle applicazioni.


$$H(X)=-\sum_{x \in X}p(x)\log_2 p(x)$$
Un modo intuitivo di vedere l'entropia è come il limite inferiore del numero dei bit per rappresentare una determinata decisione o un pezzo di informazione in maniera ottimale.