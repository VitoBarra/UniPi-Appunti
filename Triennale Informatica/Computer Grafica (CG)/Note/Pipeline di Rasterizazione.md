---
Course: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Pipeline di Rasterizazione
---
la _[[Forme di Parallelismo#Temporale Pipeline|pipeline]]_ di rasterizazione è un [[Rendering|algoritmi di rendering]] usato specialmente per il rendering di scene _dinamiche_. 

un problema che risolve questo algoritmi e quello di trasformare una scena 3D in una 2D proiettata sullo schermo, crea una _rasterizzazione_, ovviamente scene gia in 2D restano in 2D

la _pipeline_ trasforma una sequenza di _[[Computer grafica - Primitive Geometriche|primitive geometriche]]_  in _pixel_ sullo schermo, genera quindi un [[Rappresentazione delle immagini#Raster Images|immagine rasterizata]]  
![[IMG_0723.jpeg]]
Le fasi della Pipeline _sono_:
_Per-Vertex trasformation_ : 
	in questa fase ogni [[Computer grafica - Primitive Geometriche|vertice]] della scena viene trasformato in modo _user specific_ ovvero ogni vertice, con trasformazioni _lineare_ come [[Trasformazioni Lineari Geometriche|rotazioni e traslazioni]].
_Primitive Processing_:
	Prende in input i _vertici_ e le _primitive_ specificate per l utente e puo aggiungere delle primitive _suddividendo_ delle primitive in primitive piu piccole
_Rasterization stage_:
	in questa fase trasforma le primitive nella sua versione [[Rappresentazione delle immagini#Raster Images|rasterizata]] trasformando la _scena_ 3D in una rappresentazione _2D_ adatta allo schermo. 
	In questa fase vengo prodotto dei _Pixel_ con piu informazioni, ad esempio i dati si interpolazione del vertice, e questi sono chiamati _fragment_, [[Trasformare da Vertici a Frammenti (Rasterizazione)|Dettagli sul algoritmo usato]]
_per-Fragment Computation_:
	In questa fase ogni _fragment_ viene processato per determinare i valori finali del _fragment_
_output Computation_:
	questa fase decide come i _Fragment_ sono combinati nel _frame buffer_ ,che è dove si sta costruendo l immagine, e determina il colore finale del _pixel_ corrispondente al _fragment_

> [!tip] 
> in vecchie versioni della pipeline il __per-Vertex trasformation__ e il __primitive processing__ erano accorpati in un unico stage chiamato _primitive assembly_

il consto computazionale della rasterizazione si puo esprimere come
_sia_
- $n_v$ il numero di _vertici_
- $K_{tr}$ il costo della trasformazione di ogni vertice
- $m$ il numero di primitive
- $Ras(p_i)$ il costo della _rasterizazione_ della primitiva $p_{i}$
_allora_ il costo del intero processo è stimato da $$Cost(rast)=K_{tr}n_{v}+\sum^{m}_{i=0}Ras(p_{i})$$


#### Rendering di mesh non triangolari
gli algoritmi usati nelle GPU per il [[Rendering|rendering]] lavorano solo con [[Mesh Poligonali|mesh triangolari]] motivo per cui le __Mesh quadrate__ si scompongono sempre in mesh triangolari. questo anche perché sono per definizione planari ed é facile calcolare la normale della superficie al interno del triangolo
![[Pasted image 20240220035554.png]]
