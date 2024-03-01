---
Subject: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Trasformazioni Geometriche affini
---
le __trasformazioni geometriche__ sono [[Funzioni|funzioni]] su [[Computer grafica - Primitive algebriche|primitive algebriche]] che mappano _[[Computer grafica - Primitive algebriche|punti]] in punti_ e _[[Computer grafica - Primitive algebriche|vettori]] in vettori_ e quando si parla _trasformare_ un _oggetto_ si intende su tutti i punti e i vettori del _oggetto_ 

le operazioni qui elencate sono fatte sul singolo vertice ma l effetto complessivo di applicare la trasformazione a tutti i vertici del oggetto e quello di aver applicato la trasformazione al oggetto stesso

##### Traslazioni
la _traslazione_ è una [[Applicazioni affini|trasformazione affina]] ed è l  _operazione_ di spostare nello spazio un _vertice_.
solitamente vengono definite come $$T_{v}(\boldsymbol{p})=\boldsymbol{p}+\mathit{
\boldsymbol{v}}$$
##### Scaling
per _Scaling_ è una [[Applicazioni affini|trasformazione affine]] ed è ed è l _operazione_ di cambiare la dimensione complessiva del oggetto mantenendone le proporzioni questo è fatto con $$S_{(s_x,s_y)}(\boldsymbol{p}) = \begin{bmatrix}
s_x p_{x} \\
s_y p_{y}
\end{bmatrix}$$
questa operazione puo essere
- _uniforme_ se $s_x=s_y$ (_isotropic_)
- _non uniforme_ se $s_{x} \neq s_{y}$ (_antisotropic_)
con una trasformazione _uniforme_ si _mantengono_ le proporzioni mentre un uno _non uniforme_ no 
![[IMG_0729.jpeg]]
##### Rotazioni
una _rotazione_ è una [[Applicazioni affini|trasformazione affine]] ed è la rotazione un punto nello spazio seguendo la formula $$R_{\alpha}(\boldsymbol{p})=\begin{bmatrix}
p_{x}\cos(\alpha)-p_{y}\sin (\alpha) \\
p_{x}\sin(\alpha)+p_{y} \cos(\alpha)
\end{bmatrix}$$ e questa formula puo essere _dimostrata_ seguendo i passaggi.
_sia_ $\boldsymbol{p}$ un _punto_ $\rho$ la _distanza_ del _punto_ dal origine e $\beta$ l angolo del _punto_
_allora_ il _punto_  può essere espresso come  $$\boldsymbol{p}=\begin{bmatrix}
\rho \cos \beta \\
\rho \sin \beta
\end{bmatrix}$$
ruotando il punto di un angolo $\alpha$ otteniamo il _punto_ $$\boldsymbol{p}’= \begin{bmatrix}
\rho \cos (\beta+\alpha) \\
\rho \sin (\beta+\alpha)
\end{bmatrix}$$ e usando le [[Formule Trigronometriche|forumule tringonometriche]] si ottiene che $$\begin{matrix}
p_{x}’ & = & \rho \cos(\beta+\alpha) \\
 & = & \rho \cos \beta \cos \alpha-\rho \sin \beta \sin \alpha \\
 & = &p_{x}\cos \alpha-p_{y}\sin \alpha 
\end{matrix}
$$
e $$\begin{matrix}
p_{y}’ & = & \rho \sin(\beta+\alpha) \\
& = &\rho \sin \beta \cos \alpha +\rho \cos \beta \sin \alpha\\
& = &p_{y}\cos \alpha + p_{x}\sin \alpha 
\end{matrix}
$$
concludendo cosi la dimostrazione
![[IMG_0730.jpeg]]

##### Shearing
lo _shearing_ è una [[Applicazioni affini|trasformazione affine]] ed è  per cui i punti vengono _scalati_ in una dimensione in modo _proporzionale_ ad una altra _dimensione_ 

$$Sh_{(h,k)}(\boldsymbol{p})=\begin{bmatrix}
1 & k  \\
h & 1  \\
\end{bmatrix}\boldsymbol{p}=\begin{bmatrix}p_{x}+kp_{y}\\h p_{x}+p_{y}
\end{bmatrix}$$

![[IMG_0733.jpeg]]

>[!tip]
> lo sharing puo essere ottenuto anche da uno _scaling non uniforme_ e da una _rotazione_ 

#### Notazione matrice
un situazione molto comune e quando si vogliono applicare consecutivamente _rotazioni_, _traslazioni_ e _scaling_, ciò diventa _praticamente_ ingestibile e per risolvere questo problema si utilizzano le [[Matrice|matrici]].

siccome le operazioni di _scaling_ e _rotazioni_ sono _[[Combinazioni Lineari|combinazioni lineari]]_ delle componenti del _punto_$$\begin{array}{}
p_{x}’  & =a_{xx}p_{x}+a_{xy}p_{x}\\
p_{y}’ & =a_{yx}p_{y}+a_{yy}p_{y}
\end{array}$$possiamo riscrivere le operazioni in modo piu compatto usando una matrice  della forma $$\boldsymbol{p}’ = \begin{bmatrix}
a_{xx} + a_{xy} \\
a_{xy} + a_{yy}
\end{bmatrix}\boldsymbol{p}$$e possiamo poi specializzarla per attenere le _operazioni_ prima descritte 
_matrice di scaling_
	la matrice scaling è della forma  come $$T_{(s_{x},s_{y})}(\boldsymbol{p})=
	\begin{bmatrix} s_{x}  &  0  \\
    0  & s_{y} \\
    \end{bmatrix} 
    \begin{bmatrix}
    p_{x} \\ p_{y}
    \end{bmatrix}$$ed è un [[Applicazioni Lineari|applicazione lineare]]
_Matrice di rotazone_ :
	matrice di rotazione è della forma $$R_{\alpha}(\boldsymbol{p})=\begin{bmatrix}\cos   \alpha  & - \sin \alpha \\
    \sin \alpha & +\cos \alpha
\end{bmatrix}\begin{bmatrix}
p_{x}\\p_{y}
\end{bmatrix}$$ed è un [[Applicazioni Lineari|applicazione lineare]]

 non essendo una _[[Combinazioni Lineari|combinazione lineare]]_ la  _traslazione_ non puo essere espressa nello stesso modo.
 
#### Matrici Roto-traslazioni
usando le _[[Coordinate omogenee|coordinate omogenee]]_ abbiamo che possiamo rappresentate tutte le _trasformazioni_ (_traslazione_,_scaling_,_rotazioni_,_shearing_) con una sola [[Matrice|matrice]] detta _matrice di [[Applicazioni affini|trasformazione affine]]_ ed è della forma  $$\begin{bmatrix}
a_{xx} & a_{xy} & v_{x} \\
a_{yx}  & a_{yy}& v_{y}  \\
0 & 0 & 1  
\end{bmatrix}$$
dove la prima matrice $2\times 2$ e rappresenta la parte la parte di  _rotazione_ e _scaling_ e l ultima colonna rappresenta la parte di _traslazione_ e possiamo riscriverla  per comodità come  $$\begin{bmatrix}
	R  & v \\
    0 & 1
\end{bmatrix}$$
_applicando_ la _matrice di roto-traslazione_ otteniamo  $$
\begin{array}{}
\begin{bmatrix}
a_{xx} & a_{xy} & v_{x} \\
a_{yx}  & a_{yy}& v_{y}  \\
0  & 0 & 1  
\end{bmatrix}\begin{bmatrix}
p_{x}\\p_{y}\\1
\end{bmatrix} & =  \\
\begin{bmatrix}
a_{xx}p_{x} + a_{xy}p_{y} + v_{x} \\
a_{yx}p_{x} + a_{yy}p_{y} + v_{y}  \\
1
\end{bmatrix}
 & =\\ \begin{bmatrix}
\begin{bmatrix}
a_{xx} & a_{xy} \\
 a_{yx} & a_{yy} 
\end{bmatrix}\boldsymbol{p}+\boldsymbol{\mathit{v}} \\
1 
\end{bmatrix}=  \\
 \begin{bmatrix}
R\boldsymbol{p}+\boldsymbol{\mathit{v}} \\
1 
\end{bmatrix}
\end{array}
$$questa matrice esprime quindi correttamente tutte le _trasformazioni geometriche_ che ci interessano nella _computer grafica_


##### Teoria
Le [[Trasformazioni Geometriche affini|trasformazioni]] di _rotazione_ e _traslazione_ sono dette _trasformazioni rigide_ perche muovono l oggetto preservando la lunghezza delle linee e gli angolo, lo _scaling_ se non è _unifome_ non è una trasformazione rigida ma preserva solo gli angoli e la _paralerità_ delle linee

