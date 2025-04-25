---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Inviluppo Alpha (Alpha hull) 
---
le **Inviluppi Alpha** (**alpha hull**) di un [[Insiemi Matematici|insieme]] $S \subset \mathbb{R}^n$ finito sono un generalizzazione degli [[Inviluppo convesso (Convex Hull)|inviluppi convessi]] per rendere possibile creare forme non [[Convessità|convesse]], ovvero concave.

**sia** $EB_{\alpha,i}(S)$ una [[Palla|palla]] con raggio $\alpha$ fisso che tocca almeno un punto in $S$  e che non contiene nessun punto di $S$.  
**allora** l **inviluppo alpha** è definito come 
$$CH(K) = \mathbb{R}^n \backslash \bigcup_i EB_{\alpha,i}(S)$$
![[IMG - Alpha hull.png]]
si ha che con:
- $\alpha \to \infty$ l inviluppo ottenuto tende al [[IMG - Inviluppo convesso (Convex Hull) con sempispazi.png|inviluppo convesso]]
- $\alpha \to 0$ l inviluppo ottenuto tende a reggini sempre piu piccole fino a contenere sono i punti $S$ 
![[IMG - effetto del valore alpha negli alpha haull.png]]