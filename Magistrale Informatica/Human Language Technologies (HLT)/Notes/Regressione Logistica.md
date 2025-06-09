---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Regressione Logistica
La **regressione logistica** è un modello [[Classificatore Generativo e Discriminativo|discriminativo]] ampiamente utilizzato per compiti di classificazione binaria.

Nel [[Natural Language Processing|NLP]] è l'[[Algoritmi di Machine Learning]] di base per la classificazione, anche base delle reti neurali. È un algoritmo particolarmente adatto a scoprire la relazione tra caratteristiche o indizi e un determinato risultato.

La regressione logistica è un esempio di **classificatore discriminativo**, poiché si concentra direttamente sulla modellazione della probabilità condizionata $P(y|x)$, ovvero della classe dato l’input. 
Questo si contrappone ai **modelli generativi**, come [[Naive Bayes Classifier]], che cercano invece di modellare congiuntamente $P(x, y)$ o separatamente $P(x|y)$ e $P(y)$.

# Classificazione binaria - regressione logistica
Dato un insieme di coppie input/output $(x^{(i)}, y^{(i)})$, per ogni osservazione $x^{(i)}$,  si rappresenta $x^{(i)}$ tramite un vettore di caratteristiche (feature) $[x_1,x_2,\dots,x_n]$ e si calcola un output, ossia una classe predetta $\hat{y}^{(i)} \in \{0, 1\}$.  
La regressione logistica risolve questo compito imparando, da un insieme di addestramento, un vettore di pesi e un termine di bias (intercetta).

Nel contesto della regressione logistica, per ogni caratteristica $x_i$​, il peso $w_i$ indica quanto è importante quella caratteristica:

- $x_i$ =“la recensione contiene ‘awesome’”: $w_i = +10$
- $x_j$ = “la recensione contiene ‘abysmal’”: $w_j = -10$
- $x_k$ = “la recensione contiene ‘mediocre’”: $w_k = -2$

L’obiettivo della regressione logistica binaria è addestrare un classificatore capace di prendere una decisione binaria sulla classe di una nuova osservazione in input.  
Nel caso di una singola osservazione $x$, rappresentata come un vettore di caratteristiche $[x_1, x_2, ..., x_n]$, il classificatore può restituire $y=1$ oppure $y=0$ (oppure $\hat{y} \in \{0, 1, 2, 3, 4\}$ nel caso di regressione logistica multinomiale).

Per capire se un input $X$ appartiene ad una classe si fa la somma pesata $z=\left( \sum_{i=1}^n w_ix_i\right)+b$. Se questa è alta allora $\hat{y}=1$ altrimenti $\hat{y}=0$.
Per formalizzare somma alta o bassa si usano delle funzione di attivazione, come ad esempio la [[Funzione di attivazione - Sigmoide]].
![[Pasted image 20250603130931.png]]
Quindi si calcola $z$ e poi si passa dentro la sigmoide.

# Learning
La regressione logistica è un esempio di [[Algoritmi di learning supervisionato|classificazione supervisionata]]. Nella classificazione supervisionata conosciamo l’etichetta corretta $y$ (0 o 1) per ogni input $x$. 
Il sistema produce è una stima, $\hat{y}$​. 
Si vogliono impostare $W$ e $b$, pesi e bias, in modo da minimizzare la distanza tra la stima $\hat{y}^{(i)}$ e il vero valore $y^{(i)}$. 
Si ha bisogno di:
- uno stimatore: una **funzione di loss** :  si usa la [[Cross Entropy]]
- un **algoritmo di ottimizzazione** per aggiornare $W$ e $b$ al fine di minimizzare la loss : si usa l'algoritmo [[Tecnica di ottimizzazione Gradient Descent|stochastic gradient descent]]

# Multinomial regression
Nella **regressione logistica**, detta *softmax regression*, si vuole classificare ogni osservazione con una classe $k$ tra un insieme di $K$ classi, con la condizione che solo una di queste classi sia corretta.
Spesso si ha bisogno di più di due classi e se ci sono più di 2 classi, si usa la **regressione logistica multinomiale**.

Per esempio:
- Positivo / negativo / neutro  
- Parti del discorso (nome, verbo, aggettivo, preposizione, …)  
- Classificare SMS di emergenza in diverse classi di azione possibili

La somma delle probabilità deve comunque essere pari a 1:  
$P(\text{positivo}\mid \text{documento})+P(\text{negativo}\mid \text{documento})+P(\text{neutro}\mid \text{documento})=1$
