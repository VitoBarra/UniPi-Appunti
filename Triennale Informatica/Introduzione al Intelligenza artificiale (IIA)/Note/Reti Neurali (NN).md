---
Course: "[[Intelligenza Artificiale (IA)]]"
Area: "[[Concetti generali del Machine Learning]]"
topic: "[[Intelligenza Artificiale (IA)|Reti neurali]]"
SubTopic: 
tags:
  - IA
  - ML
State: Trash
---
# Reti Neurali Artificiali (ANN)
---
Le  __reti neurali Artificiale__ (__ANN__ o __NN__) è un paradigma di [[Concetti generali del Machine Learning|Machine learning]] biologicamente inspirato e sotto insieme degli approcci __sub simbolici__. Usa [[Algoritmi di apprendimento supervisionato|algoritmi di learning supervisionavi]] genera [[Modelli di machine learning parametrici|modelli parametrici]].

Una __NN__ è composta da __neuroni__ ovvero __unita__ di calcolo semplici definiti come 
$$\begin{cases}
net_i(\mathbf{x})=\sum w_{ij}x_j \\
o_i(\mathbf{x}) = f(net_i(x))
\end{cases}$$ovvero __unita__ prende in input dei valori $\mathbf{x}$ pesati con $\mathbf{w}$ (i parametri) e dopo averli sommati ci applica una [[Funzioni di attivazione|funzione di attivazione]]  $f(\mathbf{x})$  producendo un output.
![[Pasted image 20241226164009.png]]


### Deep learning
un approccio per struttura una rete neurale dove si usano molto l hidden layer.
avere piu layer permette di creare delle feature astratte sopra i dati 

![[EB46EDF4-4878-493A-BFAF-34A6CD08DE61.jpeg]]


è un modello multo buono che utilizza la composizionalita per avere un gain esponenziale 




#### Algoritmo di apprendimento
L l' algoritmo usato delle reti neurali per funzionare è l algoritmo di [[BackPropagation|BackPropagation]] 


