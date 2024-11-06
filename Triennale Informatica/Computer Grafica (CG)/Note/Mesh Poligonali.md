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
- __Realizzazione Geometrica__: dove ogni vertice è posizionato in uno spazio, anche detta parte geometrica continua.
- __Caratterizzazione Topologica__ : come gli elementi sono combinatoriamente connessi, anche detta parte combinatoria discreta.
In generale ogni forma può essere rappresentata in maniera diversa mantenendo una certa similarità geometrica ma cambiandone totalmente la aspetto topologico. Questo è importante siccome solo dal aspetto topologico possiamo attribuire alcune proprietà alla mesh come ad esempio la Manifoldness, i bordi, le componenti connesse e l orientabilità.
Questo ci permette di scegliere la rappresentazione topologica piu comoda per le operazioni che si vogliono fare sulla mesh preservando più o meno la parte geometrica e quindi l'estetica degli oggetti che si vogliono rappresentare. 



#### Bordi di una mesh
border edge: uno spigolo non condiviso da due facce
border vertex: i vertici di un border edge

__Mesh chiusa__: una mesh senza border edges
__Mesh aperta__: una mesh con border edges.
 ![[Pasted image 20240220205524.png]]



#### Manifoldness
una __mesh poligonale__ può essere un $2$-[[Manifolds|manifold]] 
![[Pasted image 20240220034236.png]]
Per controllare che la __mesh__ sia un $2$-manifold se valgono le due seguenti proprietà:
1. __Edge Manifold__ ogni spigolo (edge) é condiviso da massimo due triangoli
2. __Vertex Manifold__ : prese un numero arbitrario di facce $f_i$ che condividono un vertice $v_i$ (anche dette le facce incidenti a $v_i$) allora partendo dal vertice $v_i$ esiste una percorso sugli edge delle facce $f_i$ tale che questo tocchi tutti i vertici di tutte le facce $f_i$ senza ripassare per $v_i$. 
due esempi di mesh che non sono manifold sono
![[Pasted image 20240220034225.png]]

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



#### Rendering di mesh non triangolari
gli algoritmi usati nelle GPU per il [[Algoritmi di renderizzazione|rendering]] lavorano solo con mesh triangolari motivo per cui le __Mesh quadrate__ si scompongono sempre in mesh triangolari. questo anche perché sono per definizione planari ed é facile calcolare la normale della superficie al interno del triangolo
![[Pasted image 20240220035554.png]]



#### Attributi sulle mesh
ogni vertice oltre alla sua posizione ha degli attributi questi possono essere di qualsiasi natura, si puo scegliere che valore e che significato questi hanno.
Si puo fare l encodig di questi valori in modo diverso,
1. per vertex: sono nei vertici, é  il caso piu comune 
2. per faccia: sono nelle singole facce, poco usato


#### normale di una mesh Poligonale
Calcolare la [[Normale di una superfice|normale]] di una mesh poligonale é la normale alla superfice continua che la mesh sta rappresentando.
Avendo pero solo la superfice del poligono che stiamo rappresentando avremmo che la normale sara quella della superfice del poligono che rappresenta quella parte della superfice continua.
![[Pasted image 20240221001431.png]]
le faccie dei triangoli essendo piatte avranno una norma costante per tutti i punti della faccia.
possiamo calcolare la norma per-face, ovvero la calcoliamo una volta per un triangolo e poi la usiamo per tutti i punti della faccia. Fare cio pero porta ad enfatizare i singoli triangolo ed é solitamente qualcosa che si vuolte evitare
![[Pasted image 20240220225451.png]]
una soluzione a questo problema e calcolare la norma sui vertici e interpolare il valore della norma sui punti della faccia, questo riesce a dare dei risultati piu puliti. 
![[Pasted image 20240220225511.png]]

##### Norma per vertice
La [[Normale di una superfice|normale]] su un vertice puo essere in vari modi

come media tra tutte le normali delle facce che hanno quel vertice $$\boldsymbol{n}_v=\cfrac{1}{|S^{*}(v)|}\sum_{i \in  S^{*}(v)}\boldsymbol{n}_{f_i}$$
![[Pasted image 20240221002223.png]] 

Questa Assume che tutte le facce siano piu o meno di dimensione simile siccome piu facce piccole contribuiscono sulla media rispetto ad unica faccia grande
per risolvere questo problema si puo assegnare un peso ad ogni faccia faccia, in questo modo la formula diventa $$\boldsymbol{n}_v=\cfrac{1}{|S^{*}(v) Area(f_i)|}\sum_{i \in  S^{*}(v)}Area(f_i)\boldsymbol{n}_{v_i}$$
![[Pasted image 20240221003638.png]]
questa versione invece ha ancora il problema dei trangoli molto lunghi, la normale dovrebbe dipendere solo dei punti immediatamente vicini e quindi per correggere anche questo caso si usa la formula $$\boldsymbol{n}_v=\cfrac{1}{|S^{*}(v) \alpha(f_i,v)|}\sum_{i \in  S^{*}(v)}\alpha(f_i,v)\boldsymbol{n}_{v_i}$$ dove $\alpha$ é l angolo formato dal triangolo che contiene $v$
![[Pasted image 20240221003333.png]]


> [!Tip]
> nel caso medo la prima formula funziona bene siccome mediamente i triangoli sono di dimensioni simili.

Ci sono dei casi limite dove la norma per vertici non funziona. e questi sono i casi degli angoli delle mesh
![[Pasted image 20240221004039.png]]
In questo caso la normale non cambia in modo continuo ma c é un salto improvviso su parti delle superfici vicine.

Per gestire questo problema si possono calcolare 2 normali per vertice 
![[Pasted image 20240221004148.png]]
 per ogni vertice si sceglie se calcolare 1 o 2 normali basandosi su un angolo massimo  detto __crease angle__ che la superfice puo avere, se si supera quel angolo allo la mesh non é smooth e il vertice ha bisogno di due normali.

questa seconda normale puo essere memorizzata o in un vertice duplicato oppure nella faccia che ha quel vertice
![[Pasted image 20240221004411.png]]
 