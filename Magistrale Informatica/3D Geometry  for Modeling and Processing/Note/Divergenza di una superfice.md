---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Divergenza di funzione
---
per **divergenza  di funzione** si intende come la divergenza del campo delle [[Normale di una superfice parametrica|normali]] sulla [[Superfici|superfice]].
**sia**
- $S:\mathbb{R}^2\to \mathbb{R}^3$ una [[Superfici parametriche|superfice parametrica]] 
**allora** la divergenza è definita come una funziona $div: \mathbb{R}^2 \to \mathbb{R}$ come : $$div \ S(u,v) =  \cfrac{\partial S}{\partial u} +\cfrac{\partial S}{\partial v}$$
intuitivamente prendendo un punto $\mathbf{p}$ la divergenza di $div \ (\mathbf{p})$ è la misura di quanto il flusso delle normali va verso/scappa da al punto $\mathbf{p}$ 
![[IMG - esempi Divergenza di una superfice.png]]

la divergenza  puo anche essere espressa con la [[Curvatura media|curvatura media]] in fatti indicandola con $H$ si ha: 

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
  - **normali parallele**, **divergenza nulla**
La **divergenza della normale** cattura come la superficie "cambia" attorno a un punto
![[IMG - divergenza.png]]
![[IMG - tipi di curve.png]]
