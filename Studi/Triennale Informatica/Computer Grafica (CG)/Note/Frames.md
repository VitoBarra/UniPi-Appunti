---
Subject: "[[Computer Grafica (CG)]]"
topic: 
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
e sono espressi in [[Coordinate omogenee|coordinate omegeene]] per permettere l utilizzo di moltiplicazione matriciale per le [[Trasformazioni Lineari Geometriche|trasformazioni geometriche]].
Questo _frame_ è una [[Base Ortogonale e Ortonormale|base ortonormale]] 
![[IMG_0750.jpeg]]

##### Cambio di frame
Si presenta la necessita di cambiare il __frame__ di riferimento e quindi si procede come
sia
- $F_{0}=\{ \boldsymbol{O},\boldsymbol{u},\boldsymbol{v} \}$ un __frame__ non __canonico__
- $\boldsymbol{p}_0=(p_x,p_y)$ un punto espresso in $F_0$
- $F_c$  il __frame canonico__
allora per passare dal punto $\boldsymbol{p}_0$ in $F_0$ ad un punto $\boldsymbol{p}$ espresso in $F_c$ si usa la formula $$\boldsymbol{p}=\boldsymbol{O}+\boldsymbol{p}_x \boldsymbol{u}+\boldsymbol{p}_y \boldsymbol{v} $$_geometricamente_ stiamo prima _traslando_ il punto verso l origine $O$ e poi _trasliamo_ di $\boldsymbol{p}_x$ lungo l asse $\boldsymbol{u}$ e i di  $\boldsymbol{p}_y$ lungo l asse $\boldsymbol{v}$ ottenendo così un punto espresso in __coordinate canoniche__
![[IMG_0752.jpeg]]
questa operazione puo essere anche scritta sotto forma di matrice di _[[Trasformazioni Lineari Geometriche|rototraslazione]]_  $M_{1}$ come $$\boldsymbol{p}=\underbrace{ \begin{bmatrix}
v_x  & u_x  & O_x \\
v_y  & u_y  & O_y \\
0 & 0 & 1
\end{bmatrix} }_{ M_{0} }\boldsymbol{p_{0}}$$ed essendo la prima _sottomatrice_ $2\times 2$ una matrice di _rotazione_ si puo scrivere come $$\boldsymbol{p}= \begin{bmatrix}
R_{0}  & O_0 \\
0 & 1
\end{bmatrix}\boldsymbol{p_{0}}$$


Possiamo utilizzare questa trasformazione per passare da un __generico frame__ $F_0$ a un altro __generico frame__ $F_1$ infatti abbiamo che  
siano 
- $\boldsymbol{p}$ un punto espresso nel __frame canonico__ $F_c$
- $p_{0}$ il punto $\boldsymbol{p}$ espresso nel __frame__ $F_0$
- $p_{1}$ il punto $\boldsymbol{p}$ espresso nel __frame__ $F_{1}$ 
allora si ha che applicando la formula del cambio di frame entrambi mappano a $\boldsymbol{p}$$$\boldsymbol{p}=\underbrace{ \begin{bmatrix}
R_{0}  & O_0 \\
0 & 1
\end{bmatrix}}_{M_{0}}
\boldsymbol{p_{0}}=
\underbrace{ \begin{bmatrix}
R_{1}  & O_1 \\
0 & 1
\end{bmatrix} }_{ M_{1} }
\boldsymbol{p_{1}}$$e quindi moltiplicando entrambi i lati per la matrice [[Matrice inversa|inversa]] $M_{1}^{-1}$ si ottiene $$ M_{1}^{-1}M_{0}
\boldsymbol{p_{0}}=
\boldsymbol{p_{1}}$$ che significa che usare la matrice $M_{1}^{-1}M_{0}$ per passare dal _frame_ $F_{0}$ al _frame_ $F_{1}$ questa formula infatti corrisponde a passare da $F_0$ a $F_c$  e poi da $F_c$ a $F_1$
![[Pasted image 20240318025535.png]]


Essendo le matrici di [[Trasformazioni Lineari Geometriche|rototraslazione]] delle [[Applicazioni affini|trasformazioni affini]] abbiamo che si puo calcolare facilmente la _[[Matrice inversa|matrice inversa]]_ $M_{1}^{-1}$  

#### Frame non ortogonali 
il _frame_ possono anche non essere [[Vettori Ortogonali|ortonormali]]  infatti possiamo vedere ogni [[Applicazioni affini|trasformazione affine]] come un _cambio di frame_, dal punto di vista matematico è la stessa cosa del applicare la trasformazione ma la trasformazione è piu facile da immaginare.

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
