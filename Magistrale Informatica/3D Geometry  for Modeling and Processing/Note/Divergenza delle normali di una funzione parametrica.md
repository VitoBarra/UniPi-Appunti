---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Divergenza delle normali di una funzione parametrica
---

La **Divergenza delle [[Normale di una superfice parametrica|normali]] di una [[Superfici|superficie]]** è un'applicazione della definizione generale di [[Definizione di divergenza|Divergenza]] a un particolare campo vettoriale associato alla superficie: il **campo delle normali unità**.

**sia**
- $S:\mathbb{R}^2\to \mathbb{R}^3$ una [[Superfici parametriche|superficie parametrica]]
- il **campo delle normali** è $N = S_u \times S_v$
- e la **normale unitaria** $n = \cfrac{S_u \times S_v}{\|S_u \times S_v\|}$ che definisce un **campo vettoriale nello spazio** nei punti della superficie.
Applicando la definizione standard di [[Definizione di divergenza|Divergenza]] a questo campo vettoriale si ottiene la **divergenza della normale**$$\nabla \cdot n$$Questa quantità misura quanto il campo delle normali **si espande o converge localmente** attorno a un punto della superficie.

Intuitivamente, prendendo un punto $\mathbf{p}$ sulla superficie, la divergenza $\nabla\cdot n(\mathbf{p})$ misura quanto il flusso delle normali **si allontana o converge** attorno a $\mathbf{p}$.
![[IMG - esempi Divergenza di una superfice.png]]
La divergenza della normale è direttamente collegata alla [[Curvatura media]] $H$ tramite$$\nabla \cdot n = 2H$$Interpretazione geometrica tramite la curvatura media:

**se** $H > 0$ ci sono 2 casi:
- caso di una superficie **ellittica**:  
  - **Normali divergenti in tutte le direzioni**  
  - entrambe le curvature principali sono **positive**
- caso di una superficie **parabolica** (es. piega cilindrica):  
  - **Normali divergenti in una sola direzione**  
  - una curvatura principale è **positiva**, l’altra è **zero**

**se** $H < 0$ :
- caso di una superficie **iperbolica**:  
  - **Normali che si aprono in direzioni opposte**  
  - una curvatura principale è **positiva**, l’altra è **negativa**  
  - la somma è **negativa**, quindi la curvatura media è negativa

**se** $H = 0$ :
- caso di una **superficie piana**:  
  - entrambe le curvature sono **nulle**  
  - **Normali parallele**, **divergenza nulla**
La divergenza della normale descrive quindi **come la superficie si incurva localmente**, poiché misura come il campo delle normali varia attorno a un punto.
![[IMG - tipi di curve.png]]




