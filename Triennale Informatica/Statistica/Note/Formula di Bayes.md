---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Formula di Bayes
---
La **formula di Bayes** permette di aggiornare la probabilita di un'ipotesi alla luce di una nuova osservazione. In particolare, consente di esprimere la probabilita condizionata "inversa" $\mathcal{P}(B \mid A)$ a partire da $\mathcal{P}(A \mid B)$, ed e quindi uno strumento fondamentale nell'inferenza probabilistica. Questa deriva direttamente dalla [[Probabilita condizionata|probabilita condizionata]] e dal applicazione della [[regola del prodotto|regola del prodotto]]

**Siano** $A$ e $B$ due [[Definizione di Probabilita|eventi]] non trascurabili. Allora$$\mathcal{P}(B \mid A)=\frac{\mathcal{P}(A \mid B)\mathcal{P}(B)}{\mathcal{P}(A)}$$I nomi standard dei termini sono:
- $\mathcal{P}(B \mid A)$: **probabilita a posteriori** o **posterior**. Rappresenta quanto l'ipotesi $B$ sia plausibile *dopo* aver osservato $A$
- $\mathcal{P}(A \mid B)$: **verosimiglianza** o **likelihood**. Misura quanto l'osservazione $A$ sia compatibile con l'ipotesi $B$, cioe quanto bene $B$ "spieghi" i dati osservati.
- $\mathcal{P}(B)$: **probabilita a priori** o **prior**. Si chiama cosi perche esprime la plausibilita iniziale di $B$ *prima* di osservare $A$.
- $\mathcal{P}(A)$: **evidenza**, **probabilita marginale** di $A$ o **normalizzatore**. Si chiama evidenza perche rappresenta la probabilita complessiva dei dati osservati, ottenuta considerando tutte le possibili ipotesi; si chiama normalizzatore perche rende la probabilita a posteriori una distribuzione valida.
In forma mnemonica:$$\text{posterior}=\frac{\text{likelihood}\cdot\text{prior}}{\text{evidence}}$$



Inoltre, sia $B_1,\dots,B_n$ un [[Sistema di alternative|sistema di alternative]] e sia $A$ un evento non trascurabile. Allora valgono le formule

$$
\begin{aligned}
\mathcal{P}(A) &= \sum_{i=1}^n \mathcal{P}(A \mid B_i)\mathcal{P}(B_i) \\
\mathcal{P}(B_i \mid A) &= \frac{\mathcal{P}(A \mid B_i)\mathcal{P}(B_i)}{\mathcal{P}(A)}
= \frac{\mathcal{P}(A \mid B_i)\mathcal{P}(B_i)}{\sum_{j=1}^n \mathcal{P}(A \mid B_j)\mathcal{P}(B_j)}
\end{aligned}
$$

Qui:
- $\mathcal{P}(B_i \mid A)$ e il **posterior** dell'ipotesi $B_i$
- $\mathcal{P}(A \mid B_i)$ e la **likelihood**
- $\mathcal{P}(B_i)$ e il **prior**
- $\mathcal{P}(A)$ e l'**evidenza totale**, ottenuta per [[FJD - Marginalizzazione|marginalizzazione]]

Per la dimostrazione della formula dell'evidenza si osserva che

$$
A=(A\cap B_1)\cup \dots \cup (A\cap B_n)
$$

e che gli eventi $(A\cap B_i)$ sono a due a due disgiunti. Pertanto

$$
\mathcal{P}(A)=\sum_{i=1}^{n}\mathcal{P}(A\cap B_i)=\sum_{i=1}^{n}\mathcal{P}(A \mid B_i)\mathcal{P}(B_i)
$$
