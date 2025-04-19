---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Curvatura Gaussiana
---
La **curvatura gaussiana** $K$ è uno scalare associato ad un punto $x \in S$ su una [[Superfici parametriche|superfice parametrica]], ed è definito come il prodotto delle **[[Curvatura di una superfice|curvature ]] principali**, ovvero il valore di curvatura calcolato nella direzione di curvatura massima $k_M$ e di **curvatura minima** $k_m$ ovvero :$$
K = k_M \cdot k_m
$$Questa definizione consente di distinguere diversi comportamenti locali della superficie: infatti 

**Se** $K > 0$, le curvature principali hanno lo stesso segno. Questo accade ad esempio nelle superfici **ellittiche**, come la sfera. In questo caso, la superficie è localmente convessa (o concava) in tutte le direzioni: $k_M > 0 , k_m > 0$

**Se** $K = 0$, si hanno due situazioni possibili:
- La superficie è detta **planare**, ovvero localmente piatta, quando $k_1 = k_2 = 0$
- La superficie è detta  **parabolica** quando esattamente una delle due curvature è nulla, ad esempio $k_M = 0, k_m \ne 0$

**Se** $K < 0$, le curvature principali hanno segno opposto. la superfice è detta  **iperbolica**: ad esempio $k_M > 0, k_m < 0$

![[IMG - tipi di curve.png]]
![[IMG - Curvatura Gaussiana valenza.png]]

![[IMG - Tipi di curvatura su di un toro.png]]

sle superfici a **curvatura gaussiana** $K=0$ sono detto anche **superfici sviluppabili** è sono un tipo di superfice in cui non si aggiunge distorsione se le sia appiattisce 
![[IMG - superfici sviluppabili.png]]
La curvatura gaussiana $K$ è una misura **intrinseca** delle proprietà geometriche di una [[Superfici|superficie]] infatti il valore della curvatura gaussiana **non dipende** da come è posizionata nello spazio.

Un modo intuitivo per comprendere questa intrinsechezza è pensare a cosa accade quando ci si muove **sulla superficie stessa**, mantenendo una [[distanza geodetica|distanza geodetica]] costante da un punto. Se ci immaginiamo, ad esempio, su una sfera (come una persona sulla Terra), e decidiamo di costruire un recinto a una distanza $r$ costante dal centro della nostra proprietà, possiamo misurare quanto è lungo questo recinto, cioè la circonferenza $C(r)$.

Nel caso del piano euclideo, il risultato è noto:
$$
C(r) = 2\pi r
$$

Tuttavia, se ci troviamo su una superficie curva, questo rapporto può cambiare. Ecco alcuni casi:

- Su una superficie con $K = 0$ (cioè un piano), la lunghezza del recinto sarà esattamente $2\pi r$, qualunque sia il valore di $r$.  
- Su una superficie con $K>0$ (come una sfera), per piccoli $r$ il recinto misurato sarà **più corto** di $2\pi r$. Lo spazio si “chiude” più rapidamente di quanto accadrebbe su un piano.  
- Su una superficie con $K<0$  (come una sella o un iperboloide), la lunghezza del recinto sarà **più lunga** di $2\pi r$. Lo spazio si “apre” più velocemente.
Questo comportamento può essere quantificato dal seguente limite:

$$
K = \lim_{r \to 0} \frac{6\pi r - 3C(r)}{\pi r^3}
$$

Questo rapporto confronta il valore atteso della circonferenza nel piano (cioè $2\pi r$) con quello reale sulla superficie, e misura quanto la geometria locale devia da quella euclidea.
![[IMG - Curvatura Gaussiana su oggetti reali.png]]


