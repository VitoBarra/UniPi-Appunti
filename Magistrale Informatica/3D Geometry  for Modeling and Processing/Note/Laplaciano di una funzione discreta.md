---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Laplaciano di una funzione discreta
---
Il **laplaciano discreto** è una versione del [[Laplaciano di una funzione|laplaciano]] calcolata pero non su di una [[Funzioni|funzione]] [[Continuità di una funzione|continua]] ma su una [[Mesh Poligonali|mesh poligonale]], rendendolo quindi un concetto di [[Geometria Differenziale Discreta|geometria differenziale discreta]]

**laplaciano discreto** si puo calcolare approssimando il [[Laplaciano di una funzione|laplaciano continuo]] su un punto delle $x$ della [[Mesh Poligonali|mash]] considerando il suo vicinato $N(x)$. 

**sia**
- $f: \mathbb{R}^2 \to \mathbb{R}^3$ una [[Funzioni|funzione]]
- $\mathcal{M}$ una [[Mesh Poligonali|mesh pologonale]] che approssima la funzione $f$
- $v \in \mathcal{M}$ un [[Computer grafica - Primitive Geometriche|vertice]] della [[Mesh Poligonali|mesh]]
- $N(v)$ la lista del vicinato di $v$ 
**allora** la **discretizzazione uniforme** del laplaciano è definita come come:$$\Delta_{uni}f(v) := \frac{1}{|N_1(v)|} \sum_{v_i \in N(v)} (f(v_i) - f(v))$$che è un approccio semplice perche dipende solo dalla connettività della mesh ma sensibile a triangolazioni irregolari, poiché ignora la geometria locale, come nel caso delle [[Normale di una superfice discreta (Mesh poligonali)|normli]]  

mentre un approccio migliore è quello della **Formula della cotangente**:  $$\Delta_S f(v) := \frac{2}{A(v)} \sum_{v_i \in N(v)} (\cot \alpha_i + \cot \beta_i) (f(v_i) - f(v))$$Pesa gli archi con le cotangenti degli angoli opposti $\alpha_i$, $\beta_i$, bilanciando l’influenza di triangoli distorti. Questo metodo è geometricamente più stabile.
![[IMG - Laplaciano di una funzione discreta metodo cotangenti.png]]


