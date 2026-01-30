---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
Course 2: "[[Computer Grafica (CG)]]"
tags:
  - 3GMP
  - CG
Area: 
topic: 
SubTopic:
---

# Normale di una superfice discreta (Mesh poligonali)
---
La **normale di una superficie discreta**, comunemente una [[Mesh Poligonali|mesh poligonale]], è una stima della [[Normale di una superfice parametrica|normale]] della [[Superfici|superficie continua]] che la mesh rappresenta. 

![[Pasted image 20240221001431.png]]
Il modo più semplice per calcolare la [[Normale di una superfice parametrica|normale]] di una superficie discreta, come una [[Mesh Poligonali|mesh triangolare]], è farlo **per faccia**, poiché ogni [[Computer grafica - Primitive Geometriche|triangolo]] è planare. Per ottenere la normale di una faccia è sufficiente calcolare il [[Prodotto Vettoriale (Cross product)|cross product]] tra due edge della faccia.
 formalmente 
**sia**
- $f$ un faccia di una [[Mesh Poligonali|mesh triangolare]]
 - $d_1,d_2$ due edge [[Simplex (Simplesso)|facce]] di $f$
 **allora** la normale in $f$ è calcolata come $$\mathbf{n}_f = \cfrac{d_1 \times d_2}{\|d_1 \times d_2\|}$$una volta calcolata vale che $\forall x \in f \mid \mathbf{n}_x = \mathbf{n}_f$ è questo vale perche tutti i punti $x \in f$ sono sullo stesso piano. Questo metodo, sebbene molto efficiente, non fornisce una buona stima della [[Normale di una superfice parametrica|normale]].


Un metodo piu accurato è calcolare La **[[Normale di una superfice parametrica|normale]]** per **[[Computer grafica - Primitive Geometriche|vertice]]** $v$ e in quel caso per calcolare la normale in un generico punto  $x \in f$ su una faccia della mesh si [[Interpolazione di vertici - Coordinate Baricentriche|interpola con coordinate baricentriche ]] tra le normali calcolate nei vertici nella faccia  $f$

formalmente per calcolare la normale nei vertici:
**sia**
- $v$ un vertice sulla [[Mesh Poligonali|mesh]]
- $S^*(v) = \{f : f \text{ coface of } v\}$ è l'insieme delle [[Simplex (Simplesso)|cofacce]] di $v$, ovvero le facce che hanno come vertice $v$
**allora** si puo calcolare la normale $\mathbf{n}_v$ a partire dalle **normali delle facce** adiacenti la media non pesata delle normali di tutte le facce che condividono il vertice:$$
\mathbf{n}_v = \cfrac{1}{|S^{*}(v)|} \sum_{i \in S^{*}(v)} \mathbf{n}_{f_i}
$$![[IMG - Normale per vertice tramite media caso dimensioni uniformi.png]] Questa formulazione funziona bene quando le **facce** attorno al vertice hanno dimensioni simili. In caso contrario, le facce più piccole finiscono per avere un peso maggiore nella media, influenzando il risultato in modo sproporzionato.
![[Pasted image 20240221003638.png]]
Per compensare questo effetto, è possibile introdurre un peso per ogni **faccia** basato sulla sua area. La [[Normale di una superfice parametrica|normale]] del vertice viene così calcolata come **media pesata**:$$
\mathbf{n}_v = \cfrac{1}{\sum_{i \in S^{*}(v)} \text{Area}(f_i)} \sum_{i \in S^{*}(v)} \text{Area}(f_i) \mathbf{n}_{f_i}
$$Questo approccio si puo anche efficientare nel seguente modo:
Siccome la magnitudo della **normale per faccia** denormalizzata calcolata come  :$$\mathbf{n}_{df} = d_1 \times d_2$$ è $\|\mathbf{n}_{df}\| = 2Area(f)$ ovvero il doppio del area del triangolo $f$ si puo ottenere la media pesata direttamente come  $$\mathbf{n}_v = \cfrac{1}{|S^{*}(v)|} \sum_{i \in S^{*}(v)} \mathbf{n}_{df_i}$$ per la sua semplicità computazionale questo è il metodo standard. Può pero risultare impreciso in presenza di triangoli molto allungati, poiché da troppo peso a facce non localmente rilevanti. 
![[IMG - calcolo delle normali discrete in caso di triangolo lunghi.png]]
Per tenere conto soltanto della geometria immediatamente vicina al vertice, si può usare come peso l'angolo $\alpha$ che ogni faccia forma in corrispondenza del vertice:$$
\mathbf{n}_v = \cfrac{1}{\sum_{i \in S^{*}(v)} \alpha(f_i, v)} \sum_{i \in S^{*}(v)} \alpha(f_i, v) \mathbf{n}_{f_i}
$$

dove $\alpha(f_i, v)$ è l’angolo interno del triangolo $f_i$ nel vertice $v$.





Per gestire questo il caso in cui la normale non esiste neanche nel caso continuo si possono calcolare 2 normali per vertice 
![[Pasted image 20240221004148.png]]
 per ogni vertice si sceglie se calcolare 1 o 2 normali basandosi su un angolo massimo  detto __crease angle__ che la superfice puo avere, se si supera quel angolo allo la mesh non é smooth e il vertice ha bisogno di due normali.

questa seconda normale puo essere memorizzata o in un vertice duplicato oppure nella faccia che ha quel vertice
![[Pasted image 20240221004411.png]]



##### Utilizzo della norma discreta nel rendering
Gli effetti di calcolare la [[Normale di una superfice parametrica|normale]] per faccia nel  [[Rendering|rendering]] è quella che tende ad evidenziare i singoli triangoli, rendendo visibile la struttura della mesh, cosa che solitamente si cerca di evitare. (sinistra) 

mentre invece calcolare la [[IMG - caso limite definizione normale in superfice parametrica.png|normali]] ai **[[Computer grafica - Primitive Geometriche|vertici]]** tendono a dare  una transizione più fluida tra le facce e una rappresentazione visiva più morbida e continua della superficie, riducendo l’effetto a spigoli tipico delle normali per faccia e migliorando la resa della curvatura implicita nella superficie discreta. (destra)
![[IMG - rendering usando la normale per faccia e per vertice.png]]


