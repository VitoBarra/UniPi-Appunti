---
Course: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Rotazioni in 3D
---
Le rotazioni in 3D sono [[Applicazioni affini|Applicazioni affini]] e un estensione delle [[Trasformazioni Lineari Geometriche|rotazioni]] geometriche in 2D  Infatti possiamo vedere le _rotazioni 2D_ come una rotazione su di un piano [[Vettori Ortogonali|ortogonale]] al asse $z$ e passane per il _punto da ruotare_ e al _origine_, ottenendo cosi la  _rotazione 3D_ attorno al asse $z$ $$R_{a,z}=\begin{bmatrix}
\cos \alpha  & -\sin \alpha  & 0  & 0\\
\sin \alpha  & \cos \alpha & 0  & 0\\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}$$

In _generale_ un _rotazione 3D_ cambia solo 2 valori di posizione su 3 e il _punto ruotato_ resta sullo stesso piano [[Vettori Ortogonali|ortogonale]] al asse e passante per il punto su cui era prima della rotazione

le _Rotazioni in 3D_ sono _definite_ rispetto ad un _Asse di rotazione_ definito da $$r=O_{r}+t\boldsymbol{d_{ir}}\ \ \ t\in (+\infty,-\infty)$$ dove per le applicazioni pratiche il punto $O_{r}=[0,0,0,1]^{T}$ è l _origine canonica_, ovvero gli assi di rotazione passano sempre per l origine. Questa pero non è una limitazione siccome in caso di assi che non passano per l origine  questo puo sempre essere [[Trasformazioni Lineari Geometriche#Traslazioni|traslato]] verso _l origine_ applicare la rotazione e portato _alla posizione originale_. 

![[IMG_0762.jpeg]]
Le rotazioni sui i 3 _assi canonic_ sono:$$\begin{array}{}
R_{a,z}=\begin{bmatrix}
\cos \alpha  & -\sin \alpha  & 0  & 0\\
\sin \alpha  & \cos \alpha & 0  & 0\\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix} \\
R_{a,x}=\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & \cos \alpha  & -\sin \alpha   & 0\\
0 & \sin \alpha  & \cos \alpha   & 0\\
0 & 0 & 0 & 1
\end{bmatrix} \\
R_{a,y}=\begin{bmatrix}
\cos \alpha  & 0 & \sin \alpha  & 0  \\
0 & 1 & 0 & 0 \\
-\sin \alpha  & 0 & \cos \alpha & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
\end{array}$$
### Rotazioni introno ad un asse
si puo applicare un rotazione su generico _asse di rotazione_ $\boldsymbol{r}$ come una serie ti _trasformazione_ e  bisogna 
- _Applicare_ $F_{r}$ che fa coincidere l _asse_ $z$ al _asse_ $r$ 
- _Applicare_ la _rotazione_ $R_{\alpha,z}$
- _applicare_ $F_r^{-1}$che fa coincidere il frame al frame canonico
otteniamo quindi con la notazione a matrice
$$R_{\alpha,r}=F^{-1}_{r}R_{\alpha,z}F_{r}$$
per applicare questo metodo bisogna quindi costruire il [[Frames|frame]] $F_{r}$ 

per costruire il [[Frames|frame]] $F_{r}$ possiamo scegliere un _qualsiasi_ vettore $a$  e possiamo calcolare gli altri due _assi_ usando il [[Prodotto Vettoriale (Cross product)|Prodotto Vettoriale (Cross product)]] che genera un vettore  [[Vettori Ortogonali|ortogonale]] ad entrambi i _vettori_ che partecipano al operazione. Ricordando che vogliamo fare in modo di far coincidere $r$ con $z$ abbiamo che $z_{r}=r$ e otteniamo quindi$$\begin{array}{}
x_{r} & = & z_{r}\times a \\
y_{r} & = &  z_{r} \times x_{r}
\end{array}
$$in questo modo si ottiene il _frame_ [[Vettori Ortogonali|ortogonale]] $F_{r}$ 

la scelta di $a$ _determina_ il frame $F_{r}$, bisogna stare attendi a non scegliere un vettore $a$ [[Dipendenza Lineare|dipendente]] con l _asse_ $r$ siccome in quel caso il [[Prodotto Vettoriale (Cross product)|prodotto vettoriale]] restituirebbe il _vettore nullo_.
$a$ scegliere a caso ha [[Definizione di Probabilita|probabilita]] bassa di selezionare un vettore _dipendente_(_colineare_) con $r$ ma non zero e per via del [[Aritmetica di Macchina|algebra finita]] del calcolatore anche i vettori *__quasi__*  _colineari_ hanno lo stesso problema

Quindi si _sceglie_ il vettore _tale che_
_sia_ $i$ alla posizione della componente di $\boldsymbol{r}$ piu piccola e _diversa_ da $1$
	prendendo anche il valore $1$ essendo vettori _normalizzati_ otterremmo un $a$ colineare
_allora_ il vettore $a$ ha come $i$-esima componente 1 e 0 altrove 
 cosi facendo si selezione il vettore “_piu [[Vettori Ortogonali|ortogonale]]_ ad $\boldsymbol{r}$”

![[IMG_0773.jpeg]]
Creazione di un _frame_

##### Teoria
questo metodo utilizza un vettore $a$ che determina il [[Frames|frame]] invoca mente tra gli _infiniti_ possibili, questi puo pero essere tedioso e ci sono dei metodo che permettono di semplificare e non fare questo passaggio.

#### Rotazione asse-angolo
Questo metodo permette di trovare _geometricamente_ una formula per calcolare direttamente il punto di arrivo di una rotazione intorno ad un asse $r$

_siano_   $\boldsymbol{p}$ il punto che vogliamo _ruotare_ attorno ad un asse $r$ di un angolo $\alpha$ e sia $\boldsymbol{p}’$ il punto di arrivo della rotazione 
_sia_ $O_{F}$ il punto di _intersenzione_ tra il piano ortogonale e l asse di rotazione $r$
$\boldsymbol{p}$ e $\boldsymbol{p}’$ appartengono a quel  __piano [[Vettori Ortogonali|ortogonale]]__ al asse attorno a cui voglio ruotare  
creiamo un nuovo [[Frames|frame]] che ha per origine il punto $O_{F}$ per asse $x_{F}=\boldsymbol{p}-O_{F}$ e con il [[Prodotto Vettoriale (Cross product)|prodotto vettoriale]]  l _asse_ $y_{F}=\boldsymbol{r}\times x_{r}$

in questo grame il punto $p’$ ha coordinate $[\cos \alpha, \sin \alpha,0]^{T}$
![[IMG_0761.jpeg]]

mentre le coordinate del  _frame canonico_ sono $$
\begin{array}{}

\boldsymbol{p}’=\begin{bmatrix}  
   & O_{F_{x}}\\\boldsymbol{x}_{F}\boldsymbol{y}_{F}\boldsymbol{r} & O_{F_{y}} \\
  & O_{F_{z}}\\
0 &1 
\end{bmatrix}\begin{bmatrix}
\cos \alpha \\
\sin \alpha \\
0 \\1
\end{bmatrix}= \\ \\
\cos \alpha \boldsymbol{x}_{F} +\sin \alpha  \boldsymbol{y_{F}}+0\boldsymbol{r}+O_{F}
\end{array}
$$
dove $O_{F}$ è la [[Applicazione lineare - Proiezione|proiezione]] ortogonale di $p$ su $r$ e quindi si puo riscrivere sotto forma di [[Prodotto scalare euclideo (Dot product)|dot product]]$$O_{F}=(\boldsymbol{p}\cdot \boldsymbol{r})\boldsymbol{r}$$
e quindi $$\begin{array}{}
x_{F} & =  & \boldsymbol{p}-\boldsymbol{O}_{F}=\boldsymbol{p}- (\boldsymbol{p}\cdot \boldsymbol{r})\boldsymbol{r}  \\
y_{F} & = & r \times \boldsymbol{x}_{F}= r\times (\boldsymbol{p}-\boldsymbol{O}_{F}) \\
 & = & r \times \boldsymbol{p}-r\times(\boldsymbol{p}\cdot \boldsymbol{r})\boldsymbol{r} \\
 & = & \boldsymbol{r} \times\boldsymbol{p}
\end{array}$$
e quindi otteniamo la ___formula di Rodriguez___:
$$\boldsymbol{p}’=\cos \alpha \ \boldsymbol{p}+(1-\cos \alpha)(\boldsymbol{p}\cdot \boldsymbol{r})\boldsymbol{r}+ \sin \alpha (\boldsymbol{r} \times \boldsymbol{p})$$ questa è una formula chiusa che ci permette di saltare la costruzione del [[Frames|frame]] di rotazione 