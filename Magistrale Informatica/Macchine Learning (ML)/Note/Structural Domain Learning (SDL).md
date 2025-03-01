---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Structural Domain Learning (SDL)
---
__Structural Domain Learning__ (__SDL__) è un campo del [[Machine Learning (ML)|Machine Learning]] che si occupa di studiare [[Modelli di Machine Learning|modelli]] per il macchine learning che siano in grado di ricevere in input una __dato strutturato__ come ad esempio un [[Struttura dati - Alberi|albero]] o un [[Struttura dati - Grafi|grafo]] 

l approccio opposto sarebbe quello di trasformare questa struttura in un [[Vettori|vettore]] per essere usata dai modelli  che prendono dati flat come al esempio le [[Reti neurali Feed-Forward (FF)|FF]] o le [[Reti Neurali Convoluzionali (CNN)|CNN]] o in una __sequenza__ per essere usata da una [[Reti Neurali Ricorrenti (RNN)|RNN]].



I dati reali spesso non sono semplici vettori ma strutture complesse con relazioni intrinseche. I grafi sono una rappresentazione naturale per molteplici domini, tra cui:
- **Visione artificiale**: reti per la comprensione delle scene
- **Trasporti**: modelli predittivi del traffico
- **Social network**: modellazione delle interazioni tra utenti
- **Chimica**: rappresentazione di molecole per il drug design
- **Biologia**: reti proteiche e analisi del cervello
- **Linguistica**: parsing e knowledge graphs
Questi dati possono essere modellati con **reti neurali profonde (DGN - Deep Graph Networks)**, che generalizzano i modelli classici di deep learning ai grafi.
![[IMG - Esempio uso grafi.png]]

### Trasduttura
L __obiettivo__ del __SDL__ è imparare un __trasduttore__ che trasforma una dato strutturato sono del tipo
- __Structure-to-Structure__: trasformazione da una struttura in un altra ovvero input-output isomorfi (eg. classificazizone di noti) 
- __Structure-to-Scalar/element__: trasformazione di una struttura in uno scalare o in una sequenza o altri output non isomorfi (regressione e classificazione)
- __edge-base-task__: problemi di predizione di connessioni.
 ![[IMG - task in SDL.png]]

## Rappresentazione dei grafi e apprendimento strutturato

Un nodo in un grafo è descritto da un vettore di caratteristiche . Gli archi tra i nodi hanno etichette che possono rappresentare distanze, connessioni logiche o altre proprietà.

L’apprendimento strutturato può essere visto come il problema di mappare i dati strutturati in uno spazio continuo: Dove è una funzione che trasforma la struttura in una rappresentazione utilizzabile per regressione o classificazione.


- [[Rappresentazione simbolica e distribuita dei concetti|learning di rapresentzione ]]

## Deep Graph Networks (DGN) framework

L’idea centrale dei DGN è il **Message Passing**, un processo iterativo che permette ai nodi di aggiornare il proprio stato in base alle informazioni ricevute dai vicini.
 Passaggi fondamentali:
1. Ogni __nodo__ calcola un __messaggio__ come funzione della sua __label__, dei suoi vicini $\mathcal{N}_v$ e delle sua connessioni, manda il messaggio a tutti i suoi vicini.
2. I __nodi__ che ricevano i messaggi li aggregano con una funzione __invariante alla permutazione__ ovvero non cambia con l ordine di arrivo dei messaggi.
3. Il nodo aggiorna il proprio __stato__ combinando i messaggi con pesi liberi $W$

L’iterazione del processo di Message Passing permette di diffondere l’informazione tra tutti i nodi del grafo.
![[IMG - Message passing On SDL.png]]

Lo stato non dipende solo dal vicinato locale $\mathcal{N}_v$: le iterazioni di questo meccanismo MP permettono la diffusione delle informazioni tra tutti i nodi, raggiungendo tutti gli altri.  

Infine, è possibile emettere un output __per ciascun nodo__ o __per l'intero grafo__ attraverso un'aggregazione invariante alla permutazione delle rappresentazioni dei nodi, nota anche come __global pooling__

Piu formalmente abbiamo che:
$$\mathbf{h}_v^{(l)}= AGG_{\mathbf{W}^{(l)}}(L_vh_u^{(l-1)},\{h_u^(l-1): u \in  \mathcal{N}(v)\}) \ \ l= 1,\dots L$$dove:
- $AGG_{\mathbf{W}^{(l)}}$  aggrega (propaga) i __messaggi__ dai nodi vicini, includendo un operatore invariante per permutazione sull'insieme dei vicini (ad esempio, una somma) e combinazioni delle attivazioni delle unità della rete neurale in $h$, dove $\mathbf{W}$ sono i parametri liberi del modello. 
- $L_v$ rappresentano le etichette dei nodi.  
- $\mathcal{N}$ è definito in base alla matrice di adiacenza $A$ del grafo.

- Applicare questo calcolo a ciascun nodo del grafo corrisponde a una visita parallela e non ordinata del grafo a ogni iterazione $l$.
Abbiamo una grande flessibilità nell'implementazione di questi operatori, con molte variazioni di modello disponibili.
- $\mathbf{h}^{(l)}=relu(\hat{A}h^{l-1}W^{(l)})\hat{A}$ (CG)
- $\mathbf{h}^{(l)}=f(W^{(l)}_1h^{l-1}+W^{(l)})Ah^{l-1}$






### Graph Convolutional network  (GCN) 
un modo per allenare reti neurali per grafi è costruire iterativamente una rete sfruttando il meccanismo di passaggio di messaggi.
arche

l algoritmo graph 4 neural network ad ogni iterazione si aggiunge un layer è il campo recettivo è incrementalmente esteso in funzione della profondità.
![[IMG - GCN radius.png]]
e calcola una singola variabile di stato per ogni layer e per ogni layer che vengono poi  combinate in un neurone di output. 
![[IMG - GCN Percettiva Radius.png]]
Formalmente può essere descritto da 

$$
\mathbf{h}_v^{(l)} = 
\begin{cases}  

\displaystyle h_v^{(1)}=\left( \sum^{l^v}_{j=0}w_{1_j}L_j(v) \right) \\
\displaystyle h_v^{(l)}=f\left( \sum^{L^v}_{j=0}w_{l_j}L_j(v)+\sum^{l-1}_{j=1}\hat{w}_{j_j}\sum_{u \in  N(v)}h_u^{(j)} \right)
\end{cases}$$



### Graph Echo state network
un approccio alle reti per grafi tramite reti randomizate è l utilizzo delle [[Reservoir Computing - Echo State Network (ESN)| Echo State network]] dove si usa un vettore un vettore $h$ per il reservori
$$\begin{cases}

\mathbf{h}_v^{(l)}=\tanh\left( \sum^{L^v}_{j=0}\overline{w_{l_j}}L_j(v) + \sum_{u\in  N(v)  } \hat{W}h_u^{(l-1)}\right) \\
y(\mathbf{g})=\mathbf{W}_{out}X(\mathbf{h}(\mathbf{g}))
\end{cases}
$$

## Problemi nei modelli di apprendimento su grafi

I DGN affrontano sfide significative, tra cui:
- **Over-smoothing**: con l’aumento della profondità, i nodi tendono a diventare indistinguibili
- **Over-squashing**: la capacità di rappresentare informazioni a lungo raggio diminuisce esponenzialmente con la profondità
- **Scalabilità**: addestrare reti profonde su grafi molto grandi è computazionalmente costoso
### Soluzioni proposte:

1. **Graph Echo State Networks (GESN)**: evitano il backpropagation completo e accelerano l’apprendimento
2. **NN4G+**: modelli che costruiscono architetture dinamicamente in modo efficiente
3. **Analisi spettrale**: studi per mantenere alta la variabilità spaziale delle rappresentazioni

## Applicazioni e sviluppi futuri

I DGN trovano applicazioni in molti ambiti, come:
- **Bioinformatica**: predizione di proprietà dinamiche nei percorsi biochimici
- **Chimica computazionale**: generazione di nuove molecole con reti generative
- **Spiegabilità dei modelli**: XAI per interpretare le decisioni delle reti neurali
- **Apprendimento continuo**: estensione delle DGN a contesti di lifelong learning

Le ricerche future mirano a **rendere più efficienti le DGN**, migliorando la loro scalabilità, interpretabilità e applicabilità a contesti dinamici.



![[IMG - Dynamical System.png]]