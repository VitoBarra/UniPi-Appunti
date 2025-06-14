---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Formula di Bayes
---
la **Formula di Bayes** deriva direttamente dalla [[Probabilita condizionata|probabilita condizionata]]:

**_siano_** $A$ e $B$ due [[Definizione di Probabilita|eventi]] non _trascurabili_
_**allora**_$$\mathcal{P}(B\mid A)=\frac{\mathcal{P}(A\mid B)\mathcal{P}(B)}{\mathcal{P}(A)}$$e in piu vale che 
_sia_ $B_1,\dots,B_n$ un _[[Sistema di alternative|sistema di alternative]]_ e  $A$ un _evento non trascurabile_
_allora_ valgono le formule$$
\begin{array}{}
\mathcal{P}(A) = \sum^n_{i=1}\mathcal{P}(A|B_i)\mathcal{P}(B_i) \\ \\
\mathcal{P}(B_i|A) =\cfrac{\mathcal{P}(A|B_i)\mathcal{P}(B_i)}{\mathcal{P}(A)} =\cfrac{\mathcal{P}(A|B_i)\mathcal{P}(B_i)}{\sum^n_{j=1}\mathcal{P}(A|B_j)\mathcal{P}(B_j)}
\end{array}
$$la _dimostrazione_ si dimostra la prima formula notando che $A=(A\cap B_{1})\cup \dots\cup(A\cap B_{n})$ e sono a due a due eventi _disgiunti_ e si ha pertanto che vale $$\mathcal{P}(A)=\sum^{n}_{i=1} \mathcal{P}(A \cap B_{i})=\sum^{n}_{i=1}\mathcal{P}(A|B_{i})\mathcal{P}(B_{i})$$