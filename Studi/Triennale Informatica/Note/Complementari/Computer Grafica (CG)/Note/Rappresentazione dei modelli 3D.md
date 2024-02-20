---
Course: "[[Computer Grafica (CG)]]"
Subject: Computer Grafica
Area: 
Topic: 
SubTopic: 
tags:
  - CG
---

# Rappresentazione dei modelli 3D
---
Un __modello 3D__ é una rappresentazione matematica di un oggetto che occupa uno spazio in un volume 3D. 

La rappresentazione di modello puo essere classificata in 2 modi
- __Boundary-Based__: si rappresenta la superfice di un oggetto 3D, ed e anche chiamata __b-rep__. Esempi comuni sono
	- [[Superfici|Superfici]] implicite
	- [[Superfici|Superfici]] parametriche
	- Mesh poligonali
- __Volume-Based__: si rappresenta il volume di un oggetto 3D. Esempi comuni sono 
	- Voxellization
	- Costructive solid Geometry

Il modo di rappresentare l'oggetto dipende dal contesto applicativo e dalle strategie usate per generare il modello. possono essere generati per [[Acquisizione modelli 3D dal mondo fisico|acquisizione del mondo reale]], software di modellazione 3D, Modellazione procedurale e Simulazioni 

### Mesh Poligonali
una __Mesh poligonale__ é una [[Partizione di un insieme|partizione]] di un [[Superfici|superfice]] continua divisa in celle poligonali 
Formalmente si ha che 
_Sia_ 
- $\mathcal{V}= \{ v_i \in \mathbb{R}^{3}\mid i=1\dots N_v \}$ un [[Insiemi Matematici|insieme]] di vertici (punti in $\mathbb{R}^3$)
- $\mathcal{K}$ un insieme di adiacenza tra vertici, ovvero come questi sono connessi
 _Allora_ la tupla $(\mathcal{V,K})$ é una __Mesh poligonale__ indicata con$\mathcal{M}$ 
![[Pasted image 20240220020323.png]]
I tipi di mesh piu comuni sono quelle triangolari e quelle quadrate. 
in fase di [[Algoritmi di renderizzazione|rendering]] le Mesh quadrate si scompongono sempre in triangoli siccome questi sono gli unici supportati, Questo perché sono per definizione planari e é facile calcolare la normale della superficie al interno del triangolo
![[Pasted image 20240220035554.png]]
![[Pasted image 20240220035614.png]]

#### Risoluzione di una mesh
una Mesh piu ha facce piu questa ha __Risoluzione__ alta, bisogna fare un trade off tra la qualita della rappresentazione del oggetto e le performance siccome avere piu facce significa dover fare piu calcoli.
![[Pasted image 20240220032636.png]]
La __Risoluzione__ puo essere adattiva ovvero si possono usare piu o meno facce in porzioni diversi della stessa mesh a seconda della necessita di dettagli
![[Pasted image 20240220035133.png]]


#### Ottimizzazione sulla rappresentazione 
Per ottimizzare il numero di vertici necessari per la rappresentazione della mesh si possono utilizzare __fan__ e __strip__ di vertici. Questi ci permettono di rappresentare lo stesso numero di triangoli evitando pero di salvare piu volte i vertici comuni a piu triangoli. Non sempre é  possibile applicare questa strategia.


Sia $\mathcal{M}$ una Mesh 
allora l [[Insiemi Matematici|insieme]] di tutti i vicini di un vertice $v$  nella Mesh é detto $1$-_ring_ del vertice ed é  definito come $$v_1(i)=\{j\mid \{ i,j \} \in\mathcal{K}  \}$$ e la [[Cardinalità di un insieme|cardinalita]] $|v_1(i)|$ é detta __grado__ o __valenza__ del vertice $v_i$ 
 

una __Strip di vertici__ é una sequenza di _vertici ordinati_ che rappresentano dei triangoli senza ambiguità $\{ v_0,v_1,\dots,v_n \}$ ed ogni triangolo $i$ é  rappresentato come $\{v_i,v_{i+1},v_{i+2}  \}$

un __Fan di vertici__ é una sequenza di vertici adiacenti tra loro che condividono sempre un vertice, ogni triangolo $i$ é rappresentato come $\{ v_0,v_{i+1},v_{i+2} \}$ con $v_0$ il vertice condiviso

per una __strip__ e per un __fan__ di $m$ triangoli il numero di vertici [[Statistica descrittiva - Dati Numerici#Media (definizione)|medio]] $\overline{v_t}$ per rappresentare un triangolo é $$\overline{v_t}=\cfrac{\sum^{m-1}_{i=1}1+3}{m}=\cfrac{m-1+3}{m}=1+\cfrac{2}{m} $$ e quindi per rappresentare $m$ triangoli servono $m+2$ vertici
![[Pasted image 20240220022932.png]]


#### Manifold
una superfice é un $2$-manifold se esiste una omomorfismo  da ogni punto di $\boldsymbol{p}$ ad un disco.

in pratica significa che  preso un disco di gomma possiamo puntarlo in un punto $p$ e farlo aderire a tutta la superfice.

per accertarsi che una superfice é  un 2-manifold si possono fare 2 controlli
1. __Edge Manifol__ ogni spigolo (edge) é  condiviso da una o due triangoli
2. __Vertex Manifold__ : prese due facce $f_a$ e $f_b$ che condividono un vertice $v_i$ ci si puo muovere dal $f_a$ a $f_b$ passando solo per $v_1(i)$. Ovvero possiamo raggiungere tutti i vertici passando solo per il vicinato del vertice condiviso senza ripassare sul quel vertice
![[Pasted image 20240220034236.png]]

due esempi di mesh che non sono manifold sono
![[Pasted image 20240220034225.png]]A

