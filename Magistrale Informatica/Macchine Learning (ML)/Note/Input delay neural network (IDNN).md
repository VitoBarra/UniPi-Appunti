---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Input delay neural network (IDNN)
---
Le __delay neural network (IDNN)__ sono un tipo di [[Reti Neurali (NN)|rete neurale]] che hanno come __dominio di input__ una serie di vettori esattamente come le [[Reti Neurali Ricorrenti (RNN)|RNN]] ma utilizzano una __finestra di delay__ per immagazzinare gli input passati. la __finestra di delay__ permette alla rete di elaborare non solo l'input corrente ma anche un certo numero di input precedenti e ciò serve a modellare le dipendenze sequenziali degli input. il numero di input che la rete può processare contemporaneamente è detta __dimensione della finestra di delay__  ed è un numero $d$  fissato prima del training della rete.
![[Pasted image 20250207233810.png]]Se consideriamo una sequenza di input $l(t)$, il vettore di ingresso alla rete in un dato istante $t$ è costituito da un insieme di valori precedenti: $$\mathbf{l}(t) = \left[ l(t), l(t-1), \dots, l(t-d) \right]$$dove $d$ rappresenta la __dimensione della finestra di delay__. Assumendo un __singolo layer__ Il comportamento di una IDNN può essere formalizzato come segue:$$y(t) = f(W \mathbf{l}(t) + b)$$dove:
- $W\in \mathbb{R}^{d\times o}$ è la matrice dei pesi con $o$ la dimensione del output
- $b$ è il bias,
- $f(\cdot)$ è la [[Funzioni di attivazione|funzione di attivazione]]

In generale la trasformazione della __finestra di delay__ può essere realizzata con qualsiasi cosa ad esempio una  __[[Reti neurali Feed-Forward (FF)|MLP]]__. 
 

## Proprietà e Limitazioni delle IDNN

Le IDNN offrono alcuni vantaggi che le rendono adatte per problemi specifici. Una delle loro principali caratteristiche è la **memoria finita e fissa**: la capacità della rete di ricordare eventi passati dipende esclusivamente dalla dimensione della finestra di ritardo. Se la finestra di ritardo è troppo piccola, alcune informazioni rilevanti possono andare perse, limitando la capacità della rete di catturare schemi complessi nei dati sequenziali.

Un'altra caratteristica fondamentale è la **rappresentazione esplicita del tempo**. A differenza delle RNN, che aggiornano dinamicamente il loro stato interno, le IDNN mantengono un contesto statico basato sui valori passati disponibili nel buffer. Questo significa che il modello non evolve nel tempo, ma analizza i dati in finestre fisse, offrendo una struttura più semplice e facilmente interpretabile.

Tuttavia, questa semplicità comporta alcuni svantaggi. Il numero di pesi da apprendere nelle IDNN dipende direttamente dalla dimensione della finestra di ritardo. Se questa aumenta, il numero di parametri cresce in modo significativo, rendendo il modello potenzialmente inefficiente per sequenze lunghe. In termini di **addestramento**, però, le IDNN risultano più semplici rispetto alle RNN, poiché possono essere addestrate con il classico **backpropagation**, senza la necessità dell'unrolling nel tempo tipico delle RNN.

Nonostante la loro efficienza in alcuni contesti, le IDNN presentano alcune limitazioni fondamentali. In particolare, non possono gestire dipendenze a lungo termine a meno che la finestra di ritardo non sia molto ampia. Ciò può comportare problemi di **sovradimensionamento del modello**, con un numero eccessivo di parametri da ottimizzare. Inoltre, le IDNN non sono adatte a dati sequenziali di **lunghezza variabile**, poiché la finestra di ritardo è un parametro fisso, e non hanno una **memoria interna adattativa**, il che le rende meno efficaci rispetto alle RNN in compiti come la modellazione di sequenze linguistiche complesse o processi biologici a lungo termine.

## Connessione con le Convolutional Neural Networks (CNN)

Un'estensione interessante delle IDNN è la loro generalizzazione nelle **reti convoluzionali ([[Reti Neurali Convoluzionali (CNN)|CNN]])**. Infatti, un **filtro convoluzionale 1D** con kernel di lunghezza $d$ può essere visto come una versione più strutturata delle IDNN, in cui:
- Il __finestra di delay__ è sostituito da una __finestra mobile (kernel)__.
- I __pesi__ sono condivisi lungo tutta la sequenza, rendendo il modello **più efficiente** e riducendo il numero totale di parametri.
Questo legame tra IDNN e CNN ha portato allo sviluppo delle **Temporal Convolutional Networks (TCN)**, che offrono un'alternativa scalabile e parallela alle RNN per il trattamento di dati sequenziali.

