---
type: nota
course: Computer grafica
topic: 
tags:
  - CG
Parent MOC: "[[Computer Grafica (CG)]]"
---


# Trasformazioni Geometriche affini
---
#### Elementri geometrici
gli elementi del _dominio_ della [[Computer Grafica (CG)|computer grafica]] sono
- _scalari_: sono _monodimensionali_ e rappresentano la _magnituto_ di qualcosa (temperatura, velocita)
-  _punti_: rasentano _posizioni_ nello spazio 
- _vettori_: rappresentano una _direzione_,
	- I _vettori_ si usano anche per descrivere gli spostamenti  che hanno associato una _direzione_ e una _magnitudo_, che rappresentano rispettivamente la linea su cui avviene lo spostamento e il “_di quanto_” avviene lo spostamento.

_punti_ e _vettori_ sono multi dimensionali ma la _dimensione_ dipende dalla dimensione in cui stiamo lavorando.

![[IMG_0728.jpeg]]

##### Operazioni
Sugli _elementi geometrici_ si  possono eseguire le seguenti operazioni
_somma punto-vettore_: restituisce una nuovo _punto_ che rappresenta la nuova posizione dopo lo spostamento partendo dal punto iniziale. e quindi si ha $$\boldsymbol{p}=\boldsymbol{p_{1}}+\boldsymbol{\mathit{v}} $$

_somma vettore-vettore_: restituisce un vettore e rappresenta due spostamenti consecutivi. e quindi $$\boldsymbol{\mathit{v}}=\boldsymbol{\mathit{v}_{1}}+\boldsymbol{\mathit{v}_{2}}$$
_sotrazione punto-punto_:  restituisce un vettore e rappresenta lo spostamento necessari da punto $\boldsymbol{p_1}$ per raggiungere il punto $\boldsymbol{p_2}$. la _magnitudo_ di questo vettore e quindi $$\boldsymbol{\mathit{v}}=\boldsymbol{p_{1}}- \boldsymbol{p_{2}}$$
_moltipliczione scalare-vettore_ restituisce un _vettore_ partendo dal vettore $v_{1}$ ne coserva la _direzione_ ma ne cambia la _magnitudo_ moltiplicandola per un fattore. quindi $$\boldsymbol{\mathit{v}}=a\boldsymbol{\mathit{v}}_{1}$$


#### Operazioni su oggetti
solitamente un computer grafica le operazioni si intendono su tutto i vertici di un dato _oggetto_ ma le operazioni qui elencate sono sul singolo vertice ma vengono eseguite su tutto l oggetto.
##### Traslazioni
la _traslazione_ è una [[Trasformazioni affini|trasformazione affina]] ed è l  _operazione_ di spostare nello spazio un _vertice_.
solitamente vengono definite come $$T_{v}(\boldsymbol{p})=\boldsymbol{p}+\mathit{
\boldsymbol{v}}$$
##### Scaling
per _Scaling_ è una [[Trasformazioni affini|trasformazione affine]] ed è ed è l _operazine_ di cambiare la dimensione complessiva del oggetto mantenendone le proporzioni questo è fatto con $$S_{(s_x,s_y)}(\boldsymbol{p}) = \begin{bmatrix}
s_x p_{x} \\
s_y p_{y}
\end{bmatrix}$$
questa operazione è detta _uniforme_ se $s_x=s_y$ altrimenti è detta _non uniforme_ 
con una trasformazione uniforme si _mantengono_ le proporzioni mentre un uno _non uniforme_ no 
![[IMG_0729.jpeg]]
##### Rotazioni
una _rotazione_ è una [[Trasformazioni affini|trasformazione affine]] ed è la rotazione un punto nello spazio seguendo la formula $$R_{\alpha}(\boldsymbol{p})=\begin{bmatrix}
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
lo _shearing_ è una [[Trasformazioni affini|trasformazione affine]] ed è  per cui i punti vengono _scalati_ in una dimensione in modo _proporzionale_ ad una altra _dimensione_ 

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

siccome le operazioni di _scaling_ e _rotazioni_ sono  _[[Combinazioni Lineari|combinazioni lineari]]_  delle componenti del _punto_$$\begin{array}{}
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
usando le _[[Coordinate omogenee|coordinate omogeene]]_ abbiamo che possiamo rappresentate tutte le _trasformazioni_ (_traslazione_,_scaling_,_rotazioni_,_shearing_) con una sola [[Matrice|matrice]] detta _matrice di [[Trasformazioni affini|trasformazione affine]]_ ed è della forma  $$\begin{bmatrix}
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
