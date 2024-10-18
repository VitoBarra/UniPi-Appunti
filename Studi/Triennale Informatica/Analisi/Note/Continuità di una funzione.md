---
Course: "[[Analisi]]"
tags:
  - Analisi
---
# Continuità di una funzione
---
Una [[Funzioni|funzione]] $f:A \rightarrow\mathbb{R}$ è definita su un [[Insiemi Matematici|sottoinsieme]] dei numeri reali a valori reali si dice continua in un punto $p \in A$ se per ogni numero $\varepsilon>0$ _arbitrariamente_ piccolo, esiste un secondo numero $\delta >0$ tale che, $\forall x\in  A\cap (p-\delta,p+\delta)$, la funzione $f(x)$ dista da $f(p)$ per meno di $\varepsilon$ ovvero:

$$|f(x) - f(p)|<\varepsilon$$
In linguaggio simbolico, una funzione è continua in un punto $p$ se:$$\forall\varepsilon >0\ \exists \delta > 0 : |x-p|<\delta \Rightarrow |f(x)-f(p)|<\varepsilon$$
Se questa proprietà vale per ogni punto nel dominio di definizione della funzione, allora si dice che la funzione è continua. In questo caso si dice che $f(x) \in C(A,\mathbb{R})$, che è l'insieme delle funzioni continue a valori reali e variabili in $A$.

Più intuitivamente, se si vuole che la funzione $f(x)$ disti di un valore piccolo da $f(p)$ ci basta restringerci ad un intorno abbastanza piccolo del punto $p$. Se questo è possibile qualunque sia la distanza scelta (a meno di restringere ulteriormente l'intorno di $p$, allora la funzione è continua in $p$.
![[IMG_0707.png]]

