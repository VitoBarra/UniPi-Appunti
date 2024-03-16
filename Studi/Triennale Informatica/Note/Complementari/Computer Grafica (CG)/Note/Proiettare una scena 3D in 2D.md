---
Subject: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---
A

# Proiettare una scena 3D in 2D 
Data una scena nello spazio 3D  per visualizzarla bisogna [[Applicazione lineare - Proiezione|proiettarla]] in uno spazio 2D che rappresenta lo schermo
per fare cio si segue una pipeline operazionale
![[Pasted image 20240210022744.png]]
ogni per passare da uno spazio al altro si utilizzano delle trasformazioni con delle matrici e abbiamo quindi la pipeline come 
![[immagine_2024-02-10_013539544.jpg]]
e OpenGL solitamente non usa neanche internamento il word space e si passa direttamente da __Object space__ a __view space__ utilizzando la __matrice Model-view__ 


#### Object space
l __object space__ e' dove l'oggetto viene creato, l oggetto e' espresso a partire dal suo [[Frames|frame]] canonico di riferimento e solitamente l oggetto e' centrato al origine del frame e allineato ad esso  
![[Immagine 2024-02-10 024433.png]]

#### World Space
il __Word space__ e' il [[Frames|farame]] di riferimento del intero mondo.
Gli oggetti sono posizionati nel word space dando una posizione al [[Frames|frame]] canonico del oggetto che si vuole piazzare
![[Pasted image 20240210024831.png]]


#### Frame di vista di riferimento
il __frame di vista__ (View reference frame)  indicato con $V_{RF}$ e' un [[Frames|frame]] unitario e [[Vettori Ortonormali|ortonormale]] che _convenzionalmente_ si usa per rappresentare le informazioni di posizione e orientamento della __camera__.
infatti abbiamo che
- __View point__ (punto di vista): e' rappresentato dal __origine__ del frame
	- e' il punto da cui osserviamo la scena
- __View direction__ (direzione di vista): e' rappresentato asse  $-z$
	- la direzione in cui la camera e' orientata
- __Up direction__: e' rappresentato dal asse $y$
	- la direzione dove e' locato il sopra

![[Pasted image 20240131002705.png]]

Possiamo costruire il frame a partire  da $View \ dirction$ e $up$. 
ricordando che stiamo  cercando un frame ortonormale i passi sono:
1.  normalizzare $z=\cfrac{View \ direction}{\|View \ direction\|}$ e $y' = \cfrac{up}{\|up\|}$ 
	- $y$ non e' per un vettore ortogonale a $z$ e quindi si procede come
2. calcolare $x=z \times y'$ usando [[Prodotto Vettoriale (Cross product)|Cross product]]  
3. calcolare $y=z \times x$ usando [[Prodotto Vettoriale (Cross product)|Cross product]]   
cosi facendo si ottengono 3 [[Vettori Ortonormali|vettorii ortonormali]]  
![[Immagine 2024-02-10 023037 1.png]]
i parametri che descrivono il $V_{RF}$ sono detti __parametri di camera estrinsechi__

il $V_{RF}$ puo essere scritta in forma matriciale come
$$V_{RF} = \begin{bmatrix}
\boldsymbol{x}_x & \boldsymbol{y}_x  &  \boldsymbol{z}_x & o_x \\
\boldsymbol{x}_y & \boldsymbol{y}_y  &  \boldsymbol{z}_y & o_y  \\
\boldsymbol{x}_z & \boldsymbol{y}_z  &  \boldsymbol{z}_z & o_z  \\
0 & 0 & 0 & 1
\end{bmatrix}$$
Applicare il __View reference frame__ $V_{RF}$  ad un punto espresso in __View-space__ ci da la rappresentazione di quel punto in  __Word Space__. 
Per passare dal __Word space__ al __View-space__ si utilizza la __View matrix__ che è l inversa [[Matrice inversa|inversa]] di $V_{RF}$ ed essendo $V_{RF}$ [[Applicazioni affini|affine]] e [[Matrici ortogonali|ortogonale]] la __View Matrix__ puo essere calcolata come 
$$
VM=V_{RF}^{-1}=
\begin{bmatrix}
R^T_{xyz} &(-R_{xyz}^To) \\
0 & 1
\end{bmatrix}, \ \ \ 
R_{xyz}=\begin{bmatrix}
\boldsymbol{x}_x & \boldsymbol{y}_x  &  \boldsymbol{z}_x \\
\boldsymbol{x}_y & \boldsymbol{y}_y  &  \boldsymbol{z}_y  \\
\boldsymbol{x}_z & \boldsymbol{y}_z  &  \boldsymbol{z}_z
\end{bmatrix}
$$

tutte le [[Applicazioni affini|trasformazioni]] che si fanno in rispetto del frame di vista si chiamano Trasformazione di vista (view Transformation)
![[Pasted image 20240210031247.png]]

#### Proiezioni
le  __proiezione__ sono definiscono il  "tipo" di __camera__ che si usa per osservare la scena. La __Camera__ si occupa di mappare il mondo 3D su un piano 2D e lo fa utilizzano le __proiezioni__, il modo in cui avviene questo mapping dipende dai dei parametri detti __intrinseci__ 

Si assume senza perdita di generalità che la scena e' espressa in termini del __View reference frame__

##### Proiezione prospettica
la proiezione prospettica si ottiene considerando 2 elementi:
- Point of View : il "punto di vista", che siccome stiamo usando il View Reference frame questo corrisponde a l' origine
- View plane : un "piano di vista", ovvero un piano che usando il View Reference frame e' ortogonale al asse $z$
 
Indicando con $\boldsymbol{C} = \begin{bmatrix}0,0,0,1\end{bmatrix}^T$ il view point e con $VP$ il piano di vista e fissato al punto $-d$, supponendo di avere nello spazio 3D un punto $\boldsymbol{p}$, abbiamo che la sua proiezione prospettica $\boldsymbol{p}'$ e' l intersezione con il $VP$ della [[Retta|retta passante]] per $C$ e $\boldsymbol{p}$  

![[Pasted image 20240207185229.png]]

geometricamente possiamo osservare che i triangoli $Cap'$ e $Cbp$ sono [[Triangoli Simili|simili]] e quindi il rapporto tra i lati corrispondenti sono uguali. Abbiamo quindi che vale$$\begin{array}{}

\displaystyle\frac{p'_y}{-d}=\frac{p_y}{p_z}  & \implies &  \displaystyle p'_y=-\frac{dp_y}{p_z} \\
\displaystyle \frac{p'_x}{-d}=\frac{p_x}{p_z}  & \implies &\displaystyle  p'_x=-\frac{dp_x}{p_z}
\end{array}
$$e questo fatto ci permette di derivare facilmente la formula per la proiezione di $\boldsymbol{p}$ infatti possiamo scrivere che  $$\boldsymbol{p}'=\begin{bmatrix}
\displaystyle-\frac{dp_x}{p_z} \\
\displaystyle-\frac{dp_y}{p_z} \\
-d \\
1
\end{bmatrix}$$

> [!note]
> questa descrizione e' quella di guardare da una finestra (VP) con un occhi solo (C) la scena



una visione alternativa e' quella della camera pinhole, ovvero punto infinitamente piccolo sulla superfice di una scatola scura e la VP nel lato opposto del pinhole
disegnando le retto dei vertici della scena al pinhole fino ad intersecare VP avremmo che il risultato finale sarà specchiato (il sopra sarà sotto e il destra sarà a sinistra) motivo per cui si preferisce il modello a finestra
![[Pasted image 20240131002603.png]]
###### Divisione prospettica
Osservando la costruzione della proiezione abbiamo che tutti i punti sul linea di proiezione di $\boldsymbol{p}$ corrispondono allo stesso punto $\boldsymbol{p}'$
![[Immagine 2024-02-10 002259.jpg]]
possiamo esprimere questo fatto utilizzando le [[Coordinate omogenee|coordinate omogenee]] infatti abbiamo che indicando con $prj(\cdot)$ l operazione di proiezione $$ \boldsymbol{p}'=prj\left(\lambda\begin{bmatrix}
p_x\\p_y\\p_z\\1
\end{bmatrix}\right) \ \ \ \ \ \ \forall \lambda \not=0$$
Utilizzando queste proprietà possiamo scegliere $\lambda$ a piacere e in particolare possiamo scegliere $\lambda = -\cfrac{p_z}{d}$  in questo modo partendo dalla formula per calcolare $\boldsymbol{p}'$ avremmo che vale$$\boldsymbol{p}'=-\cfrac{p_z}{d}\begin{bmatrix}
\displaystyle-\frac{dp_x}{p_z} \\
\displaystyle-\frac{dp_y}{p_z} \\
-d \\ 1
\end{bmatrix} =
\begin{bmatrix}
p_x \\p_y \\p_z\\
\displaystyle -\frac{p_z}{d}
\end{bmatrix}$$ a questo punto avremmo che la formula per calcolare $\boldsymbol{p}'$ e' lineare siccome nessun componente di $\boldsymbol{p}'$ compare a denominatore e quindi possiamo usare la notazione matriciale per esprimere la proiezione e vale quindi che $$\boldsymbol{p}' = P_{prp} \ \boldsymbol{p} = \underbrace{ \begin{bmatrix}
1  & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & -\frac{1}{d} & 0
\end{bmatrix} }_{ prespective\ projection } \begin{bmatrix}
p_x \\ p_y \\ p_z \\ 1
\end{bmatrix} =\begin{bmatrix}
p_x \\p_y \\p_z\\
\displaystyle -\frac{p_z}{d}
\end{bmatrix} = \begin{bmatrix}
\displaystyle-\frac{dp_x}{p_z} \\
\displaystyle-\frac{dp_y}{p_z} \\
-d \\ 1
\end{bmatrix}
$$e l operazione di dividere tutti i componenti per la quarta componente per portare il punto nella forma canonica si chiama __prespective division__ (divisine prospettica).

Questa operazione __NON__ e' una [[Trasformazioni affini|trasformazione affine]] infatti preserva la colinearità tra punti ma non preserva il rapporto tra le distanze, gli angoli e le lunghezze delle linee
 
###### Effetto dei parametri
cambiando i valori parametri della proiezione prospettica possiamo controllare come cambia cio che vediamo. 

 $d$ indica la distanza tra il punto di osservazione, l "occhio", e il view Plane ($VP$) e variando $d$ abbiamo 
![[Pasted image 20240210014241.png]]
 con
 - $d$ basso abbiamo l effetto grand' angolo 
 - $d$ alto  ci spostiamo verso la proiezione ortogonale dove le linee di proiezione sono parallele.



##### Proiezione ortografica
La __proiezione ortografica__ e' una proiezione dove tutti le linee di proiezione (projectors) sono paraleli e [[Vettori Ortogonali|ortogonali]] al piano di vista $VP$  

![[Immagine 2024-02-10 020704.jpg]]
Questa si ottiene settando la coordinata $p_z$ alla distanza $-d$ (near)  questo viene dal fatto che $p'_x$ e $p'_x$ sono indipendenti da $d$ e la coordinata $p_z$ non importa siccome per motivi geometrici questa viene mappata a prescindere alla distanza $-d$ dal punto di vista.
In forma matriciale abbiamo quindi:
$$\boldsymbol{p}' = O_{oth} \ \boldsymbol{p} = \underbrace{ \begin{bmatrix}
1  & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 0 & -d \\
0 & 0 & 0 & 1
\end{bmatrix} }_{ Orthographic\ projection } \begin{bmatrix}
p_x \\ p_y \\ p_z \\ 1
\end{bmatrix} =\begin{bmatrix}
p_x \\p_y \\-d\\1
\end{bmatrix} 
$$
questa e' una [[Applicazioni affini|trasformazione affine]] ma non e' [[Matrice inversa|invertibile]]

#### View Volume
il __View volume__ e' una porzione dello spazio 3D visto dalla camera.

Questo si costruisce utilizzando 2 piani detti __near plane__ e __far palce__, il near plane corrisponde al View Plane utilizzato nelle definizione delle proiezioni, mentre il far plane e' un  alto piano che si utilizza per delimitare fin dove gli oggetti devono essere "visti".  
Gli oggetti dietro in near plane e dopo il far plane (rispetto al punto di osservazione) vengono ignorati e per questo motivo i due piani vengono chiamati __Cliping planes__ siccome si utilizzano per "tagliare" la scena       
![[Senzanome.png]]



#### Dimensione View palne e View Volume
per specificare la dimensione del __View Window__ (VW) e del __View Volume__ (VV) ci si divide in due modo uno applicare solo in caso di proiezione prospettica, l altro invece applicabile piu in generale

In generale la __View Window__ è un rettangolo sul __View Plane__ e scegliere è necessario a determinare  la dimensione del __View Volume__  


Ne caso della __proiezione Prospettica__ si ha che un modo per rappresentare la __finestra di vista__ è utilizzare Il __Field of View__ (__FOV__), Ovvero si specificano i parametri del [[Angoli|angolo]] di vista e la dimensione della finestra di vista, entrambi in modo indipendente a seconda della direzione 
- $FoV_v = yFov$ Un [[Angoli|angolo]] per la __dimensione verticale__ quindi sul asse $y$ e questo determina la lunghezza verticale della __View Window__ $h$ 
- $FoV_h=xFov$ Un [[Angoli|angolo]] per la dimensione orizzontale quindi sul asse $x$ e questo determina  la lunghezza orizzontale della __View Window__ $w$
![[Pasted image 20240210014256.png]]
![[Pasted image 20240210015150.jpg]]
![[Pasted image 20240210015206.png]]
In piu va specificate la distanza del __Far plane__ $f$ in modo da determinare l intero __View Volume__

un modo alternativo valido per entrambi i tipi di proiezione è specificare via parametri l intero __View volume__. questi sono che sono:
- $r$ right: distanza versodestra del rettangolo
- $l$ left: distanza verso sinistra  del rettangolo
- $t$ top: distanza verso l altro  del rettangolo
- $b$ bottom:  distanza verso il basso  del rettangolo
- $n$ near: la distanza tra il  __punto di vista__ è il __View Plane__ 
- $f$ far: la distanza tra il __punto di vista__ e fino a dove si deve guardare 
A seconda dei tipi di camera ottieniamo diversi View Volume, In 2D sono visti come![[Pasted image 20240210182346 1.png]]

#### Cononical View Volume
la proiezione nella pipeline non e' l ultimo step e' siccome la forma del __View volume__ cambia a seconda della proiezione scelta nasce la problematica di dover parametrizzare la pipeline per adattarsi al tipo di __View Volume__, questo renderebbe pero le cose più difficile e quindi si segue un altro approccio

Si trasforma il __View Volume__ in un __Canonical view volume__ (_CVV_), questo farà da interfaccia comune che permettere alla pipeline di funzionare a prescindere dalla proiezione 

il __Canonical View Volume__ (CVV) e' un cubo di lato 2 centrato al origine e quindi i suoi angoli sono ai punti $[1,1,1]$ e $[-1,-1,-1]$  


Prima di Arrivare al __CVV__ si deve passare al __clip space__ per poter eseguire le operazioni di [[Clipping di Frammenti nascosti|clipping delle primitive]] 
il  __Clip space__ è uno spazio 4D   che e' dove le primitive geometriche parzialmente fuori dal volume ottenuto vengono tagliate via da ciò che va renderizzato.

Per effettuare la trasformazione da __View space__ a __Clip space__ si utilizzano le seguenti matrici.

$$\begin{matrix}
P_{persp}= \underbrace{ \begin{bmatrix}
\frac{2n}{r-l} & 0 & \frac{r+l}{r-l} & 0 \\
0 & \frac{2n}{t-b} & \frac{t+b}{t-b}  & 0 \\
0 & 0 & \frac{-(f+n)}{f-n} & \frac{-2fn}{f-n} \\
0 & 0 & -1 & 0  
\end{bmatrix} }_{ perspective \ projection }   \\
 P_{orth}=
\underbrace{ \begin{bmatrix}
\frac{2}{r-l} & 0 & 0 & \frac{r+l}{r-l} \\
0 & \frac{2}{t-b}  & 0 & \frac{t+b}{t-b} \\
0 & 0 & \frac{-2}{f-n}  & -\frac{f+n}{f-n} \\
0 & 0 & 0 & 0
\end{bmatrix} }_{ orthographic\ \ projection }   
\end{matrix}$$

Per passare dal __clip space__ al __CVV__ bisogna normalizzare i punti al suo interno. Per indicare la necessita di questo processo di normalizzazione il __CVV__ viene anche chiamato __Normalized Device Context__ (NDC) e le coordinate di questo spazio sono dette __Normalized device coordinates__ 
![[Pasted image 20240131002757.png]]
![[Immagine 2024-02-10 140419.png]]



#### View Port
la __View Port__ e' una porzione di un rettangolo più grande chiamato __Application Window__ che e' dove e permesso al applicazione di disegnare i suoi elementi.
![[Pasted image 20240131002825.png]]
Questa ha Coordinate Discrete siccome disegna utilizzando i pixel dello schermo.

la __View Port__ viene riempito con ciò che e' presente nel __View Plane__ (o View windows) dopo la proiezione
il __View Plane__ e' mappato sul faccia $(-1,-1,-1),(1,-1,1),(1,1,-1),(-1,1,-1)$  del __CVV__ e bisogna trasformare questa faccia nella __view Port__. Per fare cio si utilizza il seguente algoritmo
sia
- $(v_x,v_y)^T$ l angolo in basso a sinistra della __view port__ 
- $(v_X,v_Y)^T$ l angolo in alto a destra della __view port__
per effettuare la trasformazione da __CVV__ a __view port__ bisogna 
1. [[Trasformazioni Geometriche affini#Traslazioni|traslare]] in modo da portare l angolo in basso a sinistra al origine
2. scalare di $\cfrac{v_X-v_x}{2}$ sul asse $x$
3. [[Trasformazioni Geometriche affini#Scaling|scalare]] di $\cfrac{v_Y-v_y}{2}$ sul asse $y$
4. [[Trasformazioni Geometriche affini#Traslazioni|traslare]] di $(v_x,v_y)$ 
 dove i passi 2-3 servono a trasformare la faccio del CVV in un rettangolo grande quando la __View Port__ e il passo 4 serve per posizionarlo dove e' la __view port__.
 
In forma matriciale si puo scrivere come:
![[Pasted image 20240211011253.png]]
$$\begin{align}{}
W & =  
\begin{bmatrix}
1 & 0 & v_x \\
0 & 1 & v_x \\
0 & 0 & 1
\end{bmatrix} 
\begin{bmatrix}
\cfrac{v_X-v_x}{2} & 0 & 0 \\
0 & \cfrac{v_Y-v_y}{2}  & 0  \\
0 & 0 & 1
\end{bmatrix} 
\begin{bmatrix}
1 & 0 & 1 \\
0 & 1 & 1 \\
0 & 0 & 1
\end{bmatrix} \\
 & = 
\begin{bmatrix}
\cfrac{v_X-v_x}{2} & 0 & \cfrac{v_X-v_x}{2}v_x \\
0 & \cfrac{v_Y-v_y}{2}  & \cfrac{v_Y-v_y}{2}v_y  \\
0 & 0 & 1
\end{bmatrix}
\end{align}$$


###### Correzione di Aspect ratio 
l __Aspect ratio__ di un rettangolo e' il rapporto tra la larghezza (width) e altezza (height)

Se l __aspect ratio__ del View plane e del View Port sono diverse avremmo che la scena che vediamo  e' deformata e questo avviene perché la trasformazione $PW$ ($P$ e' la trasformazione di proiezione) genera uno scaling non uniforme.

ritrovarsi in questa situazione e' molto comunque, in piu solitamene la __view port__ copre tutta l __application windows__

Formalizzando abbiamo che 
_Sia_
- $V_w,V_h$ la larghezza e l altezza del __view plane__ che vogliamo impostare
- $W_w,W_v$  la larghezza e l altezza della __View Port__ 
abbiamo che il problema della deformazione si presenta quando $$\frac{V_w}{V_h} \not = \frac{W_w}{W_h}$$per risolvere il problema vogliamo tenere fisso la __View port__ e  modificare $V_w$ e $V_h$ per ottenere lo stesso aspect ratio. 
per fare si utilizzano due fattori di scaling $k_w,k_h$ ottenendo $$
\begin{array}{}
V'_w=V_w k_w \\
V'_h=V_h k_h \\
\end{array} $$ tale che valga$$\frac{V'_w}{V'_h} = \frac{W_w}{W_h}$$avere due coefficienti ci permette di scegliere in che modo fare lo scaling infatti la soluzione piu comune e' tenere fisso uno dei dure e risolvere per l altro.
1. se $\frac{V_w}{V_h} > \frac{W_w}{W_h}$ si fissa $k_w=1$ e si risolve per $k_h$
2. se $\frac{V_w}{V_h} < \frac{W_w}{W_h}$ si fissa $k_h=1$ e si risolve per $k_w$
In questo modo avremmo che il coefficiente per cui stiamo risolvendo e' sempre $>1$ e stiamo sempre allargando la __view windows__, questo ci garantisce di non tagliare mai qualcosa che intendevamo vedere