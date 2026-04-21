---
Course: "[[Information Retrieval (IR)]]"
tags:
  - IR
Area: 
topic: 
SubTopic:
---
# Bag of words
---
**Bag of Words** è una rappresentazione vettoriale discreta che modella un documento come una collezione non ordinata di parole, trasformando un oggetto testuale in una struttura numerica basata esclusivamente sulle frequenze.

Dato un vocabolario $\mathcal{V} = \{w_1, \dots, w_N\}$ e un insieme di documenti $\{d_1, \dots, d_M\}$, Bag of Words rappresenta ogni documento $d_i$ tramite un vettore di conteggi $$x_i = (x_{1i}, \dots, x_{Ni}) \in \mathbb{N}^N$$ dove $$x_{ji} = n(w_j, d_i)$$ è il numero di occorrenze della parola $w_j$ nel documento $d_i$ 

L’intero dataset è quindi rappresentato come una matrice termine-documento $$X \in \mathbb{N}^{N \times M}$$ in cui ogni colonna corrisponde a un documento e ogni riga a una parola del vocabolario.

Dal punto di vista probabilistico, **Bag of Words** induce una rappresentazione multinomiale dei documenti. Se $n_i = \sum_{j=1}^N x_{ji}$ è la lunghezza del documento $d_i$, si assume che $$x_i \sim \text{Multinomial}(n_i, \theta)$$ dove $\theta = (\theta_1, \dots, \theta_N)$ è un vettore di probabilità tale che $\sum_{j=1}^N \theta_j = 1$ e $\theta_j = P(w_j)$.

La probabilità del documento è quindi $$P(x_i|\theta) = \frac{n_i!}{\prod_{j=1}^N x_{ji}!} \prod_{j=1}^N \theta_j^{x_{ji}}$$ che riflette un processo generativo in cui ogni parola è estratta indipendentemente secondo la stessa distribuzione $\theta$.

Questa formulazione evidenzia l’assunzione fondamentale del modello: indipendenza condizionata tra le parole, cioè $$P(w_{j_1}, \dots, w_{j_{n_i}}|\theta) = \prod_{t=1}^{n_i} P(w_{j_t}|\theta)$$ che giustifica la perdita completa dell’ordine sequenziale.

Dal punto di vista strutturale:
- lo spazio è ad alta dimensionalità ($N$ grande)
- i vettori sono sparsi: $x_{ji} = 0$ per la maggior parte delle parole
- la rappresentazione è invariante rispetto a permutazioni delle parole

Bag of Words costituisce la base per modelli generativi discreti come [[Naive Bayes Classifier|Naive Bayes]], dove si introduce una variabile latente di classe $C$ e si assume $$P(x|C=c) = \prod_{j=1}^N P(w_j|c)^{x_j}$$, e per modelli latenti come [[Latent Dirichlet Allocation (LDA) 1|LDA]], in cui il vettore osservato $x_i$ è generato da una miscela di distribuzioni multinomiali associate a variabili latenti di tipo topic.