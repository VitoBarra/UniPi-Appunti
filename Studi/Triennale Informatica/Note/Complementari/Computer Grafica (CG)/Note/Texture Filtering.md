---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Texture Mapping]]"
SubTopic:
---

# Texture Filtering
---
per passare dal [[Pipeline di Rasterizazione|frammento]] che mantiene delle coordinate in __Texture space__ ad un [[Rappresentazione di colori|colore]] corrispondente a quello sulla [[Texture|texture]] per via delle coordinate discrete dei __texel__ possono succedere due cose
- _Magnification_: Il [[Texture Mapping con Proiezione Prospettica|pixel proiettato]] è piu piccolo di un __Texel__ 
- _Minification_: il [[Texture Mapping con Proiezione Prospettica|pixel proiettato]] è piu grande di un __Texel__
![[Pasted image 20240301054347.png]]
in entrambi i casi vanno attuate delle strategie per per selezionare il colore giusto

#### Magnification
in caso di __magnification__ si possono attuare due strategie.

__Nearest neighbot filtering__: è la soluzione piu veloce si prende il colore del __texel__  con __centro__ piu vicino. 
Questo pero porta al fatto che piu la texture viene ingrandita, ovvero piu la proiezione del pixel sulla texture è piccolo, piu si vedranno i singoli __texel__ dando dei risultati mediocri 
![[Pasted image 20240301055241.png]]
una altra strategia è
__interpolazione bi-lineare__: si prendono i 4 __texel__ piu vicini e si [[Interpolazione Lineare|interpola linearmente]] tra i 4 centri con la formula: 
_sia_
- $c_{ij}=p_{ij}$ il valore di un centro di un __texel__
- $(u,v)$ le coordinate in _texture space_
allora $$
\begin{align}{}
c  =&  [c_{00}(1-u)+c_{10}u](1-v) +\\
    &  [c_{01}(1-u)+c_{11}]v
\end{align}
$$
![[Pasted image 20240301061120.png]]

alternativamente puo essere visto come un quadrato grande quanto un __texel__ centrato nelle coordinate $(u,v)$ e pesate con la la porzione dei texel coperti da quel quadrato, questo utilizzando la formula
$$c=(1-u)(1-v)\ c_{00}+(1-u)v\ c_{01}+(1-v)\ c_{10}+uv\ c_{11}$$
![[Pasted image 20240301061343.png]]

![[Pasted image 20240301061611.png]]


#### Minification
in caso di __minification__ le strategie viste per il __magnification__ non funzionano.
![[Pasted image 20240301061905.png]]
si utilizza una strategia chiamata 

__MipMapping__:
_mip_ ovvero multum in pravo, tanto con uno, si riferisce al fatto di generare molti livelli della stessa texture e selezinale il livello a seconda del numero di __texel__ che il pixel compre.

sia $n \times n$ la risoluzione di una [[Texture|texture]] si costruiscono $\log_2n$ livelli di texture dimezzando iterativamente la risoluzione fino ad arrivare a $1 \times 1$.
per decidere il colore  pixel nelle nuove texture si fa una media dei 4 pixel vicini.
In questo modo si costruisce una struttura gerarchia a livelli chiamata __Piramide MIpmapp__ e per costrurie l intera gerarchia $n$ deve esser una potenza di $2$
![[Pasted image 20240301062823.png]]
bisogna selezionare  il livello della __pirimide mipmap__ basandosi sul numero di texel che un pixel copre 

per scegliere il livello si potrebbero proiettare i 4 angoli di un pixel sul il __texture space__ e poi si potrebbe calcoalare l area del poligono associato ed utilizzare quel area per calcolare quanti texel sono coperto, questo è troppo costoso dal punto di vista computazionale e quindi si puo aprossimare questa cosa.
_sia_
- $(x,y)$ le coordinate in __screen space__
- $(u,v)$ la coordinate della proiezione di $(x,y)$ in __texture space__
allora si puo calcolare $$\rho=max\left(\left\| \begin{bmatrix}
\cfrac{\partial u}{\partial x} \\\cfrac{\partial v}{\partial x}
\end{bmatrix} \right\| ,
\left\| \begin{bmatrix}
\cfrac{\partial u}{\partial y} \\\cfrac{\partial v}{\partial y}
\end{bmatrix} \right\|\right)$$ e il livello è calcolat come $$L=\log_2(\rho)$$
mentre $$
\begin{array}{}

\begin{bmatrix}
\cfrac{\partial u}{\partial x} \\\cfrac{\partial v}{\partial x}
\end{bmatrix} =
\begin{bmatrix}
\cfrac{u(x+\Delta x,y)-u(x,y)}{\Delta x} \\ \cfrac{v(x+\Delta x,y)-v(x,y)}{\Delta x}
\end{bmatrix} \\
\begin{bmatrix}
\cfrac{\partial u}{\partial y} \\\cfrac{\partial v}{\partial y}
\end{bmatrix} =
\begin{bmatrix}
\cfrac{u(x,y+\Delta y)-u(x,y)}{\Delta y} \\ \cfrac{v(x,y+\Delta y)-v(x,y)}{\Delta y}
\end{bmatrix}
\end{array}
$$
e queste rappresentano il cambiamento in texture space rispetto al cambiamento in screen space
![[Pasted image 20240301064032.png]]
![[Pasted image 20240301061741.png]]