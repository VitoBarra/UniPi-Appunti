---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Network Science - Network propagation
---
La **network propagation** è un metodo di analisi in [[Network Science|analisi delle reti]] che sfrutta la topologia della rete per **diffondere informazione** a partire da un insieme iniziale di nodi noti.

L’idea è che l’informazione associata a un nodo possa propagarsi lungo gli archi della rete, influenzando i nodi vicini e quelli più lontani attraverso percorsi successivi.

Principio **Guilt-by-Association** (**smoothness assumption**):  
se un nodo della rete è associato a una certa proprietà o informazione, anche i nodi **vicini nella rete** hanno alta probabilità di essere associati alla stessa proprietà.

Input:
- vettore iniziale $Y$ che identifica i nodi noti (**seed nodes**)
Output:
- vettore di punteggio $F$ che assegna a ogni nodo una **rilevanza rispetto ai seed**.

La propagazione dell’informazione avviene tramite un processo iterativo definito da$$F^{t+1}=\alpha A'F^t+(1-\alpha)Y$$dove:
- $F^t$ è il vettore dei punteggi allo step $t$
- $\alpha$ è il **fattore di smoothing** che bilancia l’informazione proveniente dalla rete e quella iniziale ($0.5<\alpha<0.9$)
- $A'$ è la **matrice di adiacenza normalizzata**, che rappresenta la struttura della rete.

Il primo termine $\alpha A'F^t$ rappresenta la **diffusione dell’informazione attraverso la rete**, mentre il secondo termine $(1-\alpha)Y$ mantiene un **ancoraggio ai nodi iniziali**.

L’iterazione continua finché la differenza tra $F^{t+1}$ e $F^t$ diventa inferiore a una soglia, raggiungendo uno **stato stazionario**.
![[IMG - Network Science - Network propagation.png]]
Il punteggio finale dei nodi non dipende solo dalla distanza dai seed, ma dalla **struttura topologica della rete** codificata nella matrice normalizzata $A'$.

Se $A'$ è **row-stochastic**, un nodo con molti archi uscenti (alto out-degree) distribuisce la propria influenza su molti vicini, riducendo l’impatto su ciascuno di essi. Al contrario, nodi che ricevono connessioni da nodi influenti possono ottenere punteggi più elevati.  

La propagazione quindi dipende non solo dalla vicinanza ai seed, ma anche dal **ruolo strutturale dei nodi nella rete**.

##### Normalizzazioni possibili
La matrice di adiacenza $A$ può essere normalizzata in diversi modi prima di applicare la propagazione:

- **Row normalization**$$A' = D^{-1}A$$
ogni riga viene normalizzata per il grado del nodo; la matrice diventa **row-stochastic** e può essere interpretata come una matrice di transizione di un **random walk**.
- **Symmetric normalization**$$A' = D^{-1/2} A D^{-1/2}$$

normalizzazione simmetrica utilizzata in molti metodi spettrali; preserva la simmetria della matrice.

- **Column normalization**$$A' = A D^{-1}$$

meno comune, ma interpreta la propagazione come distribuzione dell’informazione in base ai collegamenti entranti. La scelta della normalizzazione influenza il modo in cui l’informazione si diffonde nella rete e quindi il **ranking finale dei nodi**.

