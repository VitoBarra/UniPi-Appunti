---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
Course 2: "[[Computer Grafica (CG)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Indici Spaziali - KD Tree
---
I **KD-Tree** sono degli [[Indici spaziali|Indici spaziali]] basati su [[Struttura dati - Alberi|alberi]] e sono una specializzazione dei [[Indici Spaziali - Binary Space Partition-Tree (BSP)|BSP]] dove ogni piano è allineato a gli assi.
![[IMG - Indici spaziali KD-tree.png]]
il che rispetto ai [[Indici Spaziali - Binary Space Partition-Tree (BSP)|BSP]] li rende gia piu efficienti in quanto invece che dover memorizzare un intero piano basta una singola coordinata, il che è anche [[Cache|cashe]] freadly.


Un esempio di utilizzo per questi [[indici spaziali|indici spaziali]] per quanto riguarda il [[Ray Tracing|Ray Tracing]]
il costo $C(T)$ di visita di un nodo come per i [[Indici Spaziali - Binary Space Partition-Tree (BSP)|BSP]] può essere espresso come $$C(T) = 1 + \mathcal{P}(T_L)C(T_L) + \mathcal{P}(T_R)C(T_R)$$dove $\mathcal{P}(T_L)$ rappresenta la [[Definizione di Probabilita|probabilità]] che un raggio che interseca $T$ intersechi anche il sottoalbero sinistro $T_L$. 
puo essere espresso come $$\mathcal{P}(T_L) = \frac{|\text{ray intersetting } T_L|}{|\text{ray intersetting } T|}$$i raggio che intersecano una certa area sono facile da definire infatti intuitivamente vale che preso **un raggio** che interseca l area $T$ questo interseca nei punti $(p_1,p_2)$ allora questa interseca $T_L \iff$ $p_1$ o $p_2$ intersecano $T_L$   ![[IMG - Indici Spaziali - KD Tree raggi intersecanti.png]]
sapendo questo e facendo alcune assunzioni sulle [[Distribuzione di probabilita|distribuzioni]] dei raggi puo esprimere $\mathcal{P}(T_L)$ rapporto tra le aree superficiali: $$\mathcal{P}(T_L) = \frac{|\text{superficie di } T_L|}{|\text{superficie di } T|}$$
![[IMG_1115 1 1.jpeg]]

**La costruzione** di un **kd-tree** richiede come input un bounding box allineato agli assi e una lista di triangoli. Le operazioni base includono la suddivisione del bounding box lungo un piano allineato a un asse.

Analizzando un caso in cui si deve **scegliere un piano** in una scena dove la distribuzione delle primitive è fatta in modo da avere una superfice vuota e una con una distribuzione uniforme interna.
- **in the middle** : ogni raggio dovra con buona probabilità testare inutilmente molte primitive 
- **Median**:  si minimizza la profondita capita che buona parte dei raggi devono fare molti test anche quando non è necessario  
- **Cost optimizad**: si minimizza il costo facendo in modo da minimizzare $C(T)$

![[IMG - KD-tree construction.png]]



**Alcune Query**:
**Range query**: Per le query, come trovare i primitivi all'interno di un box dato, l'algoritmo 
- verifica l'intersezione tra il nodo e il box.
- Se il nodo è completamente contenuto nel box, tutti i suoi primitivi vengono aggiunti al risultato.
- Se è completamente esterno, la ricerca termina. 
- Se è parzialmente interno, si procede ricorsivamente con i figli.
Il [[Complessita|costo mputazionale]] di questa operazione, con foglie contenenti un solo primitivo e albero bilanciato, è $O(n^{1-\frac{1}{d}} + k)$, dove $n$ è il numero di primitivi e $d$ la dimensione. Il numero di possibili risultati è $O(n^{2d})$.




**Nearest Neighbor**: l'algoritmo cerca il primitivo più vicino a un punto $c$ partendo dalla foglia che lo contiene. Se la sfera centrata in $c$ interseca i confini della regione, vengono controllati anche i primitivi nelle celle adiacenti intersecate.
![[IMG - Indici spaziali KD-tree query.png]]
