---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
Course 1: "[[Machine Learning (ML)]]"
Course 2: "[[Human Language Technology (HLT)]]"
Course 3: "[[Information Retrieval (IR)]]"
tags:
  - IIA
  - HLT
  - AIF
Area: "[[Concetti generali del Machine Learning]]"
topic: "[[Text Classification]]"
SubTopic:
---
# Naive Bayes Classifier
---
Il **Naive Bayes Classifier** è un algoritmo di classificazione probabilistico basato sul [[Formula di Bayes|Teorema di Bayes]] con l'assunzione che le feature siano **indipendenti tra loro** a parità di classe. Questa assunzione è però irrealistica e quindi può performare male se le feature sono fortemente correlate. 
Nonostante questa assunzione semplificativa, il modello è efficace nel campo del [[Natural Language Processing|NLP]].

Il Naive Bayes Classifier utilizza estrazioni di feature a frequenza, come [[Bag of words]] o [[Term Frequency - Inverse document Frequency (TF-IDF)|TF-IDF]].

Nonostante il nome, il classificatore Naïve Bayes ha molte qualità utili, soprattutto nei compiti di classificazione del testo:

- **Molto veloce**, con **bassi requisiti di memoria**: Ideale per dataset di grandi dimensioni o per applicazioni in tempo reale.
- **Funziona bene anche con pochissimi dati di addestramento**: È in grado di produrre buone performance anche quando i dati sono scarsi.
- **Robusto rispetto a feature irrilevanti**: Le feature che non sono informative si compensano tra loro e **non peggiorano** significativamente le prestazioni.
- **Ottimo in domini con molte feature ugualmente importanti**: Ad esempio nei testi, dove **ogni parola può contribuire** un po’ alla classificazione. I **decision tree** in questi casi soffrono per il problema della **frammentazione** (troppe suddivisioni su dati poco rappresentativi), specie se il dataset è piccolo.
- **È ottimale se le assunzioni di indipendenza sono soddisfatte**: Se le parole (feature) sono davvero indipendenti tra loro a parità di classe, allora Naïve Bayes è **il miglior classificatore possibile secondo la teoria bayesiana**.
- **Un buon punto di partenza per la classificazione del testo**: Anche se ci sono modelli più accurati (es. SVM, Random Forest, o Transformer), Naïve Bayes è un **baseline semplice, efficace e affidabile**.


I classificatori Naive Bayes possono usare qualsiasi tipo di feature (URL, indirizzi email, dizionari, caratteristiche di rete).  
Ma se si usano solo le feature basate sulle parole, e si utilizzano tutte le parole presenti nel testo (e non un sottoinsieme), allora Naïve Bayes presenta un'importante somiglianza con i [[Probabilistic Language models|language models]].

# Definizione del classificatore Bayesiano
Per stimare la classe corretta il classificatore utilizza la funzione **argmax** per selezionare la classe che massimizza la probabilità $P(c \mid d)$, dove $c\in C$ è una delle classi discrete mentre $d$ è il documento che si vuole classificare:
$$\hat{c}=\text{argmax}_{c \in  C}P(c\mid d)$$
A questa viene applicata [[Formula di Bayes]] che permette di suddividere la probabilità condizionata $P(c \mid d)$ in tre probabilità con delle proprietà utili.

Infatti si ha : $$\hat{c}=\text{argmax}_{c \in  C} \frac {P(d \mid c)P(c)}{P(d)}$$
e dato che $P(d)$ non cambia in base alle varie classi si ottiene:
$$\hat{c}=\text{argmax}_{c \in  C}P(d \mid c)P(c)$$
In questa formula chiamiamo $P(d \mid c)$ *likelihood* del documento e $P(c)$ *prior probability*, che corrisponde alla percentuale di documenti nel training set che appartengono alla classe c.

Dato che il documento è composto da features si può riscrivere come $$\hat{c}=\text{argmax}_{c \in  C}P(f_1,\dots f_n \mid c)P(c)$$
Dato che le feature sono numerose, stimare la probabilità di ogni possibile combinazione di feature richiederebbe $O(|\mathbf{X}|^n*C)$ parametri oltre ad un training set enorme.
Perciò il classificatore bayesiano si basa su due principali assunzioni:
1. **Bag of words**: si assume che la posizione delle parole nel documento non conti e quindi si tiene semplicemente in considerazione la loro frequenza.
2. **Naive Bayes assumption**: Assume l'indipendenza delle feature a prescindere dalla classe

Per la seconda assunzione si può riscrivere la likelihood come : $P(f_{1},\dots,f_n \mid c)= P(f_{1} \mid c)*\dots*P(f_n \mid c) =\prod_{f \in F} P(f \mid c)$

Quindi si ottiene come equazione finale del classificatore:$$\hat{c}= \text{ argmax}_{c \in  C}P(c) \prod_{f \in  F}P(f \mid c)$$
#### Applicazione al testo
Per applicare il **[[Naive Bayes Classifier|classificatore Bayesiano]]** al testo si utilizza ogni parola nel documento come feature accompagnata da un index che corrisponde alla sua posizione nel documento.
$$c_{nb}=\text{argmax}_{c \in  C} P(c)\prod_{i \in  position}P(w_i \mid c)$$
dove position è il numero totale di posizioni di parole in un documento.

Però, moltiplicando molte probabilità si può avere un **floating-point underflow** e ciò si può risolvere sommando i logaritmi delle probabilità al posto di moltiplicarle tra loro.
Questo è possibile perché:
- $\log(ab)=\log(a)+\log(b)$
- il logaritmo è una funzione monotona e non cambia la selezione della classe c
- la somma è limitata tra $(-\infty, 0]$ ma non può essere infinitamente piccola
Si ha quindi: 
$$c_{nb}= \text{argmax}_{c \in  C} \left[ \log P(c)+\sum_{i \in  \text{position}}\log P(w_i \mid c) \right]$$
Mettendo il logaritmo non cambia la classificazione ed inoltre si ottiene un [[Modelli lineari con LMS|modello lineare]].

# Training
Per il training bisogna imparare le due probabilità della formula precedente:
- $P(c)$
- $P(w_i \mid c )$

Per la prima si utilizza la percentuale dei documenti nel training set che hanno classe c. Quindi, sia $N_c$ il numero di documenti di classe $c$ e $N_d$  il numero dei documenti, allora: $\hat{P}(c)=\frac{N_c}{N_d}$

Per imparare la probabilità $P(w_i \mid c)$ assumiamo che che una feature è semplicemente l'esistenza di una parola nel bag of words e quindi si calcola quante volte la parola $w_i$ appare in tutti i documenti di classe $c$. Quindi:
$$\hat{P}(w_i \mid c)=\frac{\\text{count}(w_i,c)}{\sum_{w \in  V}\text{count}(w,c)}$$
Dove $V$ è il vocabolario di tutte le parole di tutti i documenti di tutte le classi.

Se una parola nel training set non è presente in nessun documento di classe $c$ ma esiste nel vocabolario non vuol dire che non appartiene mai a quella classe. Per evitare che la probabilità condizionata sia diversa da zero per queste parole, si aggiunge il **Laplace smoothing**:
$$\hat{P}(w_i \mid c)=\frac{\text{count}(w_i,c)+1}{\sum_{w \in  V}(\text{count}(w,c)+1)}=\frac{\text{count}(w_i,c)+1}{(\sum_{w \in  V}(\text{count}(w,c)))+|V|}$$

Grazie al Laplace smoothing si possono risolvere due tipi di problemi:
1. Previene il "zero-probabilities"
2. Bilancia le parole rare e comuni

Le parole che invece si trovano nel test set ma non sono presenti nel vocabolario del training set, vengono classificate come unknown e vengono semplicemente ignorate  rimosse dal set test.

Vengono anche ignorate le *stop words*, ossia le parole molto frequenti come gli articoli. Queste devono essere prima definite e poi vengono rimosse sia dal training set che dal test set. 

```pseudo
\begin{algorithm}
\caption{Naive Bayes Classifier}
\begin{algorithmic}
\Function{Train-Naive-Bayes}{$D, C$}
    \State \textbf{returns} $\log P(c)$ and $\log P(w|c)$
    \For{each class $c \in C$} \Comment{Calculate $P(c)$ terms}
        \State $N_{doc}$ = number of documents in $D$
        \State $N_c$ = number of documents from $D$ in class $c$
        \State $logprior[c] \gets \log \frac{N_c}{N_{doc}}$
    \EndFor
    \State $V \gets$ vocabulary of $D$
    \For{each class $c \in C$}
        \State $bigdoc[c] \gets$ append($d$) for $d \in D$ with class $c$
        \For{each word $w$ in $V$} \Comment{Calculate $P(w|c)$ terms}
            \State $count(w,c) \gets$ \# of occurrences of $w$ in $bigdoc[c]$
            \State $loglikelihood[w,c] \gets \log \frac{count(w,c) + 1}{\sum_{w' \in V} (count(w',c) + 1)}$
        \EndFor
    \EndFor
    \Return $logprior$, $loglikelihood$, $V$
\EndFunction
\State
\Function{Test-Naive-Bayes}{$testdoc, logprior, loglikelihood, C, V$}
    \State \textbf{returns} best $c$
    \For{each class $c \in C$}
        \State $sum[c] \gets logprior[c]$
        \For{each position $i$ in $testdoc$}
            \State $word \gets testdoc[i]$
            \If{$word \in V$}
                \State $sum[c] \gets sum[c] + loglikelihood[word,c]$
            \EndIf
        \EndFor
    \EndFor
    \Return $\arg\max_c sum[c]$
\EndFunction
\end{algorithmic}
\end{algorithm}
```


# Multinomial Naive Bayes 
Questo è l'algoritmo per text classification usando l'algorritmo *Multinomial Naive Bayes*, che impara allenandosi su un [[Words and Corpora|corpus]]:

1. Si estrae il vocabolario, creando una lista di tutte parole uniche (tokens) che appaiono nei dati di training
2. Si calcola la probabilità a priori $P(c_j)=\frac{\text{\# doc nella classe }c_j}{\text{\# totale dei documenti}}$, ciò esprime quanto un documento appartenga alla classe $c_j$ prima di guardare alle parole
3. Calcolare la MLE (maximum likelihood estimation) $P(w_k\mid c_j)$

Poi per ogni classe $c_j$ e per ogni parola $w_k$ del vocabolario si stima quanto quest'ultima appare nella classe.
- Si uniscono tutti i documenti della classe $c_j$​ in un unico grande testo chiamato $\text{Text}_j$
- Si contano le occorrenze della parola $w_k$​ in $\text{Text}_j$​, ottenendo $n_k$​.
- Si applica lo smoothing di Laplace per evitare probabilità nulle:
  $$P(w_k​∣c_j​)=\frac{n_k+\alpha}{n+\alpha \cdot \mid \text{Vocabolario}\mid}​$$

Dove:

- $n_k$: numero di volte che la parola $w_k$ appare in $\text{Text}_j$​
- $n$: numero totale di parole in $\text{Text}_j$
- $\alpha$: parametro di smoothing (di solito 1)
- $|\text{Vocabolario}|$: numero di parole uniche nel vocabolario

> Questo è importante perché il modello calcola la probabilità di un documento **moltiplicando** le probabilità delle singole parole

Una volta calcolate tutte le probabilità $P(c_j)$ e $P(w_k \mid c_j)$, per classificare un nuovo documento:

$$\text{Classe}(d) = \arg\max_{c_j} \left[ P(c_j) \times \prod_{w_k \in d} P(w_k \mid c_j) \right]$$Se nel documento di test appaiono parole non viste nel training si può:
- **ignorarle** completamente.
- Non vengono incluse nel calcolo delle probabilità.
- Non forniscono alcuna informazione utile; il fatto che una classe abbia più OOV non cambia nulla.​

Alcuni sistemi rimuovono le **stop words**: parole molto frequenti e poco informative come “il”, “di”, “a”.
Si può ordinare il vocabolario in base alla frequenza e creare una lista delle prime 10 o 50 parole da eliminare.
Tuttavia, **rimuovere le stop words non migliora quasi mai le prestazioni**.
In pratica, i modelli Naïve Bayes funzionano **meglio usando tutte le parole**, senza escludere stop words

## Ottimizzazione per sentimental Analysis
Per migliorare le performance per la [[Sentimental analysis]] si può usare una variante chiamata : ***Binary Multimodal Naive Bayes***, che usa lo stesso algoritmo mostrato prima con la sola eccezione che per ogni documento si rimuovono i tutte le parole duplicate prima di concatenare i documenti della solita classe e poi si rimuovono anche le parole duplicate nel test set. Dopo di che si applica la stessa equazione: 
$$C_{NB}=argmax_{c_j \in  C}P(c_j) \prod_{i \in  \text{positions}}P(w_i\mid c_j)$$


Uno dei problemi nella classificazione per la sentiment analysis sono le negazioni. Per sistemarle si fa text normalization e la parola negata vine modificata in una nuova parola con la negazione davanti. (esempio: didn't like -> not_like)

In altri scenari, in cui non si hanno abbastanza data etichettati si usano i [[Affect Lexicon]], liste di termini pre-annotati. Un modo per utilizzarli è aggiungere una feature dove appare il termine.


# Evaluation Measures
Nel contesto della classificazione binaria o multiclasse, **l'accuratezza** non è sempre una metrica affidabile, soprattutto quando le classi sono sbilanciate. Un classificatore potrebbe ottenere un'accuratezza molto alta semplicemente prevedendo sempre la classe più frequente, senza realmente svolgere un buon lavoro nel riconoscere i casi rilevanti. Per questo motivo, si preferisce usare **precisione** e **recall**, che si concentrano sulla qualità delle previsioni positive.

- **Precisione** indica la percentuale delle previsioni positive che sono effettivamente corrette.

- **Recall** misura la percentuale degli elementi rilevanti che sono stati effettivamente identificati dal sistema.

Per avere una valutazione complessiva che tenga conto di entrambe, si utilizza spesso la **F1-score**, che è la media armonica tra precisione e recall. Questo è particolarmente utile quando vogliamo bilanciare l'importanza di evitare falsi positivi e falsi negativi.

Quando il problema coinvolge più di due classi, le metriche possono essere aggregate in due modi principali:

- **Macroaveraging**: calcola precisione e recall per ciascuna classe, e poi fa la media. È utile quando tutte le classi hanno la stessa importanza.

- **Microaveraging**: aggrega tutte le decisioni in un’unica matrice di confusione e calcola precisione e recall globali. È più influenzato dalle classi più frequenti.

Infine, quando si confrontano due classificatori, le differenze di performance osservate su un singolo test set potrebbero essere casuali. Per valutare se una differenza è statisticamente significativa, si usano test di ipotesi. L’ipotesi nulla (H₀) afferma che non c’è differenza significativa tra i modelli; se possiamo rigettarla con sufficiente confidenza, allora possiamo concludere che uno dei due è effettivamente migliore.

# Avoiding Harms in classification
La letteratura ha dimostrato che i classificatori automatici possono **propagare stereotipi negativi e bias** presenti nei dati e nei modelli stessi. Uno studio di Kiritchenko e Mohammad (2018) ha rilevato che molti classificatori di sentiment tendono ad associare **valori di sentiment più bassi e emozioni più negative** alle frasi che contengono **nomi afroamericani**.

Anche i classificatori di tossicità (utilizzati, ad esempio, per rilevare linguaggio d’odio, abusi o molestie) possono comportarsi in modo problematico: **segnalano erroneamente come tossiche** frasi che non lo sono, solo perché contengono riferimenti a identità come persone cieche, donne o persone LGBTQ+.

Questi problemi possono avere diverse cause:

- **Bias nei dati di addestramento**: è noto che i sistemi di machine learning tendono ad amplificare i pregiudizi già presenti nei dati su cui sono stati allenati.

- **Errori o distorsioni nei dati etichettati**: le etichette umane usate per supervisionare il modello possono essere influenzate da pregiudizi.

- **Problemi nelle risorse utilizzate**, come i dizionari lessicali o le liste di parole associate a emozioni o tossicità.

- **Limiti nell’architettura del modello**, ad esempio per via di ciò che il modello viene addestrato a ottimizzare (es. massimizzare la classificazione corretta senza attenzione all’equità).


La **mitigazione di questi danni** è un tema ancora **aperto nella ricerca**, con molte sfide da affrontare per rendere i modelli più equi e inclusivi.