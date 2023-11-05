---
type: nota
course: Computer grafica
topic: 
tags:
  - CG
Parent MOC: "[[Computer Grafica (CG)]]"
---


# Pipeline di Rasterizazione
---
la _pipeline di restirazione_ è un [[Algoritmi di renderizazione|algoritmi di rendering]] usato specialmente per il rendering di scene dinamiche, per funzionare usa una struttura a [[Forme di Parallelismo#Temporale Pipeline|pipeline]] 


la pipeline trasforma una sequenza di _primitive geometriche_ quali _punti_, _linee_, _triangoli_ e _poligoni_ in _pixel_ sullo schermo, genera quindi un [[Rappresentazione delle immagini#Raster Images|immagine rasterizata]]

Ogni _primitiva_ e rappresentata da dei vertici, 1 per il punto 2 per le linee, 3 per i _triangoli_
ogni _vertice_ è specificato dalle sole coordinate ma ad ogni vertice si possono aggiungere più attributi ad esempio il colore del vertice. In generale gli si puo dare qualsiasi attributo abbia senso per l applicazione.  
![[IMG_0723.jpeg]]
Le fasi della Pipeline _sono_:
_Per-Vertex trasformation_ : 
	in questa fase ogni vertice della scena viene trasformato in modo _user specific_ ovvero ogni vertice, con trasformazioni _lineare_ come rotazioni e traslazioni.
_Primitive Processing_:
	Prende in input i _vertici_ e le _primitive_ specificate per l utente e puo aggiungere delle primitive  _suddividendo_ delle primitive in primitive piu piccole
> [!tip] 
> in vecchie versioni questo stage era accorpato con il pretendente ed era chiamato _primitive assembly_

_Rasterization stage_:
	in questa fase trasforma le primitive nella sua versione rasterizata trasformando la _scena_ 3D in una rappresentazione _2D_ adatta allo schermo. 
	In questa fase vengo prodotto dei _Pixel_ con piu informazioni, ad esempio i dati si interpolazione del vertice, e questi sono chiamati _fragment_
_per-Fragment Computation_
	In questa fase ogni _fragment_ viene processato per determinare i valori finali del _fragment_
_ouput Computation_
	questa fase decide come i _Fragment_ sono combinati nel _framebuffer_ ,che è dove si sta costruendo l immagine, e determina il colore finale del _pixel_ corrispondente al _frament_



##### Costo computazionale
_sia_
- $n_v$ il numero di _vertici_
- $K_{tr}$ il costo della trasformazione di ogni vertice
- $m$ il numero di primitive
- $Ras(p_i)$ il costo della _rasterizazione_ della primitiva $p_{i}$
_allora_ il costo del intero processo è stimato da $$Cost(rast)=K_{tr}n_{v}+\sum^{m}_{i=0}Ras(p_{i})$$

	
