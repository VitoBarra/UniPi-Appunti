---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area: 
topic: 
SubTopic:
---
# Input delay neural network (IDNN)
---
Le __Input delay neural network (IDNN)__ sono un tipo di [[Reti Neurali (NN)|rete neurale]] caso  per dati sequenziali, ed è un tipo specifico di specifico della classe [[Time delay neural network (TDNN)|TDNN]] che usa una __finestra di delay__ per includere esplicitamente gli input passati: il contesto temporale è rappresentato tramite ritardi espliciti, ma la finestra viene poi trattata come un normale vettore di input.

La __finestra di delay__ permette alla rete di elaborare non solo l'input corrente ma anche un certo numero di input precedenti, così da modellare dipendenze sequenziali locali. Il numero di input che la rete può processare contemporaneamente è detto __dimensione della finestra di delay__ ed è un numero $d$ fissato prima del training della rete.

![[IMG - Input delay neural network (IDNN).png]]

Se consideriamo una sequenza di input $l(t)$, il vettore di ingresso alla rete in un dato istante $t$ è costituito da un insieme di valori precedenti: $$\mathbf{l}(t) = \left[ l(t), l(t-1), \dots, l(t-d) \right]$$dove $d$ rappresenta la __dimensione della finestra di delay__. Assumendo un __singolo layer__ il comportamento di una IDNN può essere formalizzato come segue: $$y(t) = f(W \mathbf{l}(t) + b)$$ dove:
- $W\in \mathbb{R}^{d\times o}$ è la matrice dei pesi con $o$ la dimensione dell'output
- $b$ è il bias
- $f(\cdot)$ è la [[Funzioni di attivazione|funzione di attivazione]]

In generale la trasformazione della __finestra di delay__ può essere realizzata con qualunque funzione parametrica, ad esempio una __[[Reti neurali Feed-Forward (FF)|MLP]]__.
 
## Proprietà e Limitazioni delle IDNN

Le IDNN offrono alcuni vantaggi che le rendono adatte per problemi specifici. Una delle loro principali caratteristiche è la **memoria finita e fissa**: la capacità della rete di ricordare eventi passati dipende esclusivamente dalla dimensione della finestra di ritardo. Se la finestra di ritardo è troppo piccola, alcune informazioni rilevanti possono andare perse, limitando la capacità della rete di catturare schemi complessi nei dati sequenziali.

Un'altra caratteristica fondamentale è la **rappresentazione esplicita del tempo**. A differenza delle [[Recurrent Neural Network (RNN)|RNN]], che aggiornano dinamicamente il loro stato interno, le IDNN mantengono un contesto statico basato sui valori passati disponibili nel buffer. Questo significa che il modello non evolve nel tempo, ma analizza i dati in finestre fisse, offrendo una struttura più semplice e facilmente interpretabile.

Tuttavia, questa semplicità comporta alcuni svantaggi. Il numero di pesi da apprendere nelle IDNN dipende direttamente dalla dimensione della finestra di ritardo. Se questa aumenta, il numero di parametri cresce in modo significativo, rendendo il modello potenzialmente inefficiente per sequenze lunghe. In termini di **addestramento**, però, le IDNN risultano più semplici rispetto alle RNN, poiché possono essere addestrate con il classico **[[Back Propagation|backpropagation]]**, senza la necessità dell'unrolling nel tempo tipico delle RNN.

Nonostante la loro efficienza in alcuni contesti, le IDNN presentano alcune limitazioni fondamentali. In particolare, non possono gestire dipendenze a lungo termine a meno che la finestra di ritardo non sia molto ampia. Ciò può comportare problemi di **sovradimensionamento del modello**, con un numero eccessivo di parametri da ottimizzare. Inoltre, le IDNN non sono adatte a dati sequenziali di **lunghezza variabile**, poiché la finestra di ritardo è un parametro fisso, e non hanno una **memoria interna adattativa**, il che le rende meno efficaci rispetto alle RNN in compiti come la modellazione di sequenze linguistiche complesse o processi biologici a lungo termine.

## Connessione con le CNN

Le __IDNN__ condividono con le [[Convolutional Neural Network  (CNN)|CNN]] l'idea di usare una __finestra locale__ dell'input per catturare dipendenze di breve raggio. In entrambi i casi, infatti, l'output dipende da un intorno limitato della sequenza anziché dall'intera storia passata.

La differenza utile è questa:
- nelle __IDNN__ la sequenza viene trasformata in una finestra di delay fissa, poi trattata come un normale vettore di input;
- nelle [[Time delay neural network (TDNN)|TDNN]] e nelle __CNN 1D__ la struttura del modello è invece progettata per far scorrere lo stesso kernel lungo la sequenza.

Per questo motivo le __TDNN__ risultano strutturalmente più vicine alle [[Convolutional Neural Network  (CNN)|CNN]] rispetto alle IDNN, anche se le IDNN restano un antecedente concettuale importante perché introducono l'idea di contesto temporale locale senza ricorrere alla ricorrenza.
