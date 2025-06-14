---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Alpha Shape
---
un **Alpha Shape** è una [[Poliedro|poliedro]] ottenuto collegando con un [[Computer grafica - Primitive Geometriche|edge]] tra loro i punti connessi da una sfera di un [[Inviluppo Alpha (Alpha hull)|Inviluppo Alpha]] di un [[Insiemi Matematici|insieme]] $S \subset \mathbb{R}^n$ finito. 
![[IMG - alpha haull vs alpha shape.png]]
e sono usate come metodo **esplicito** per [[Ricostruzione di superfici del mondo reale con rappresentazioni point base|ricostruzione di superfici]]
 

Per costruire una **alpha shape** si utilizzano gli **alpha diagra** che sono essenzialmente definite come i [[Tasselizazione di Voronoi|diagrammi di vornoi]] ma lo spazio associato ad ogni seme è limitato da l' raggio $\alpha$
![[IMG - Ricostruzione di superfici alpha diagram.png]]
il diagramma ottenuto è l intersezione tra il [[Tasselizazione di Voronoi|diagramma di voronoi]] e tutte le sfere centrare nei punto di raggio $\alpha$. 

Come nel [[Tasselizazione di Voronoi|diagramma di voronoi]] si puo generare la [[Tasselizazione di Voronoi|triangolazine di delauny]] qui si puo generare la **triangolazione alpha** seguendo le stesse regole, ovvero connettendo con un edge i semi che generano celle con si toccano.
![[IMG - Ricostruzione di superfici confronto alphashape e vonoi.png]]
la **triangolazione alpha** è sempre un **sotto insieme** della [[Tasselizazione di Voronoi|triangolazine di delauny]] infatti un alto modo per costruirla è partire da una [[Tasselizazione di Voronoi|triangolazine di delauny]] e togliere i triangoli che hanno un **circoncerchio** con un raggio maggiore di $\alpha$ si ottiene la **triangolazione alpha**

il [[poliedro]] ottenuto dalla **triangolazione alpha** è detto **alpha complex** e **non** è un [[Poliedro|poliedro]] [[Convessita|convesso]], infatti ci sono delle sacche e sono possibili die buchi
![[IMG - Ricostruzione di superfici confronto tra alpha shape e voronoi.png]]
scegliendo un numero finito di raggi $\alpha$ con $\alpha_0 < \dots<\alpha_n$  questi tutte le possibili **alpha complex** ottenibili con quei trashold che sono al massimo $2n^2-5n$.

In 3D **alpha complex** è un sotto insieme di una tasselizazione tedaedrale e quindi le [[Normale di una superfice discreta (Mesh poligonali)|normali]] sono orientate a caso e spesso è **non** 2-[[Manifolds (Varieta)|manifod]] 
![[IMG - Alpha complex in 3D.png]]

Ci sono delle condizioni di sampling per cui la mesh generata con $\alpha$ è un [[Manifolds (Varieta)|manifold]]-2 e    
**siano** un [[Manifolds (Varieta)|manifold]] $M$ e un campionamento $S$, e indicando con $B(\mathbf{x},\alpha)$ una palla centrata in $x$ di raggio $\alpha$
**se**
1. per ogni centro $x \in \mathbb{R}^n\text{, }B(x,\alpha)\cap M$ se non è vuota deve essere omeomorfa ad un disco 
2. per ogni centro $x \in M\text{, }B(x,\alpha)\cap S\neq\emptyset$,
**allora** lo $\alpha$-shape di $S$ è omeomorfo a $M$.
![[IMG - Alpha shape sampling condition.png]]
Questa proprietà garantisce che ogni palla di raggio $\alpha$ “vede” porzioni di $M$ semplici (omeomorfe a dischi) e che non ci siano regioni del manifold prive di punti di $S$. In tal modo viene preservata la topologia di $M$ nel complesso costruito sul campionamento.





