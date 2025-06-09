---
Course: "[[Information Retrieval (IR)]]"
tags:
  - IR
Area: "[[Information Retrieval - Concetti generali]]"
topic: 
SubTopic:
---
# Retrieval models
---
Un ***retrieval model*** è un metodo utilizzato in un [[Information Retrieval - Concetti generali|sistema di IR]] per recuperare i documenti. 
Un modello definisce come il sistema recupera e classifica (ranking) i documenti in base alla query di un utente.
Un modello di recupero $R$ formalizza uno specifico ***principio di Ranking***.

![[Retrieval models.png]]

Sia $D$ un insieme di documenti e $Q$ un insieme di query. 
Allora un **retrieval model** $R$ per $D,Q$ è una tupla $\langle \mathbf{D},\mathbf{Q},\rho\rangle$ , dove:
- $\mathbf{D}$ è l'insieme delle rappresentazioni dei documenti $D$, e quindi $\mathbf{d}\in\mathbf{D}$ rappresenta $d\in D$
- $\mathbf{Q}$ è l'insieme delle rappresentazioni dei documenti $Q$, e quindi $\mathbf{q}\in\mathbf{Q}$ rappresenta $q\in Q$
- $\rho$ è la funzione di rilevanza utilizzata dal modello per correlare la query ad un documento. La si definisce come: $$\rho:\mathbf{Q}\times \mathbf{D}\to \mathbb{R}$$
Quindi, dati una query $q \in Q$ e un documento $d \in D$ il modello usa le loro rappresentazioni $\mathbf{q}\in\mathbf{Q}$ e $\mathbf{d \in \mathbf{D}}$ per calcolare la loro rilevanza attraverso la funzione $\rho(\mathbf{q},\mathbf{d})$.
Il risultato prodotto da $\rho$ lo chiamiamo **Relevance Score**.


### Probability Ranking Principle (PRP)

Se i documenti recuperati vengono ordinati in base alla probabilità decrescente di rilevanza sui dati disponibili, allora l'efficacia del sistema è la migliore che si possa ottenere per i dati.

Questo principio è valido sotto le seguenti assunzioni:
- La rilevanza $\mathrm{rel}(d,q)$ è una proprietà di un documento $d$ date le richieste di informazioni da una query $q$, senza riferimenti ad altri documenti 
- La rilevanza è binaria : $\mathrm{rel}(d,q) \in \{0,1\}$
- La rilevanza è unica per l'utente che fornisce la query $q$

Se seguiamo questo principio possiamo massimizzare molte unzioni obiettivo come:
- La recall attesa
- la precision attesa
- l'utilità attesa


### Tipi di modelli
Tra i vari tipi di modelli di recupero dele informazioni abbiamo:
- [[Boolean models|Modelli booleani]]
- [[Probabilistic models|Modelli probabilistici]] : [[Best Matching 25 (BM25)|BM25]]
- [[Natural language models|Modelli basati sul linguaggio naturale]] : [[Bag of words]], [[Term Frequency - Inverse document Frequency (TF-IDF)|TF-IDF]]