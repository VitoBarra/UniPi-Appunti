---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Formula di Bayes
---
La **formula di Bayes** permette di aggiornare la [[Definizione di Probabilita|probabilita]] di un'ipotesi alla luce di una nuova osservazione. In particolare, consente di esprimere la probabilità condizionata "inversa" $\mathcal{P}(B \mid A)$ a partire da $\mathcal{P}(A \mid B)$, ed e quindi uno strumento fondamentale nell'inferenza probabilistica. Questa deriva direttamente dalla [[Probabilita condizionata|probabilita condizionata]] e dal applicazione della [[regola del prodotto|regola del prodotto]]

**Siano** 
- $A$ un [[Definizione di Probabilita|eventi]] non trascurabili
- $B_1,\dots,B_n$ un [[Sistema di alternative|sistema di alternative]] 
**Allora** $$\mathcal{P}(B_i \mid A)=\frac{\mathcal{P}(A \mid B_i)\mathcal{P}(B_i)}{\mathcal{P}(A)} = \frac{\mathcal{P}(A \mid B_i)\mathcal{P}(B_i)}{\sum_{j=1}^n \mathcal{P}(A \mid B_j)\mathcal{P}(B_j)} $$ 
I nomi standard dei termini sono:
- $\mathcal{P}(B \mid A)$: **probabilita a posteriori** o **posterior**. Rappresenta quanto l'ipotesi $B$ sia plausibile *dopo* aver osservato $A$
- $\mathcal{P}(A \mid B)$: **verosimiglianza** o **likelihood**. Misura quanto l'osservazione $A$ sia compatibile con l'ipotesi $B$, cioe quanto bene $B$ "spieghi" i dati osservati.
- $\mathcal{P}(B)$: **probabilita a priori** o **prior**. Si chiama cosi perche esprime la plausibilità iniziale di $B$ *prima* di osservare $A$.
- $\mathcal{P}(A)$: **evidenza**, **probabilita marginale** di $A$ o **normalizzatore**. Si chiama evidenza perche rappresenta la probabilita complessiva dei dati osservati, ottenuta considerando tutte le possibili ipotesi; si chiama normalizzatore perche rende la probabilita a posteriori una distribuzione valida.

$\mathcal{P}(A)=\sum_{j=1}^n \mathcal{P}(A \mid B_j)\mathcal{P}(B_j)$ viene direttamente dall'applicazione della regola di [[FJD - Marginalizzazione|marginalizzazione]] e della [[Regola del prodotto|regola del prodotto]], e dice che la probabilita complessiva di osservare $A$ si ottiene sommando i contributi di tutte le possibili ipotesi $B_j$, pesati secondo la loro probabilita a priori. In questo senso, $\mathcal{P}(A)$ e la probabilita marginale di $A$, detta anche evidenza, perche misura quanto l'osservazione sia complessivamente plausibile prima di fissare quale ipotesi $B_j$ sia vera. 
Per la dimostrazione l identita dell'evidenza si osserva che$$A=(A\cap B_1)\cup \dots \cup (A\cap B_n)$$e che gli eventi $(A\cap B_i)$ sono a due a due disgiunti. Pertanto$$\mathcal{P}(A)=\sum_{i=1}^{n}\mathcal{P}(A\cap B_i)=\sum_{i=1}^{n}\mathcal{P}(A \mid B_i)\mathcal{P}(B_i)$$

mnemonicamente la formula puo essere ricordata come:$$\text{posterior}=\frac{\text{likelihood}\cdot\text{prior}}{\text{evidence}}$$