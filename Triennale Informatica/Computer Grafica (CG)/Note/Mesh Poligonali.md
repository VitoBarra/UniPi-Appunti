---
Course: "[[Computer Grafica (CG)]]"
Course 2: "[[3D Geometry for Modeling and Processing (3GMP)]]"
Area: 
topic: "[[Rappresentazione di modelli 3D]]"
SubTopic: 
tags:
  - CG
---

# Mesh Poligonali
---
una __Mesh poligonale__ é un modo per [[Rappresentazione di modelli 3D|rappresentare un oggetto in uno spazio 3D digitale]] una [[Partizione di un insieme|partizione]] di un [[Superfici|superfice]] continua divisa in celle [[Poligoni|poligonali]], ovvero è un [[Complesso di celle (Cell Complex)|complesso di cell]]. I tipi di mesh piu comuni sono le __mesh triangolari__  dove quelle ben formate sono un  [[Complesso di celle (Cell Complex)|2-complesso simpliciale massimale]] o le __mesh quadrangolari__ 

Formalmente si ha che  
__Sia__ 
- $\mathcal{V}= \{ v_i \in \mathbb{R}^{3}\mid i=1\dots N_v \}$ un [[Insiemi Matematici|insieme]] di vertici (punti in $\mathbb{R}^3$)
- $\mathcal{K} \subset \mathcal{V} \times \mathcal{V}$ un insieme di adiacenza tra vertici, ovvero come questi sono connessi
 __Allora__ la tupla $(\mathcal{V,K})$ é una __Mesh poligonale__ indicata con $\mathcal{M}$ 
![[Pasted image 20240220020323.png]]
Considerando una mesh possiamo discriminare $2$ aspetti fondamentali:
- __Realizzazione Geometrica__: dove ogni vertice è posizionato in uno spazio, anche detta parte **geometrica, continua**.
- __Caratterizzazione Topologica__ : come gli elementi sono combinatoriamente connessi, anche detta parte **combinatoria, discreta**.
In generale ogni forma può essere rappresentata in maniera diversa mantenendo una certa similarità geometrica ma cambiandone totalmente la aspetto topologico. Questo è importante siccome solo dal aspetto topologico possiamo attribuire alcune proprietà alla mesh come ad esempio la [[Manifolds (Varieta)|Manifoldness]], i **bordi**, le **componenti connesse** e l **orientabilità**.
Questo ci permette di scegliere la rappresentazione topologica piu comoda per le operazioni che si vogliono fare sulla mesh preservando il piu possibile la parte geometrica e quindi l'estetica degli oggetti che si vogliono rappresentare. 



#### Bordi di una mesh
border edge: uno spigolo non condiviso da due facce
border vertex: i vertici di un border edge

__Mesh chiusa__: una mesh senza border edges
__Mesh aperta__: una mesh con border edges.
 ![[Pasted image 20240220205524.png]]




#### Orientamento
i triangoli di una mesh $\mathcal{M}$ possono essere orientati in due modi diversi, orario e anti-orario. 
per scegliere l'orientamento basta guardare l ordine di specifica dei vertici nel insieme di connettività $\mathcal{K}$ .
due triangolo adiacenti che condividono dei vertici se hanno lo stesso orientamento dovranno avere l ordine di specifica dei vertici inverso 
![[Pasted image 20240220204312.png]]
un 2-manigolf ha tutte le facce orientate nello stesso modo.

Non tutte le mesh si possono orientare e queste sono dette mesh con un solo lato. 
![[Pasted image 20240220203830.png]]



#### Risoluzione di una mesh
una Mesh piu ha facce piu questa ha __Risoluzione__ alta, bisogna fare un trade off tra la qualità della rappresentazione del oggetto e le performance siccome avere piu facce significa dover fare piu calcoli.
![[Pasted image 20240220032636.png]]
La __Risoluzione__ puo essere adattiva usando usando gli adeguati [[Indici spaziali|indici spaziali]] si puo rappresentare lo stesso oggetto usando piu o meno facce in porzioni diversi della stessa mesh a seconda della necessita di dettaglio.
![[Pasted image 20240220035133.png]]


#### Ottimizzazione sulla rappresentazione 
Per ottimizzare il numero di vertici necessari per la rappresentazione della mesh si possono utilizzare __fan__ e __strip__ di vertici. Questi ci permettono di rappresentare lo stesso numero di triangoli evitando pero di salvare piu volte i vertici comuni a piu triangoli. Non sempre é  possibile applicare questa strategia.


Sia $\mathcal{M}$ una Mesh 
allora l [[Insiemi Matematici|insieme]] di tutti i vicini di un vertice $v$  nella Mesh é detto $1$-_ring_ del vertice ed é  definito come $$v_1(i)=\{j\mid \{ i,j \} \in\mathcal{K}  \}$$ e la [[Insiemi - Cardinalita|cardinalita]] $|v_1(i)|$ é detta __grado__ o __valenza__ del vertice $v_i$ 
 

una __Strip di vertici__ é una sequenza di _vertici ordinati_ che rappresentano dei triangoli senza ambiguità $\{ v_0,v_1,\dots,v_n \}$ ed ogni triangolo $i$ é  rappresentato come $\{v_i,v_{i+1},v_{i+2}  \}$

un __Fan di vertici__ é una sequenza di vertici adiacenti tra loro che condividono sempre un vertice, ogni triangolo $i$ é rappresentato come $\{ v_0,v_{i+1},v_{i+2} \}$ con $v_0$ il vertice condiviso

per una __strip__ e per un __fan__ di $m$ triangoli il numero di vertici [[Statistica descrittiva - Dati Numerici#Media (definizione)|medio]] $\overline{v_t}$ per rappresentare un triangolo é $$\overline{v_t}=\cfrac{\sum^{m-1}_{i=1}1+3}{m}=\cfrac{m-1+3}{m}=1+\cfrac{2}{m} $$ e quindi per rappresentare $m$ triangoli servono $m+2$ vertici
![[Pasted image 20240220022932.png]]






#### Attributi sulle mesh
ogni vertice oltre alla sua posizione ha degli attributi questi possono essere di qualsiasi natura, si puo scegliere che valore e che significato questi hanno.
Si puo fare l encodig di questi valori in modo diverso,
1. per vertex: sono nei vertici, é  il caso piu comune 
2. per faccia: sono nelle singole facce, poco usato


