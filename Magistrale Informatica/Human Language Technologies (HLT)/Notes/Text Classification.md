---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Text Classification
---
La classificazione di testo (aka Text Classification) è uno dei task del [[Natural Language Processing|NLP]] che si occupa di decidere la classe di una parola, frase o di un intero testo o documento.

L'obiettivo della classificazione è quello di analizzare i dati, estrarne le caratteristiche rilevanti e assegnarli a una delle classi discrete predefinite.


> [!NOTE] Task
> Input :
> 	documento $d$
> 	un set fissato di classi : $C=\{c_1,c_2,\dots, c_n\}$
> Output:
> 	predizione della classe $c \in C$ per il documento $d$


Il modo più comune per la classificazione di testo è attraverso tecniche di [[Algoritmi di learning supervisionato|machine learning supervisionato]]. 

Questi vengono utilizzati per la creazione di classificatori probabilistici, ossia che restituiscono la probabilità di un dato osservato di essere in una determinata classe.
Si possono distinguere in:

- *Generativi*, come il [[Naive Bayes Classifier]], apprendono la probabilità congiunta $P(x, y)$ e usano la regola di Bayes per calcolare $P(y|x)$. Costruiscono un modello in base a come hanno appreso su come vengono generati i dati in funzione della classe
- *Discriminativi*, come la [[Regressione Logistica]] o le [[Support Vector Machine (SVM)|SVM]], che apprendono direttamente $P(y|x)$ o una funzione che discrimina tra le classi. Invece di imparare feature dall'input viene usata per discriminare tra le possibili classi. Sono quelli più usati.



## Componenti di un classificatore probabilistico
Data una coppia input/label $(\mathbf{x}^{(i)},\mathbf{y}^{(i)})$ un classificatore è formato da:
- La rappresentazione delle feature dell'input : $\mathbf{x}^{(i)}=[x_1,\dots,x_n]$
- Una funzione di classificazione, come la [[Funzione di attivazione - Sigmoide|Sigmoide]] o la [[Funzione di attivazione - SoftMax|SoftMax]], che calcola $\mathbf{y}$, ossia la classe stimata attraverso $p(y|x)$
- Una funzione obiettivo per il learning, come la [[Cross Entropy]]
- Un algoritmo di ottimizzazione, come il [[Tecnica di ottimizzazione Gradient Descent|Gradient Descent]]

### Applicazioni
Con questo task si possono svolgere task come la [[Sentimental analysis]], lo spam detection, l'attribuzione dei crediti d'autore o etichettare l'argomento di un documento dato il suo contenuto.

## Language model come classificatore
Anche un [[Probabilistic Language models|language model]] può essere visto come task di classificazione in cui ogni parola del vocabolario rappresenta una classe e il task di predizione può essere inteso come classificazione del costo contesto nella nuova parola.



