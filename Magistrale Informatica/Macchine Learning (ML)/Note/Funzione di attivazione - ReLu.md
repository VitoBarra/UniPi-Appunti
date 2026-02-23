---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area: "[[Reti Neurali (NN)]]"
topic: 
SubTopic:
---
# Funzione di attivazione - ReLu
---
La __[[Funzioni di attivazione |funzione di attivazione]] Ratified Linear__ (__ReLu__) è definita come: 
$$Relu(x) = \max(0,x)$$

![[Pasted image 20241227064955.png]]

è spesso utilizzata nel [[UniPi-Appunti/Magistrale Informatica/Macchine Learning (ML)/Note/Deep Learning|deep learning]] per via della sua derivata : $$Relu'= \begin{cases}
0  & if  & x<0 \\
1  & if &  x>0
\end{cases}$$ 