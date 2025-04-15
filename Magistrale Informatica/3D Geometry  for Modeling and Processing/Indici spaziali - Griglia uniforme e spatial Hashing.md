---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---


# Indici spaziali - Griglia uniforme e spatial Hashing
---
le **Griglia uniforme** e sono dei [[Indici spaziali|Indici spaziali]] **NON gerarchici** è possono essere descritti nel seguente modo:

Lo **spazio geometrico** viene suddiviso con una **griglia uniforme** con **celle cubiche**, ciascuna delle quali contiene riferimenti alle [[Computer grafica - Primitive Geometriche|primitive geometriche]] presenti nella cella. 

per costruire **griglia** ogni primitiva deve essere assegnata ad almeno una cella e questo puo essere fatto nel seguente modo metodo, la primitiva viene assegnata:
- alla cella che contiene una caratteristica della primitiva, come ad esempio il [[Interpolazione di vertici - Coordinate Baricentriche|baricentro]] o uno dei suoi vertici 
- a tutte le celle attraversate dalla primitiva stessa.![[IMG - Indici spaziali griglia uniforme 1.png]]


Alcune query su usando **griglie uniformi** sono le seguenti:
**Cella di una primitiva**: basta fare la divisione intera di $(x, y, z)$ per calcolare a quale cella appartiene quel punto, quindi ha [[Complessita|Complessita]] constante

**primitiva più vicina ad un punto** $p$: si inizia dalla cella che contiene $p$ e si controllano i primitivi presenti all'interno di sfere concentriche crescenti centrate in $p$. Ad ogni passo, il raggio della sfera viene aumentato includendo nuove celle. la [[Complessita|complessità]] 
- caso peggiore $O(\#cells + n)$ nelle $n$ è primitive
- caso medio: $O(1)$
![[IMG - Indici spaziali griglia uniforme.png]]

**Intersezione primitive con un raggio**: Questo è la query principale fatta dal [[Ray Tracing|Ray Tracing]].   Per risolverla si identificano di tutte le celle attraversate dal raggio, per ogni cella individuata, si esegue un test di intersezione con le [[Computer grafica - Primitive Geometriche|primitive geometriche]] contenute in essa, evitando di testare primitive gia incontrate da altre celle "mailboxing". 
la [[complessita|complessita]] è 
- caso peggiore: $\mathcal{O}(\#cells + n)$ dove $n$ è il numero totale di primitive.
- caso medio:  $\mathcal{O}(d\sqrt[d]{\#cells} + \sqrt[d]{n})$ con $d$ la dimensionalità dello spazio.
![[IMG - Intersezione raggio griglia uniforme e primitive testate.jpeg]]
![[IMG - Occupazione in griglia.png]]


La **griglia uniforme** è l [[Indici spaziali|indice spaziale]] più semplici da implementare ma ha due contro principali:  
- l'occupazione di memoria che è data da $\mathcal{O}(\#cells + n)$, Il che puo essere uno spreco in quanto in ogni caso al crescere della dimensione della scena ci saranno sempre piu celle vuote. Questo è anche un problema in quanto questo approccio non è [[Cache|chache frendly]].
- le performance dipendono molto dalla distribuzione delle primiive

Per risolvere il problema dell occupazione di memoria si utilizza lo **Spacial hashing** non si mantiene in memoria ogni cella e ogni cella che interseca con una primitiva viene [[Funzioni Hash|hashata]] e quindi si salvano quindi solo le celle effettivamente in uso, introducendo pero il problema della gestione delle collisioni.
Questo **indice spazione** mantiene gli quasi gli stessi costi teorici della **griglia uniforme**, eccezione fatta per l' accesso ad una cella che per via delle collisioni al caso pessimo ha [[Complessita|complessità in tempo]] $\mathcal{O}(\#cells)$ mentre la [[Complessita|complessita in spazio]] :
- *caso peggiore*: si memorizzano tutte le celle volumetriche $\mathcal{O}(\#cells)$
- *caso medio*: si alloca memoria solo per le celle che intersecano primitive.
![[IMG - Spatial hashing.png]]
Il problema principale di questo approccio è la scelta ottimale della dimensione della cella, infatti questa dipende molto dal tipo di input che si usa: 
![[IMG - scelta della cella.png]]
![[IMG_1106 1 1.jpeg]]








##### Intersezione di un raggio con la griglia

_siano_
- $tMaxX,tMaxY$ il valore massimo di $t$ per il quale la coordinata $X$ o $Y$ non cambia
- $tDeltaX,tDeltaY$ valore di cui incrementare $t$ per spostare un punto lungo il raggio della dimensione del [[Voxelization|voxel]] in direzione $X$ o $Y$  
e ricordando la definizione di __ray__ come $$r =\begin{bmatrix}
d_x\\d_y\\d_z
\end{bmatrix}\cdot t +\begin{bmatrix}
c_x\\c_y\\c_z
\end{bmatrix} $$
si ha che il caso 2D è come segue 
![[IMG_1103 1 1.jpeg]]

