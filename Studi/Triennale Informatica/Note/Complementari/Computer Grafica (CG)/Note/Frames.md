---
Course: "[[Computer Grafica (CG)]]"
Subject: Computer Grafica
Area: 
Topic: 
SubTopic: 
tags:
  - CG
---

# Frames
---
un _frame_ $F=\{O, \boldsymbol{\mathit{v}}_{1},\dots,\boldsymbol{\mathit{v}_{n}}\}$ in $n$-dimensionale è _caratterizzato_ da 
- $n$ _vettori_ che rappresentano gli _assi_
- un _punto_ detto _origine_ del frame
sono delle [[Base di uno spazio vettoriale|basi]]

I _punti_ e i _vettori_ che usiamo sono espressi _relativamente_ ad un _frame_, ovvero non esiste una posizione assoluta e per rappresentare questi oggetti si parte dal frame  
![[IMG_0753.jpeg]]

#### Frame canonico 2D
il _frame_ di partenza è il _frame canonico 2D_ $F=\{O,\boldsymbol{\mathit{u}},\boldsymbol{\mathit{y}}\}$ con  
- gli _assi_ $v=\begin{bmatrix}1&0&0\end{bmatrix}^{T}$ e  $u=\begin{bmatrix}0&1&0\end{bmatrix}^{T}$  
-  l _origine_ $O=\begin{bmatrix}0&0&1\end{bmatrix}^{T}$ 
e sono espressi in [[Coordinate omogenee|coordinate omegeene]] per permettere l utilizzo di moltiplicazione matriciale per le [[Trasformazioni Geometriche affini|trasformazioni geometriche]].
Questo _frame_ è una [[Base Ortogonale e Ortonormale|base ortonormale]] 
![[IMG_0750.jpeg]]

##### Cambio di frame
per convertire un punto espresso in termini di un _frame_ $F_{0}$ in un altro espresso in termini un _frame_ $F_{1}$

partendo da una _generico_ $F_{0}$ _non canonico_ ad il _frame canonico_$$\boldsymbol{p}=O_{0}+\boldsymbol{p}_{0_{x}}\boldsymbol{\mathit{u}}_{0}+\boldsymbol{p}_{1_{y}}\boldsymbol{\mathit{v}}_{0} $$_geometricamente_ stiamo prima _traslando_ il punto verso l origine $O_{0}$ e poi _transliamo_ di $\boldsymbol{p}_{0_{x}}$ lungo l asse $\boldsymbol{\mathit{u}}_{0}$ e poi di  $\boldsymbol{p}_{0_{y}}$ lungo l asse $\boldsymbol{\mathit{v}}_{0}$  ottenendo così un punto espresso in _coordinate canoniche_
![[IMG_0752.jpeg]]
questa operazione puo essere anche scritta sotto forma di matrice di _[[Trasformazioni Geometriche affini|rototraslazione]]_  $M_{1}$ come $$\boldsymbol{p}=\underbrace{ \begin{bmatrix}
v_{0_{x}}  & u_{0_{x}}  & O_{0_{x}} \\
v_{0_{y}}  & u_{0_{y}}  & O_{0_{y}} \\
0 & 0 & 1
\end{bmatrix} }_{ M_{0} }\boldsymbol{p_{0}}$$ed essendo la prima _sottomatrice_ $2\times 2$ una matrice di _rotazione_ si puo scrivere come $$\boldsymbol{p}= \begin{bmatrix}
R_{0}  & O_0 \\
0 & 1
\end{bmatrix}\boldsymbol{p_{0}}$$

Da qui notiamo che presi due punto $p_{1}$ $p_{1}$ espressi in  nei _frame_ $F_{0}$ e $F_{1}$  che mappano allo stesso punto nel _frame canonico_ vale e equazione $$\boldsymbol{p}=\underbrace{ \begin{bmatrix}
R_{0}  & O_0 \\
0 & 1
\end{bmatrix}}_{M_{0}}
\boldsymbol{p_{0}}=
\underbrace{ \begin{bmatrix}
R_{1}  & O_1 \\
0 & 1
\end{bmatrix} }_{ M_{1} }
\boldsymbol{p_{1}}$$
e quindi moltiplicando entrambi i lati per la matrice [[Matrice inversa|inversa]] $M_{1}^{-1}$ si ottiene $$ M_{1}^{-1}M_{0}
\boldsymbol{p_{0}}=
\boldsymbol{p_{1}}$$ che significa che usare la matrice $M_{1}^{-1}M_{0}$ per passare dal _frame_ $F_{0}$ al _frame_ $F_{1}$ 

Essendo le metrici matrici di [[Trasformazioni Geometriche affini|rototraslazione]] stiamo lavorando con [[Trasformazioni affini|trasformazioni affini]] e ciò rende facile calcolare l inversa _[[Matrice inversa|inversa]]_ $M_{1}^{-1}$  

#### Frame generici
il _frame_ possono anche non essere [[Vettori Ortogonali|ortonormali]]  infatti possiamo vedere ogni [[Trasformazioni affini|trasformazione affine]] come un _cambio di frame_, dal punto di vista matematico è la stessa cosa del applicare la trasformazione ma la trasformazione è piu facile da immaginare.

#### Frame gerachici
piu _frame_ posso essere ordinati in modo gerarchico in questo modo siamo in grado di descrivere la scena in termini di altri frame, ad esempio ogni _frame_ puo essere un oggetto o una parte di un oggetto.
i _frame_ possono essere rappresentati con un [[Grafi - Matematica|grafo]] dove i nodi sono i _frame_ e gli archi sono le _operazioni_ per passare da un frame ad un altro 
![[IMG_0754.jpeg]]
con questa organizzazione applicare un trasformazione ad un _frame_ la applica anche a tutti i _frame_ sottostanti nella gerarchia, il che può tornare molto comodo nella pratica
#### Frame in 3 dimensioni
tutto ciò che si puo fare in $2D$  si può fare anche in $3D$ basta aggiungere un terzo asse $z$ 

ci sono due modi per farlo regola della _mano destra_ e della _mano sinistra_
![[IMG_0755.jpeg]]
la regola della _mano destra_ è solitamente più scelta

tutte le trasformazioni funzionano facilmente anche in $3D$ tranne per le rotazioni che hanno bisogno di più accortezza e quindi esistono dei meccanismi apposta per le [[Rotazioni in 3D|Rotazioni in 3D]]
