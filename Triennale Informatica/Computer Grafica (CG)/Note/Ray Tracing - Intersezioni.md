---
Course: "[[Computer Grafica (CG)]]"
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
il modo peggiore di fare questa cosa è iterare su ogni triangolo è testare ognuno di questo. 
Per ottimizare questo processo si fa largo uso degli [[Indici spaziali|Indici spaziali]], strutture dati appositamente progettate per poter rispondere a domande sulle primitive come collisioni o vicinanza.




[[Ray tracing|Ray tracing]] e [[Indici spaziali - Griglia uniforme e spatial Hashing|Griglia uniforme ]]
La rasterizazione del raggio è simile a quella che si fa per [[Trasformare da Vertici a Frammenti (Rasterizazione)|disegnare una linea]] ma non uguale 
![[IMG_1102 1 1.jpeg]]








suddivisione delle primitive:
questo è un approccio bottom-up, ogni primitiva viene confinata in un voxel e [[Ricorsione|ricorsivamente]] se due bordi intersecano si crea un nuovo bordo che le contiene entrambi  ![[IMG_1109 1 1.jpeg]]
questo approccio genera dei voxel irregolari quindi non si può usare rasterizazione 