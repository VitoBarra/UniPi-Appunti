---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic: "[[Illuminazione - Modelli avanzati]]"
---

# Illuminazione - Modello Oren-Nayar
---
il modello di __illuminazione  Oren-Nayar__ è un modello per di [[Illuminazione nella Computer Grafica|illuminazione locale]] basato sulla fisica e quindi deve rispettare la [[Legge di conservazione del energia|legge di conservazione dell energia]]. 

Si basa sul assunzione che le superfici siano fatte da micro-sfacetature che si comportano come [[Superfice lambertiana|Superfici lambertiane perfetta]]
![[Pasted image 20240305224939.png]]
![[Pasted image 20240305224956.png]]
Questo modello oltre alle superfici lambertiane smooth riesce a catturare anche quelle "rough" ovvero quelle esibiscono il fenomeno di retro-Reflection, ovvero una parte della luce viene emessa direttamente nella direzione della fonte di luce.

un superfice piu è rough piu appare piatta
![[Pasted image 20240305224846.png]]

Il modello è definito come
_sia_
- $\alpha$ è l [[Angoli|angolo]] tra la [[Normale di una superfice|normale]] e la direzione della luce incidente $\alpha = \arccos(\boldsymbol{N}\cdot \boldsymbol{L})$
- $\beta$ è l [[Angoli|angolo]] tra la [[Normale di una superfice|normale]] e la direzione di vista $\beta = \arccos(\boldsymbol{N}\cdot \boldsymbol{V})$
- $A$ e $B$ sono parametri per definire la roughness
- $C$ è l angolo di azimuthal tra  la direzione di vista $V$ e direzione della luce  $L$
- $\rho$  è la [[Variabili Aleatorie Notevoli - Gaussiane|distribuzione gaussiana]] con media a 0
allora il modello è definito come $$L_r=\rho L_p(\boldsymbol{N} \cdot \boldsymbol{L})(A+BC\sin (\alpha) \tan (\beta))$$
![[Pasted image 20240305225016.png]]
dove $$\begin{array}{}
A = 1.0 -0.5\cfrac{\sigma^2}{\sigma^2+0.33} & 	B=0.45 \cfrac{\sigma^2}{\sigma^2+0.09}
\end{array}$$e per calcolare $C$ si calcola prima la proiezione sul piano tangente alla superfice del vettore di direzione  di vista $V'$ e  della direzione di luce $L'$  $$\begin{align}
  C & =  \cos(\phi_V-\phi_L)=(L'\cdot V') \\
  L' & =  \boldsymbol{L}-(\boldsymbol{L}\cdot \boldsymbol{N})\boldsymbol{N} \\
  V' & =  \boldsymbol{V}-(\boldsymbol{V}\cdot \boldsymbol{N})\boldsymbol{N}
\end{align}$$