---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Algoritmi di community detection
---
Gli **algoritmi di community detection** sono metodi utilizzati in [[Network Science|analisi delle reti]] per identificare **[[Network Science - Community o moduli|comunità]] (moduli)**, cioè gruppi di nodi **densamente connessi tra loro** e **poco connessi con il resto della rete**.

La **modularità** $Q$ è una misura utilizzata per valutare **quanto una specifica partizione della rete in comunità sia significativa**. L’idea è confrontare il numero di archi realmente osservati **all’interno delle comunità** con il numero di archi che ci si aspetterebbe **se la rete fosse casuale**.

Formalmente:$$Q=\frac{1}{2M}\sum_{i,j}\left(A_{ij}-\frac{k_i k_j}{2M}\right)\delta(c_i,c_j)$$dove:
- $M$ è il numero totale di archi della rete
- $A_{ij}$ indica se esiste un arco tra i nodi $i$ e $j$
- $k_i$ e $k_j$ sono i gradi dei nodi $i$ e $j$
- $\cfrac{k_i k_j}{2M}$ rappresenta il numero di archi **attesi** tra $i$ e $j$ in un modello casuale che mantiene gli stessi gradi dei nodi
- $\delta(c_i,c_j)$ vale $1$ se i nodi $i$ e $j$ appartengono alla **stessa comunità**, e $0$ altrimenti.
La somma considera quindi **solo le coppie di nodi appartenenti alla stessa comunità** e verifica se il numero di connessioni osservate è maggiore di quello atteso nel modello casuale.

Valori elevati di $Q$ indicano che:
- i nodi all’interno delle comunità sono **più densamente connessi tra loro**
- le connessioni tra comunità diverse sono **relativamente poche**


Gli algoritmi di community detection cercano quindi una partizione della rete che **massimizzi la modularità $Q$**, cioè quella in cui la struttura modulare della rete è più evidente.

### Ottimizzazione della modularità
Trovare la partizione della rete che massimizza $Q$ è un problema **[[Classi di complessita - NP-Hard|NP-hard]]**. Per questo motivo gli algoritmi di community detection utilizzano **strategie euristiche** che producono soluzioni approssimate ma computazionalmente efficienti.

Tra gli approcci più utilizzati:
- **Louvain algorithm**  
  algoritmo gerarchico greedy che ottimizza iterativamente la modularità aggregando nodi e comunità. È molto efficiente e adatto a reti di grandi dimensioni.
- **Infomap**  
  metodo basato su **random walk** e **[[Teoria del informazione (TDI)|teoria dell’informazione]]**, che identifica le comunità come regioni della rete in cui un camminatore casuale tende a rimanere più a lungo.