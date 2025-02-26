---
Course: "[[Machine Learning (ML)]]"
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
Le  __reti neurali Artificiale__ (__ANN__ o __NN__) è un paradigma di [[Concetti generali del Machine Learning|Machine learning]] biologicamente inspirato e sotto insieme degli approcci __sub simbolici__. Usa [[Algoritmi di apprendimento supervisionato|algoritmi di learning supervisionavi]] genera [[Modelli Parametrici|modelli parametrici]].

una __Rete neurale__ è caratterizzata da 3 cose:
- __unita__: Il tipo di funzione di attivazione
- __Architettura__: Il numero di unita e la topologia delle connessioni
- __Algoritmo di learning__: l algoritmo di learning usato per fare la ricerca dei pesi

Le  __unita di calcolo__  sono dette anche  __neuroni__  e sono definiti come  definiti come $$\begin{cases}
net_i(\mathbf{x})=\sum w_{ij}x_j \\
o_i(\mathbf{x}) = f(net_i(x))
\end{cases}$$ovvero un __unita__ prende in input dei valori $\mathbf{x}$ pesati con $\mathbf{w}$ (i parametri) e dopo averli sommati ci applica una [[Funzioni di attivazione|funzione di attivazione]]  $f(\mathbf{x})$  producendo un output.

![[Pasted image 20241226164009.png]]




#### Algoritmo di apprendimento
L l' algoritmo usato delle reti neurali per funzionare è l algoritmo di [[BackPropagation|BackPropagation]] 


### Capacita espressiva
la capacita di generalizzare delle __reti neurali__ è teoricamente giustificata dal [[Teorema di approssimazione universale]]


## VC-Dimesion
la [[Statistical Learning Theory (SLT)|VC-dimension]] per le reti neurali è dinamica e dipenda principalmente dalla dimensione dei pesi infatti
- con pesi a  $0$ è minima perche nessun collegamento è attivo
- con pesi sono piccoli in modulo si ha __VC-dimension__ bassa siccome le [[funzioni di attivazione|funzioni di attivazione]] sono ancora nella parte lineare 
- se i pesi grandi in modulo il modello  si ha __VC-dimension__ altra siccome le [[funzioni di attivazione|funzioni di attivazione]] sono ancora nella parte __NON__ lineare 



