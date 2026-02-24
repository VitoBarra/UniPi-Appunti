---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
Corse 1: "[[Generative Deep Learning (GDL)]]"
tags:
  - AIF
  - GDL
Area:
topic:
SubTopic:
---

# Bayesian network
---
i **Bayesian network** è un modo rappresentare una [[Full Joint Distribution (FJD)|full joint distribution]] in [[Modelli Probabilistici|domini incerti]] in modo piu compatto sfruttando l [[Indipendenza condizionata|indipendenza condizionale]].
Un **Bayesian network** è un [[Directed Acyclic Graph (DAG)|grafo diretto aciclico]] (DAG) in cui:
- ogni nodo rappresenta una [[Variabili Aleatorie (Casuali)|variabile casuale]], discreta o continua;
- le frecce indicano relazioni di influenza diretta, dove il nodo di partenza è il **genitore** di quello di arrivo;
- ogni nodo $X_i$ è associato una **conditional probability tables (CPTs)**, una tabella che indica la distribuzione di **[[Probabilita condizionata|probabilità condizionata]] locali** $\theta(X_i \mid Parents(X_i))$, che quantifica l'effetto dei genitori sul nodo $X_i$ ogni riga devo sommare ad $1$ e in caso di [[Variabili Aleatorie Notevoli - Bernulli|variabili boolenare]] si indica solo caso $True$ in quanto il caso $False$ si può ottenere come $1-p$, Per variabili booleane con $k$ genitori booleani, sono necessarie $2^k$ probabilità indipendenti. Un nodo senza genitori ha una sola riga che rappresenta le probabilità a priori della variabile.
![[IMG - Bayesian network esempio.png]]
La topologia della rete determina le relazioni di [[Indipendenza condizionata|indipendenza condizionale]] tra le variabili indicate dal fatto che non esiste un collegamento tra le due variabile [[Indipendenza condizionata|condizionalmente indipendenti]], riducendo significativamente il numero di [[Definizione di Probabilita|probabilità]] da specificare rispetto alla [[Full Joint Distribution (FJD)|Full joint Distribution]]. 

le **Bayesian Network** definisce la sua **semantica globale** come la [[Full Joint Distribution (FJD)|distribuzione congiunta]] sulle variabili $X_1, \dots, X_n$ come riscritta come:$$
P(x_1, \dots, x_n) = \prod_{i=1}^n \theta(x_i \mid Parents(X_i))
$$Si può dimostrare che le **probabilità locali** $\theta(x_i \mid Parents(X_i))$ corrispondono esattamente alle probabilità condizionate $P(x_i \mid Parents(X_i))$ derivate dalla distribuzione congiunta. Infatti vale:$$
P(x_i \mid Parents(X_i)) \equiv 
\frac{P(x_i, Parents(X_i))}{P(Parents(X_i))} =
\frac{\sum_{\mathbf{y}} P(x_i, Parents(X_i), \mathbf{y})}
{\sum_{x_i', \mathbf{y}} P(x_i', Parents(X_i), \mathbf{y})}
$$ e la dimostrazione segue usando la [[Inferenza con Full Joint distribution|marginalizazione]]


La **semantica locale** di una **rete bayesiana** si definisce attraverso specifiche proprietà di indipendenza condizionale legate alla struttura del grafo. La prima di queste proprietà è quella dei non-discendenti, secondo la quale ogni variabile  è condizionatamente indipendente dai propri non-discendenti, dato l'insieme dei suoi genitori $Parents(X_i)$. In forma schematica: $$\mathcal{P}(X_i \mid  Parents(X_i), NonDescendants(X_i)) = \mathcal{P}(X_i \mid  Parents(X_i))$$dove per $NonDescendants$ si intendono tutti i nodi che non sono **figli diretti o indiretti** del nodo $X_i$. Questa proprietà e il fatto che $\theta(X_i \mid Parents(X_i))= P(X_i \mid Parents(X_i))$, sono sufficienti sufficiente a ricostruire [[Distribuzione di probabilita congiunta totale|la distribuzione congiunta]] come: $$P(X_1, \dots, X_n) = \prod_i P(X_i \mid Parents(X_i))$$Un'altra proprietà è data dalla **Markov blanket** che garantisce che ogni variabile sia [[Indipendenza condizionata|condizionatamente indipendente]] da tutte le altre [[Variabili Aleatorie (Casuali)|variabili]] della rete$$\mathcal{P}(X_i \mid MarkovBlanket(X_i) ,Rest(X_i)) =\mathcal{P}(X_i \mid MarkovBlanket(X_i))  $$dove la $MarkovBlanket(X_i)$ sono tutti **i genitori, i figli e i padri dei figli** della variabile $X_i$ 

visivamente a sinistra la **non-descendent** e a destra la **markov blanket**.
![[IMG - Bayesian network indipendence dai non-descendants e markov blanket.png]]


i **Bayesian network** fornisce una rappresentazione completa e **non ridondante** della [[Distribuzione di probabilita congiunta totale|full joint distrubuion]], ma può essere anche molto più compatto rispetto alla distribuzione congiunta completa. Questa proprietà rende possibile gestire domini con molte variabili. La compattezza è una caratteristica dei sistemi **localmente strutturati** (o **sparsi**), in cui ogni sotto-componente interagisce direttamente con un numero limitato di altri componenti, indipendentemente dal numero totale. In tali sistemi, la complessità cresce linearmente piuttosto che esponenzialmente,  infatti nel caso delle reti bayesiane, si assume spesso che ogni variabile casuale sia influenzata direttamente da al massimo $k$ altre variabili. Per $n$ variabili booleane, ogni tabella di probabilità condizionata richiede al massimo $2^k$ numeri, quindi la rete completa può essere specificata con $2^k \cdot n$ numeri, rispetto ai $2^n$ numeri della distribuzione congiunta completa. La scelta dell'**ordinamento dei nodi** influisce notevolmente sulla compattezza: un ordine causale, dove le cause precedono gli effetti, riduce il numero di collegamenti e la complessità delle CPT.

Anche se il numero massimo di genitori $k$ è contenuto, compilare le CPT può richiedere fino a $O(2^k)$ numeri, ma spesso le relazioni tra genitori e figlio seguono pattern standard (**distribuzioni canoniche**), che riducono drasticamente la complessità. Tra questi pattern ci sono:

- **Nodi deterministici**: il valore del nodo è determinato esattamente dai genitori, ad esempio tramite una funzione logica o numerica.
- **Indipendenza contestuale** (**CSI, Context-Specific Independence**): un nodo può essere indipendente da alcuni genitori dati valori specifici di altri genitori.
- **Relazioni logiche rumorose** (**noisy-OR**): generalizzazione della disgiunzione logica che permette di modellare l'incertezza dell'efficacia causale dei genitori. La probabilità condizionata si calcola come:$$
P(x_i | Parents(X_i)) = 1 - \prod_{j : X_j = true} q_j
$$dove $q_j$ è la probabilità di inibizione del genitore $X_j$. usarli permette di ridurre drasticamente il numer odi numeri necessari a rappresentare la [[Full Joint Distribution (FJD)|full joint distrubution]]








