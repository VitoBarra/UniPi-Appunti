---
Course: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Interpolazione di Rotazioni
---
ci si pone il problema di _interpolare_ tra due [[Rotazioni in 3D|rotazioni 3D]] ovvero si voglio approssimare tutte le _rotazioni_ tra due _rotazioni note_ 
Questo permette di creare un animazione che passa da una rotazione ad un altra.

un altro modo per vedere l _interpolazione_ tra 2 _rotazioni_ e vederla come _interpolazione_ tra 2 [[Frames|frame]] siccome dal punto di vista matematico sono equivalenti.

#### Interpolazione con Matrici di rotazione
l [[Interpolazione Lineare|Interpolazione lineare]] __non__ funziona per le [[Rotazioni in 3D#Rotazioni introno ad un asse|matrici di rotazione]] infatti avremmo la formula $$R_{t}=R_{0}(1-t)+R_{1}t$$infatti $$
\begin{align}
0.5I+0.5R_{z}\left( \cfrac{\pi}{2} \right) & =  0.5\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1 
\end{bmatrix}+0.5\begin{bmatrix}
0 & 1 & 0 \\
-1 & 0 & 0 \\
0 & 0 & 1
\end{bmatrix} \\
 & =  \begin{bmatrix}
0.5 & 0.5 & 0 \\
-0.5 & 0.5 & 0 \\
 0 & 0 & 1
\end{bmatrix}
\end{align}
$$dove la matrice finale non è una _matrice di rotazione_ e quindi non funziona


#### interpolazione Angolo-asse
le [[Rotazioni in 3D#Rotazione asse-angolo|rotazione angolo-asse]] possono essere  [[Interpolazione Lineare|linearmente interpolate]] usando le seguenti formule 
$$\begin{array}{}
\theta_{t}=\theta_{0}(1-t)+\theta_{1}t \\
r_{t}=\cfrac{r_{0}(1-t)+r_{1}t}{\|r_{0}(1-t)+r_{1}t\|}
\end{array}$$
ma la velocita di interpolazione non è costante, è più _lenta_ al inizio e alla fine e più _veloce_ nel mezzo 
![[IMG_0766.jpeg]]
	Intervalli di lunghezza uguale sottondono angoli diversi

##### Interpolazione Lineare sferica
per l una velocità costante nel interpolazione si una l _interpolazione lineare sferica_ tra due vettori $\boldsymbol{e}_{0}$ e $\boldsymbol{e}_{1}$

1. [[Algoritmi per trovare basi|costruisce]] una [[Base di uno spazio vettoriale|base]] [[Base Ortogonale e Ortonormale|ortonormale]] da $\boldsymbol{e}_{0}$ e $\boldsymbol{e}_{1}$ 
2.  si interpola l angolo tra i due vettori
$$\boldsymbol{e}^{p}_{1}=\frac{\boldsymbol{e}_{1}-(\boldsymbol{e}_{0}\cdot \boldsymbol{e}_{1})\boldsymbol{e}_{0}}{\|\boldsymbol{e}_{1}-(\boldsymbol{e}_{0}\cdot \boldsymbol{e}_{1})\boldsymbol{e}_{0}\|}$$ e la formuala di interpolazione è $$\boldsymbol{e}(t)=\cos(t\psi)\boldsymbol{e}_{0}+\sin(t\psi)\boldsymbol{e}^{p}_{1}$$
![[IMG_0795.jpeg]]


##### Slerp: Shperical linear interpolation
dove
- $R=\{r_{0},r_{1},0 \}$ è un [[Frames|frames]] 
il _vettore_ $\boldsymbol{r}(t)$ è espresso in _termini_ di $R$
ed è definito come	$$r(t)=0+\omega_{0}(t)r_{0}+\omega_1(t)r_{1}$$
dove $$
\begin{array}{}
\psi=\arccos(r_{0}\cdot r_{1})=\alpha(t)+\beta(t) \\
\sin \psi=\cfrac{ \sin \alpha(t)}{\omega_1} \implies \omega_{1}=\cfrac{\sin \beta(t)}{\sin  \psi}  \\
\sin \phi = \cfrac{\sin  \beta(t)}{\omega_{0}}\implies \omega_{0}=\cfrac{\sin \beta(t)}{\sin \psi} \\
\alpha(t)=t\psi   \\
\beta(t)=(1-t)\psi \\
r(t)=\cfrac{\sin t\psi}{\sin \psi}r_{0}+\cfrac{\sin(1-t)\psi}{\sin  \psi}
\end{array}
$$
questa formula _finale_ funziona in qualsiasi dimensione e quindi si puo usare per _interpolare_ tra [[Quaternioni|quaternioni unitari]]  
$$\begin{array}{}
\psi=\arccos(q_0\cdot q_1) \\
\boldsymbol{q}(t)=\cfrac{\sin t\psi }{\sin  \psi}\boldsymbol{q}_{0}+\cfrac{\sin(1-t)\psi}{\sin \psi}\boldsymbol{q}_{1}
\end{array}$$
da una rotazione a veloce uniforme su i quaternioni