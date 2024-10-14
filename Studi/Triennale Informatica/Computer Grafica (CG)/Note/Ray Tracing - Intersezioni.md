---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Ray Tracing]]"
SubTopic: 
---

# Ray Tracing - Intersezioni
---
un componente importante del __[[Ray Tracing|ray tracing]]__ sono gli algoritmi di test di intersezione con i vari tipi di [[Rappresentazione di modelli 3D|modelli 3D]]  

#### Intersezioni superfici algebriche
per intersecare un _ray_ con delle [[Superfici implicite|superfici algebriche]] è facile basta sostituire un punto con la definizione di raggio e trovare una soluzione infatti abbiamo che   

##### Cerchio 
intersezione di un __ray__ con una __sfera__ centrata in $c$ con raggio $r$ e rappresentata dalla [[Superfici implicite|curva implicita]] $$S=\{ \boldsymbol{p} \in  \mathbb{R}^3 \mid (\boldsymbol{p}-\boldsymbol{c})(\boldsymbol{p}-\boldsymbol{c})=r^2 \}$$ e bisogna testare se un __ray__ $\boldsymbol{o}+ t\boldsymbol{d}$ appartiene ad $S$. Si procede quindi per sostituzione 
![[Pasted image 20240310170345.png]]
$$
\begin{align}
(\boldsymbol{o}+t\boldsymbol{d}-c)(\boldsymbol{o}+t\boldsymbol{d}-\boldsymbol{c}) & =r^2\\
 ((\boldsymbol{o}-c)+t\boldsymbol{d})((\boldsymbol{o}-\boldsymbol{c})+t\boldsymbol{d}) & =r^2 \\
 \underbrace{ (\boldsymbol{o}-\boldsymbol{c})(\boldsymbol{o}-\boldsymbol{c})-\boldsymbol{r}^2 }_{ C }+t^2\underbrace{ \boldsymbol{d}^2 }_{ A }+t\underbrace{2\boldsymbol{d} (\boldsymbol{o}-\boldsymbol{c}) }_{ B }& =\boldsymbol{0}
\end{align}
$$
e quindi vale che si puo scrivere come $At^2+Bt+C=0$  e quindi $$t=\cfrac{-B\pm\sqrt{(B^2-4AC)}}{2A}$$ e il numero di soluzioni reali indicano il numero di intersezioni
![[Pasted image 20240310165822.png]]



##### Piano
l per il test di intersezione di un __ray__ con un __piano__ si usa la definizione de piano come $$P=\{\boldsymbol{p} \in  \mathbb{R}^3 \mid (\boldsymbol{p}-\boldsymbol{c})\boldsymbol{n}=\boldsymbol{0} \}$$
![[Pasted image 20240310172901.png]]
e si a $p$ sostituisce la definizione di  un raggio ottenendo$$(\boldsymbol{o}+ t\boldsymbol{d}-\boldsymbol{c})\boldsymbol{n}=\boldsymbol{0}$$
e quindi si ha che $$t=-\cfrac{(\boldsymbol{o}-\boldsymbol{c})\cdot\boldsymbol{n} }{d\cdot \boldsymbol{n}}$$ e vale che 
1. $t>0 \implies$ il ray ha un intersezione
2. $d\cdot \boldsymbol{n} \not=\boldsymbol{0} \implies$ una soluzione
3. $d\cdot \boldsymbol{n} =\boldsymbol{0} \implies$ ray parallelo al piano
4. $d\cdot \boldsymbol{n} \land (\boldsymbol{o}-\boldsymbol{c})\cdot\boldsymbol{n} \implies$ ray incluso totalmente nel piano



##### Quad
per l intersezione con un __quad__ che è definito a partire da un frame di riferimeto $F=\{ \boldsymbol{c},\boldsymbol{x},\boldsymbol{y},\boldsymbol{n} \}$ come $$Q=\{  (\boldsymbol{x},\boldsymbol{y},\boldsymbol{0}) \mid-\boldsymbol{a}<\boldsymbol{x}<\boldsymbol{a},-\boldsymbol{b}<\boldsymbol{y}<\boldsymbol{b}\}$$
![[Pasted image 20240310175021.png]]
e per cercare un punto di intersezione si puo
1. calcolare l intersezione ray-piano per trovare $t_i$
2. esprimere $\boldsymbol{o}+t_i\cdot d$ in $F$
3. testare se  le componenti $x,y$ coincidono
oppure piu efficientemente si puo calcolare direttamente in object-space
1. Esprimere il raggio in $F$ trasformandolo in $O_F+t\cdot d_F=F^{-1}\boldsymbol{o}+t\cdot F^{-1}\boldsymbol{d}$
2. calcolare l intersezione Ray-pianoXY per cercare $t_i$ e in questo caso il test diventa $t=- \cfrac{O_{F_z}}{d_{F_z}}$
3. testare se  le componenti $x,y$ coincidono 
![[Pasted image 20240310175737.png]]


##### Box
l intersezione di un raggio come una box si puo fare considerando ogni faccia come quad e usare quel tipo di intersezione.

Oppure piu efficientemente si possono usare gli __slabs__. gli __slabs__ sono una regione tra due piani paralleli e una scatola è un intersezione di 3 slabs 
![[Pasted image 20240311160515.png]]
a questo punto si puo usare l algoritmo [[Clipping di Frammenti nascosti|Liang-barsky]] usato per il clipping prendendo come volume la box ![[Clipping di Frammenti nascosti#Liang-Barsky|Liang-barsky]]

##### Triangle
per intersecare il ray con un triangoli
1. trova l intersezione con il piano
2. trova le [[Interpolazione di vertici - Coordinate Baricentriche|coordinate baricentriche]] 
![[Pasted image 20240311160611.png]]
$$\begin{align}
\boldsymbol{v_{b0}}  &=v_{20}-\cfrac{v_{20}v_{21}}{|v_{21}|}v_{21} \\
a_0  & =\boldsymbol{1}-\cfrac{\cfrac{\boldsymbol{v_{p0}v_{b0}}}{|\boldsymbol{v_{b0}}|}}{\cfrac{\boldsymbol{v_{20}v_{b0}}}{|\boldsymbol{v_{bo}}|}}=\cfrac{\boldsymbol{v_{p0}v_{b0}}}{\boldsymbol{v_{20}v_{b0}}}
\end{align}$$


##### Cilindro
per intersecare un __ray__ con un cilindro si posizione una __slab__ con i piani sopra e sotto  il cilindro.
e si controlla se il ray interseca con il cerchio della base nel piano
![[Pasted image 20240311160644.png]]



#### Costructure Solid Geometry
per intersecare un ray con la [[Costructive Solid Geometry (CSG)|CSG]]  bisogna sapere fare l intersezione su ognuna delle primitive usate
![[IMG_0781.jpeg]]
bisogna prima definire gli __spans__.
gli spans sono una porzione consecutiva del ray che partono da un $t_{in}$ e finiscono in $t_{out}$
![[Pasted image 20240311160725.png]]
l intersezione con un oggetto chiuso produce degli __span__ sul __ray__
![[Pasted image 20240311160732.png]]
e su questi si possono fare le operazioni di 
- unione
- intersezione 
- differenza
![[Pasted image 20240311160740.png]]
e quindi per trovare un intersezione basta cercare gli spans sulle foglie del albero di costruzione e poi seguire le operazioni che si riflettono anche sugli span. 
se é rimasto qualche span allora c é un punto di intersezione

per mantenere la corretta [[Normale di una superfice|normale]] basta mantenerla in memoria nei punti di intersezione, negandola in caso di intersezione
![[Pasted image 20240311160754.png]]



#### Scena
Si vuole testare se un raggio interseca un triangolo in una scena composta da $n$ triangoli.
![[IMG_1098 1 1.jpeg]]
il modo peggio di fare questa cosa è iterare su ogni triangolo è testare ognuno di questo.


Una soluzione migliore è quella di ridurre il numero di primitive da testare. 
Per fare ciò si immagina una griglia sulla scena e si raasterizza il raggio in modo da controllare quali delle celle rasterizate intersecano le celle della griglia. In questo modo si possono controllare solo le [[Computer grafica - Primitive Geometriche|primitive geometriche]] che sono al interno di quelle celle della griglia
![[IMG_1101 1 1.jpeg]]
La rasterrizzazione del raggio è simile a quella che si fa per [[Trasformare da Vertici a Frammenti (Rasterizazione)|disegnare una linea]] ma non uguale 
![[IMG_1102 1 1.jpeg]]

un modo per fare questo in 3D è il DDA-3d
In questo algoritmo si posizione una griglia cubica di voxel e interseca il  __ray__   un raggio con il bordi che definisce la fine e l inizio dei [[Voxelization|Voxel]] 


_siano_
- $tMaxX,tMaxY$ il valore massimo di $t$ per il quale la coordinata $X$ o $Y$ non cambia
- $tDeltaX,tDeltaY$ valore di cui incrementare $t$ per spostare un punto lungo il raggio della dimensione del voxel in direzione $X$ o $Y$  
e ricordando la definizione di __ray__ come $$r =\begin{bmatrix}
d_x\\d_y\\d_z
\end{bmatrix}\cdot t +\begin{bmatrix}
c_x\\c_y\\c_z
\end{bmatrix} $$
si ha che il caso 2D è come segue 
![[IMG_1103 1 1.jpeg]]

nel caso un __ray__ colpisce due [[Voxelization|voxel]] che hanno entrambi solo una parte della stessa [[Computer grafica - Primitive Geometriche|primitiva]] questa viene testata per l intersezione due volte.
Per evitare ciò si assegna alla primitiva l ID ultimo ray per cui è stata testata l intersezione, Se si vorrai provare a fare un secondo test sullo stesso __ray__ questo verra saltato
![[IMG_1104 1 1.jpeg]]


Bisogna decidere la dimensione dei voxel e quindi va scelto un compromesso tra velocità di rasterizazione e numero di primitive effettivamente tagliate
![[IMG_1106 1 1.jpeg]]In generale vale che conviene avere voxel piccoli dove la scena è densa di primitive e grandi dove non lo è 

Per ottenere un buon compromesso anche con griglie in regolari si possono applicare 2 approcci

suddivisione delle primitive:
questo è un approccio bottom-up, ogni primitiva viene confinata in un voxel e [[Ricorsione|ricorsivamente]] se due bordi intersecano si crea un nuovo bordo che le contiene entrambi  ![[IMG_1109 1 1.jpeg]]
questo approccio genera dei voxel irregolari quindi non si può usare rasterizazione 


_suddivisione dello spazio_: 
è un approccio top-Down, si segue  la stessa idea del [[Voxelization#Encoding Efficiente dei modelli in Voxel oct-tree|octa-tree]] ovvero si suddivide ricorsiva mente lo zone che contengono delle primitive e si lasciano invariate quelle che non le contengono
![[IMG_1107 1 1.jpeg]]

Per salvare efficientementel octa-tree si possono codificare i nodi che hanno delle primitive con dieci numeri interi in modo che numeri consecutivi corrispondono a celle consecutive.

Per fare cio si può usare la Z-Filling Curve
![[IMG_1110 1 1.jpeg]]


Un altro modo è usare un __Bynary space partition-Tree__ (BSP)
si divide  ricorsiva di una regione dello spazio in due partizione e la divisione è fatta con un  iperpiano
si costruisce un  [[albero binario|albero binario]] dove i nodi sono la divisione dei piani e le foglie le primitive nel piano rappresentato dal padre
![[IMG_1112 1 1.jpeg]]

per testare se un punto è al interno di una primitiva si discende l albero iniziando dalla radice e si arriva fino alla foglia che contiene la primitiva cercata. Si fa in test di intersezione con tutte le primitive in quella foglia.
![[IMG_1113 1 1.jpeg]]
Il [[Complessita|costo computazionale]]  nel numero di primitive $n$
- caso pessimo $O(n)$
- Caso Medio. $O(\log n)$ 




##### kd-tree
Si puo usare anche un __kD-trees__ ovvero un __BSP__ con le divisioni allineate agli assi  

![[IMG_1114 1 1.jpeg]]
E per costruire efficientemente questi tipo di albero bisogna sapere quale è il costo.
Questo può essere visto come la [[Probabilita condizionata|probabilita condizionata]] del intersezioni con una cella significa anche l intersezione di una sua parte qundi 
$$\begin{align}
cost(cell)  = \ & cost\_traversal & + \\
	 & \mathcal{P}(left\_cell|cell)Cost(left\_cell) & + \\
	 & \mathcal{P}(right\_cell|cell)Cost(right\_cell)

\end{align}
$$
![[IMG_1115 1 1.jpeg]]
prendendo come esempio $left\_cell$ si ha che $$\mathcal{P}(left\_cell|cell) = \cfrac{Area(left\_cell)}{Area(cell)}$$
e  $$cost(left\_cell)$$ dipende dal numero di primitive al interno i $left\_cell$ ![[IMG_1116 1 1.jpeg]]

quindi si fa sceglie una divisione che minimizza il costo ad esempio 
![[IMG_1117 1 1.jpeg]]