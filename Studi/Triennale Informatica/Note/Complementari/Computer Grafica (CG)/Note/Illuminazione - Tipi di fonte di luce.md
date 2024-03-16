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

  

#### Area light
la fonte di __luce ad area__ è un intera area che emette luce. Questa puo essere definita dalla geometria della sorgente e a seconda dei casi da 
- [[Illuminazione - Radiometria#Radiant flux|Flux]]: se è uniforme sia spazialmente  che per direzione
- [[Illuminazione - Radiometria#Irradiance e exitance|Funzione di exitance]]: se varia spazialmente ma è uniforme per  direzione
- [[Illuminazione - Radiometria#Radianza|Funzione di irradianza]]: se varia sia spazialmente che per direzione
 
 
_sia_
- $\omega_p$ La direzione dalla fonte di luce alla superficie riflettente 
- $L(p,\omega_p)$ la radianza dal punto $p$ verso la superficie riflettente  
- $dA$ l aria differenziale intorno al punto $p$

_allora_ l irradianza totale proveniente dalla lice ad area è $$L_r(\omega _r)= \int_{p \in  A}  dL_r(\omega_r)  =\int_{p \in  A} f_r(\omega_p,\omega_r)L_p(w_p)\cfrac{\cos \theta \cos \theta_p}{r^2_p} dA_p   $$
per per [[Superfice lambertiana|superfici labertiane]] diventa  $$L_r(\omega _r)= \cfrac{\rho}{\pi}L_p\int_{p \in  A}\cfrac{\cos \theta \cos \theta_p}{r^2_p} dA_p   $$


![[IMG_1121 1 1.jpeg]]


##### Spotlight

 per la spotlight vale $$f_s=
\begin{cases}
1 & \alpha <\theta_{\text{inner}} \\
\cos(\alpha-\theta_{\text{inner}})^n &\theta_{\text{inner}}<\alpha<\theta_{\text{outer}}  \\
0 & \alpha>\theta_{\text{outer}}
\end{cases}$$
 ![[Pasted image 20240307185042.png]]
![[Pasted image 20240301003151.png]]