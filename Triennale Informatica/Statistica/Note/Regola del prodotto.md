---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Regola del prodotto
---
La **regola del prodotto** esprime una probabilità congiunta come prodotto tra una probabilità condizionata e una probabilità marginale. Deriva direttamente da [[Probabilita condizionata|probabilità condizionata]] e, per due eventi $A$ e $B$ non trascurabili, assume la forma $$\mathcal{P}(A \cap B) = \mathcal{P}(A\mid B)\mathcal{P}(B)=\mathcal{P}(B\mid A)\mathcal{P}(A)$$
Le due uguaglianze seguono da $$\begin{array}
\mathcal{P}(A \mid B)  & = &\displaystyle  \frac{\mathcal{P}(A \cap B)}{\mathcal{P}(B)}  & \implies &  \mathcal{P}(A \mid B)\,\mathcal{P}(B)  & = &  \mathcal{P}(A \cap B) \\
\mathcal{P}(B \mid A)  & = &\displaystyle  \frac{\mathcal{P}(A \cap B)}{\mathcal{P}(A)}  & \implies &  \mathcal{P}(B \mid A)\,\mathcal{P}(A)  & = &  \mathcal{P}(A \cap B) 
\end{array}$$
e quindi vale l'identità $$\boxed{\mathcal{P}(A \mid B)\mathcal{P}(B)=\mathcal{P}(B \mid A)\mathcal{P}(A)=\mathcal{P}(A \cap B)}$$