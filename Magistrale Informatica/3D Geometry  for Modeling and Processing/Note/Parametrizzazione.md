---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Parametrizzazione
---
La **parametrizzazione** è il processo mediante il quale una [[Superfici|superficie]] 3D viene trasformata in una rappresentazione 2D. 

Formalmente, 
**sia**
- $S \subset \mathbb{R}^3$ il una [[Superfici|superficie]]
- $\Omega \subset \mathbb{R}^2$ lo spaio dei parametri 
una **parametrizzazione** è una [[Funzioni|funzione]]$$f: \Omega \rightarrow S \quad \quad \quad f(u,v) = (x,y,z)$$Il problema di **trovare una parametrizzazione** consiste nel trovare l'[[inverso di una funzione|inverso]] della parametrizzazione $$f^{-1}: S \to \Omega \quad \quad \quad f (x,y,z) =(u,v)$$dove la notazione distinta:
- $u$ e $v$ per le coordinate nel parametriche 
- $x$, $y$, $z$ per le superfici 
è usata per evitare ambiguità 
![[IMG - visualizazione parametrizazione.png]]
 la mappatura introdurrà della **[[Parametrizzazione - Distorsione|distorsione]]** che deve essere mantenuta  entro certi limiti per definirsi accettabile. Per fare ciò va tenuto conto del fatto che le **superfici chiuse**, non ammettono una **parametrizzazione** continua senza introdurre **distorsione** ed è quindi necessario introdurre dei **tagli**, questi permettono di abbassare la distorsione totale introducendo punti di non continuità.![[IMG - parametrizazione tagli.png]]scegliere come fare i tagli è una delle problematiche del **trovare  una parametrizzazione**

> [!tip]
> In teoria, potremmo ridurre la distorsione a zero introducendo un numero arbitrariamente grande di tagli, ma in questo modo su ogni tagli ci sarebbe esattamente un triangolo è questo è problematico per il [[texture mapping|texture mapping]]


Per ogni [[Superfici|superficie]] non esiste una **parametrizzazione** unica e perfetta al problema della parametrizzazione. Ogni tecnica privilegia diversi aspetti alcuni di questi sono: distorsione angolare, area-preserving, conformità. Un problema famoso che mostra questa problematica è quello della **parametrizzazione** del globo che è una sfera ad una mappa nel piano 2D. ![[IMG - Parametrizzazione del globo terrestre.png]]
nel [[texture mapping|texture mapping]], ogni regione ottenuta da tagli sono chiamate **chart**. Queste corrispondono a regioni dell'immagine che vengono campionate durante il rendering per recuperare gli attributi come il colore.
![[IMG - Parametrizazione del coniglietto di stenford.png]]
La **parametrizzazione** non è soltanto guidata dalla geometria della mesh, ma anche dalla sua semantica. Un approccio semanticamente coerente alla parametrizzazione consente di mantenere coese parti significative dell’oggetto (ad esempio la bocca, la pelle o un arto) facilitando operazioni di colorizzazione artistica o manipolazioni successive.![[IMG - parametrizazoine semantica.png]]

la **parametrizzazione** può essere usata anche [[Meshing e il Remeshing|remeshing]]. Se si ottiene una **parametrizzazione** globale di una mesh, è possibile definire una griglia regolare sul dominio 2D e trasferirla sulla superficie originale, ottenendo così una nuova mesh regolare![[IMG - parametrizazione per remeshing.png]] 
può anche essere usata per trasformare una [[Mesh Poligonali|mesh]] originale in una struttura quadrilaterale o esagonale.![[IMG - parametrizazioni per il remeshing.png]]
una **parametrizzazione** può anche essere usata per applicare tecniche derivati dall’[[Immage Processing|image processing]] al mondo tridimensionale.




le **parametrizzazioni**, dal punto di vista matematico devono essere **[[Applicazioni tra insiemi|bigettive]]**, nella pratica invece questo vincolo viene spesso volontariamente ignorato. infatti siccome si mantiene nei vertici $f^{-1}$ e non $f$ questo non crea problemi e puo essere sfruttato per mettere assieme nello spazio dei parametri delle informazioni riutilizzate
![[IMG -  bigettivita della parametrizazione caso pratico in cui non serve.png]]



 
Il numero di tagli necessari per fare una **parametrizzazione** senza interruzioni dipende in modo diretto dal [[Genus|genus]] $g$ della superficie. 

Per le superfici con $g=0$, un qualsiasi tagli o albero di taglio basta è  produce una superficie connessa
![[IMG - tagli con superfice con genus 0.png]]
All'aumentare del [[genus|genus]], come nel caso di un toro ($g=1$), la quantità di tagli cresce. 

![[IMG - tagli con superfice con genus 1.png]]
Generalizzando, per una superficie chiusa con genus $g$ sono necessari almeno $2g$ tagli per ottenere una superfice continuamente conessa.
![[IMG - tagli su superfice con genus 3.png]]
![[IMG - tagli su superfice complessa genus 6.png]]


Le strategie per effettuare questi tagli possono essere diverse. Alcuni approcci si basano su tagli non strutturati, guidati localmente dalla distorsione che si intende minimizzare. In altri casi, si utilizzano quad mesh coarse per decomporre la superficie in blocchetti quadrati, sfruttando la loro regolarità per facilitare l'interpolazione e la continuità tra le porzioni parametrizzate. Esistono anche approcci impliciti, nei quali la parametrizzazione è costruita direttamente attraverso una corrispondenza tra una mesh e una struttura cubica tridimensionale, come avviene nel caso delle cube map per la sfera.
![[IMG - tagli strategie generiche.png]]

Per poter eseguire operazioni di [[Meshing e il Remeshing|remeshing]], è fondamentale che la griglia definita nel dominio parametrico venga correttamente trasferita sulla superficie. Questo richiede che la continuità tangenziale sia mantenuta lungo i tagli (seams). In particolare, è necessario che le direzioni delle coordinate $u$ e $v$ siano correttamente allineate lungo i bordi dei tagli; in caso contrario, la griglia risultante potrebbe presentare discontinuità o distorsioni.
![[IMG - direzione della parametrizzazione non allineate sulla seams.png]]


![[IMG - direzione  della parametrizzazione allineate sulla sim.png]]

Per garantire la **smoothness globale** della parametrizzazione, è necessario posizionare con cura le **singolarità**. Le singolarità sono punti in cui la mesh quadrilatera non ha la struttura regolare di quattro quadrati attorno a ciascun vertice. Se ne distinguono due tipi: 
- **vertici blu** vi sono solo tre quadrati (singolarità di deficit),
- **vertici rossi** ne troviamo cinque o più (singolarità di eccesso). 
Questi punti corrispondono a regioni dove la [[Curvatura Gaussiana|Curvatura Gaussiana]] è diversa da zero: positiva nelle singolarità blu e negativa in quelle rosse.

![[IMG - buon posizionamento delle singolarita.png]]
La distribuzione delle singolarità segue vincoli imposti dalla geometria intrinseca della superficie. Secondo il [[Teorema di Gauss-Bonnet|teorema di Gauss-Bonnet]], l'integrale della curvatura gaussiana su tutta la superficie è proporzionale al genus $g$. Questo implica che, conoscendo il genus della superficie, è possibile determinare il numero totale e la somma dei difetti angolari delle singolarità necessarie a rappresentare correttamente la curvatura complessiva della superficie. In tal modo, la curvatura può essere "concentrata" solo in un numero limitato di punti, rendendo le restanti regioni localmente sviluppabili e dunque più facili da parametrizzare.
