---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Sampling
---
Il __Sampling__ è un concetto riutilizzato in molti contesti. 
In generale per __sampling__ ci si riferisce al __campionare__ in un certo modo un generico dominio. Il sampling generato da dal campionamento puo essere poi utilizzato in vario modo asseconda del contesto ad esempio si utilizza per fare [[Meshing e il Remeshing|remeshing]] e il [[Ray Tracing|ray tracing]] 

Ci sono vari modi di fare __sampling__ tra i piu semplici ci sono i sampling __random__, __uniformi__ e  __jittered__
![[Pasted image 20241208215736.png]]
Il __sampling random__ si ottiene scegliendo casualmente su una [[Probabilita con distribuzione uniforme|distribuzione uniforme]] due valori per le coordinate $x,y$  non ha nessuna proprietà particolare ed è molto probabile che due campioni diversi siano molto vicini rendendo il sampling inefficiente

il __sampling uniforme__ campiona in modo uniforme ovvero ogni campione è ugualmente distante da tutti gli altri. Questo tipo di sampling tende a dare problemi di aliasing quando il dominio sottostante ha anche esso una struttura regolare

il __sampling jittered__ è un trade off tra sampling randomico e sampling uniforme. Si parte da una __sampling uniforme__ successivamente si spostano i punti di una quantità casuale e limitata, in questo modo si evitano situazioni in cui ci sono troppi punti vicini ma si mantiene una certa randomicita che in molti contenti applicativi da de risultati migliori.