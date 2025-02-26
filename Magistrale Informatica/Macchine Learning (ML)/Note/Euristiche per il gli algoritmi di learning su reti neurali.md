---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Euristiche per il gli algoritmi di learning su reti neurali
---

Le reti neurali rappresentano un paradigma flessibile e potente nell'ambito dell'apprendimento automatico. Estendono i metodi lineari, permettendo l'approssimazione di funzioni arbitrarie, incluse quelle non lineari. Nel corso del documento, si esplorano i principi fondamentali dell'addestramento, le sfide comuni e le soluzioni pratiche.

---

## Sfide comuni nell'addestramento delle reti neurali

Uno dei problemi principali riguarda l'over-parametrizzazione del modello, che aumenta il rischio di overfitting. Questa condizione si verifica quando la rete apprende troppo dai dati di addestramento, perdendo capacità di generalizzare. Inoltre, il processo di ottimizzazione è spesso non convesso, portando a instabilità e difficoltà nel raggiungere minimi globali. 

Tra le questioni affrontate:
- La scelta dei __iperparametri__, come i valori iniziali dei pesi, il tasso di apprendimento ($\eta$) e la dimensione del batch.
- La presenza di __minimi multipli__, che rende l'addestramento dipendente dall'inizializzazione.
- Criteri di arresto, fondamentali per evitare il sovra-allenamento.
- La necessità di bilanciare la complessità del modello con tecniche come la regolarizzazione.

---

## Algoritmi di apprendimento

### Discesa del gradiente
La discesa del gradiente costituisce il cuore dell'addestramento delle reti neurali. Questo metodo si basa sul calcolo del gradiente dell'errore rispetto ai pesi della rete, aggiornandoli per ridurre progressivamente l'errore. Sono state sviluppate diverse varianti per migliorare l'efficienza:
- __Batch gradient descent__: calcola il gradiente sull'intero set di dati per ogni aggiornamento dei pesi, garantendo stime precise ma richiedendo più tempo.
- __Online (stocastico) gradient descent__: aggiorna i pesi dopo ogni esempio, rendendo l'addestramento più rapido ma meno stabile.
- __Mini-batch gradient descent__: combina i vantaggi delle due modalità precedenti, aggiornando i pesi dopo aver elaborato piccoli gruppi di esempi.

### Heuristics per migliorare la convergenza
Per accelerare la convergenza e stabilizzare l'ottimizzazione, si usano tecniche come il __momentum__, che aggiunge una frazione dello spostamento precedente al gradiente attuale. Questo aiuta a superare le oscillazioni e velocizza l'apprendimento in superfici con plateau.

Altre innovazioni includono:
- __Momentum di Nesterov__, che valuta il gradiente dopo l'applicazione del momentum, migliorando la velocità di convergenza.
- __Tassi di apprendimento adattivi__, come AdaGrad, RMSProp e Adam, che regolano automaticamente $\eta$ durante l'addestramento, adattandosi alle caratteristiche dei dati.

---

## Regolarizzazione

La regolarizzazione è una tecnica fondamentale per prevenire l'overfitting e controllare la complessità del modello. Viene aggiunto un termine di penalità alla funzione di perdita:
$$ L(w) = MSE + \lambda \|w\|^2 $$
Questo termine favorisce pesi più piccoli, riducendo la capacità della rete di adattarsi eccessivamente ai dati di addestramento. La selezione del parametro $\lambda$ avviene tipicamente attraverso la validazione incrociata.

Un approccio alternativo è l'__early stopping__, che utilizza un set di validazione per determinare il momento ottimale per arrestare l'addestramento, evitando che la rete diventi troppo complessa.

---

## Configurazione dell'architettura

La scelta del numero di unità nascoste è critica per bilanciare underfitting e overfitting. Una rete con troppe poche unità non riesce a catturare la complessità dei dati, mentre una rete con troppe unità rischia di adattarsi eccessivamente.

Due approcci principali guidano la configurazione:
1. __Costruttivi__: partono con una rete minima, aggiungendo unità durante l'addestramento quando necessario. Un esempio è l'algoritmo __[[Reti neurali approccio costruttivo Cascade Correlation|Cascade Correlation]]__, che aggiunge unità in modo incrementale fino a ridurre sufficientemente l'errore.
2. __Pruning__: iniziano con una rete grande, eliminando progressivamente unità o connessioni non necessarie.

---

## Preprocessing degli input e output

Il preprocessing dei dati in ingresso è fondamentale per garantire un addestramento stabile. Le tecniche includono:
- __Normalizzazione__: scalare i dati in un intervallo $[0,1]$ o standardizzarli a media zero e deviazione standard unitaria.
- __Codifica categorica__: rappresentare variabili categoriali con tecniche come 1-of-K encoding.

Per gli output:
- Nelle attività di __regressione__, si usano unità lineari.
- Per la __classificazione__, sono comuni funzioni di attivazione sigmoidee o softmax, quest'ultima particolarmente utile per interpretare le probabilità delle classi.

---

## Considerazioni finali

Le reti neurali si sono dimostrate strumenti estremamente versatili. Grazie alla loro capacità di apprendere funzioni complesse, sono applicabili a una vasta gamma di problemi, dalla classificazione alla regressione, fino alle applicazioni non supervisionate.

Tuttavia, presentano alcune limitazioni. La loro natura di "black box" le rende difficili da interpretare, un problema che la ricerca sull'intelligenza artificiale interpretabile (XAI) sta cercando di affrontare. Inoltre, l'efficacia delle reti neurali dipende in modo significativo dalla scelta degli iperparametri e dall'accuratezza del preprocessing.

In conclusione, le reti neurali sono uno strumento potente, ma richiedono un'attenta progettazione e analisi per ottenere i migliori risultati.
