---
Subject: "[[Computer Grafica (CG)]]"
Area: 
topic: "[[Rappresentazione di modelli 3D]]"
SubTopic: 
tags:
  - CG
---

# Mesh Poligonali
---
una __Mesh poligonale__ é un modo per [[Rappresentazione di modelli 3D|rappresentare un oggetto in uno spazio 3D digitale]] una [[Partizione di un insieme|partizione]] di un [[Superfici|superfice]] continua divisa in celle poligonali 
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

#### Classificazione mesh
border edge: uno spigolo non condiviso da due facce
border vertex: i vertici di un border edge

__Mesh chiusa__: una mesh senza_ border edges
__Mesh aperta__: una mesh con border edges.
 ![[Pasted image 20240220205524.png]]

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
![[Pasted image 20240220034225.png]]

#### Orientamento
i triangoli di una mesh $\mathcal{M}$ possono essere orientati in due modi diversi, orario e anti-orario. 
per scegliere l'orientamento basta guardare l ordine di specifica dei vertici nel insieme di connettività $\mathcal{K}$ .
due triangolo adiacenti che condividono dei vertici se hanno lo stesso orientamento dovranno avere l ordine di specifica dei vertici inverso 
![[Pasted image 20240220204312.png]]
un 2-manigolf ha tutte le facce orientate nello stesso modo.

Non tutte le mesh si possono orientare e queste sono dette mesh con un solo lato. 
![[Pasted image 20240220203830.png]]


#### Strutture dati per le mesh

##### Polygon soup
é  un array di $n$ __poligoni__ ed ogni poligono é  una array di posizioni + attributi.
é  un approccio molto semplice ma inefficiente siccome ogni vertice condiviso é duplicato per ogni poligono, questo lo rende anche difficile da aggiornare siccome per ogni aggiornamento di un vertice va aggiornato su tutti i poligoni che mantengono una copia di quel vertice.

##### Indexed Mesh
Si divide il concetto di vertice e poligono.
si mantiene un [[array|array]] di vertici detto __Geometry array__ e un array di poligoni
i Poligoni sono rappresentati come una sequenza di referenze ad i vertici nel __Geometry array__
![[Pasted image 20240220212013.png]]

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
 