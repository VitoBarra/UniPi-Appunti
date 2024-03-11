---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic:
---

# Illuminazione - Tipi di fonte di luce
---
nel [[Illuminazione nella Computer Grafica|Illuminazione nella Computer Grafica]] sono considerati deversi tipi di fonte di luce 

direzionale: la luce è costante su tutta la scenta è si usa per rappresentare luce al intera scena che viene da molto lontano, come ad esempio il sole.
punto o posizionale:  varia tra la scena e i usa per modellare cose come lampioni o luci vicine
![[Pasted image 20240229232910.png]]

 spotlight:  
 ad area:
![[Pasted image 20240301003151.png]]
 
 per la spotlight vale $$f_s=
\begin{cases}
1 & \alpha <\theta_{\text{inner}} \\
\cos(\alpha-\theta_{\text{inner}})^n &\theta_{\text{inner}}<\alpha<\theta_{\text{outer}}  \\
0 & \alpha>\theta_{\text{outer}}
\end{cases}$$
 ![[Pasted image 20240307185042.png]]