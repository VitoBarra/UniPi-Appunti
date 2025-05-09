---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---
# Rigid matching di geometrie
---
**Rigid matching** è un problema fondamentale che attraversa diversi ambiti come la **computer vision**, il **pattern recognition** e la **computer graphics**. Si tratta del processo di determinare una **[[Trasformazioni Lineari Geometriche|trasformazione rigida]]**, ovvero le roto-traslazioni, che mappa un oggetto tridimensionale su un altro, mantenendo inalterate le distanze interne tra i punti. Tale trasformazione consente di confrontare, allineare o riconoscere forme in maniera coerente.

alcune applicazioni di questo sono
![[IMG- Applicazioni rigid matching.png]]
Un approccio classico e piuttosto intuitivo a questo problema è l’uso della [[Principal Component Analisys (PCA)|PCA]], L’orientamento dell’ellissoide fornisce un [[Frames|sistema di riferimento]] naturale che può essere usato per allineare due oggetti. Se entrambi sono trasformati in modo da allineare i propri assi principali con gli assi canonici ($x$, $y$, $z$), si ottiene un primo **allineamento rigido**.
![[IMG - rigid matching.png]]
Tuttavia, questo metodo presenta delle **criticità**. Ad esempio, se l’oggetto possiede **assi di simmetria**, l’ellissoide d’inerzia può risultare ambiguo: due configurazioni speculari possono produrre lo stesso risultato, portando ad allineamenti errati.

![[IMG - Registrazione di una superfice Problematicce PCA con assi di simetrica.png]]
Inoltre, quando gli **[[Autovettori e Autovalori|autovalori]]** sono molto simili (come nel caso di oggetti sferoidali o approssimativamente simmetrici), il sistema non è stabile, poiché piccoli disturbi nei dati possono produrre grandi variazioni negli assi calcolati.
![[IMG - PCA con oggetti con componenti principali simili.png]]
Un’ulteriore debolezza del [[Principal Component Analisys (PCA)]] emerge quando si tenta di confrontare oggetti **solo parzialmente simili**. Ad esempio, nel confronto tra una sedia e uno sgabello, lo schienale della sedia — che non ha controparte nello sgabello — viene trattato come parte del matching, distorcendo l’allineamento. In scenari di questo tipo, è necessario un approccio che sia in grado di distinguere tra **inlier** (punti compatibili tra le due forme) e **outlier** (differenze strutturali irrilevanti per l’allineamento).

![[IMG - Registrazione di una superfice PCA similarita parziale.png]]

Per affrontare i limiti della [[Principal Component Analisys (PCA)|PCA]] nel contesto del rigid matching, si adotta frequentemente il paradigma del **[[Random Sample Consensus (RANSAC)|Random Sample Consensus (RANSAC)]]**. gli approccio RANSAC in questo contesto consistono nel 
1. nel selezionare casualmente sottoinsiemi di punti da due superfici da allineare
2.  stimare per ciascun campione una trasformazione rigida
3. validare la trasformazione contando quanti punti trasformati risultano coerenti con la seconda superficie.
La trasformazione che massimizza il numero di **inlier** viene selezionata come soluzione ottimale, escludendo cosi i punti rumorosi.


Nel caso 2D, per stimare una traslazione è sufficiente identificare due coppie di punti corrispondenti. La trasformazione che allinea una curva all’altra è determinata da quattro punti: due appartenenti a un pezzo di curva, due all’altro. La distanza relativa tra i punti corrispondenti deve essere preservata:$$
||\mathbf{p}_1 - \mathbf{p}_2|| \approx ||\mathbf{p}_1' - \mathbf{p}_2'||.
$$![[IMG Rigid matching esempi in 2D coerenti e non coerenti.png]]
Nel caso 3D, invece. Sono necessarie almeno tre coppie di punti, quindi sei punti in totale. Tuttavia
![[IMG - numero di esempio necessari in rigid metching con RANSAC in 2D e3D.png]]
in entrambi i casi l'accuratezza della stima è fortemente influenzata dalla distribuzione spaziale dei punti scelti, infatti se i punti sono troppo vicini, la trasformazione stimata diventa instabile. Se sono distribuiti spazialmente in modo ampio, la stima è più robusta. 


la [[Definizione di Probabilita|Probabilità]] di trovare una tripletta valida in 3D in $N$ tentativi è $1-(1-p^3)^N$ che è relativamente basa, per aumentare questa probabilità ad ogni punto si aggiungono dei descrittori locali della superfice, che permette di considerare solo corrispondenze tra punti con **descrittori simili**. Questo approccio, noto come **feature point detection** 

Uno dei possibili descrittori è la **[[Normale di una superfice parametrica|normali]]**. In questo caso, ogni punto è definito come $(\mathbf{p}, \mathbf{n})$, con $\mathbf{n}$ normale alla superficie. Il matching tiene conto non solo della distanza tra punti, ma anche della coerenza angolare tra le normali.

Le condizioni matematiche fondamentali da rispettare includono:
1. **Distanza simile**:$$
\|\mathbf{p}_1 - \mathbf{p}_2\| \approx \|\mathbf{p}_1' - \mathbf{p}_2'\|.
$$
2. **Angoli tra direzione e normali invarianti**:
$$
\angle(\mathbf{n}_1, \mathbf{d}) = \angle(\mathbf{n}_1', \mathbf{d}'), \quad \angle(\mathbf{n}_2, \mathbf{d}) = \angle(\mathbf{n}_2', \mathbf{d}').
$$

3. **Angolo tra normali invariato**:
$$
\angle(\mathbf{n}_1, \mathbf{n}_2) = \angle(\mathbf{n}_1', \mathbf{n}_2').
$$

L’utilizzo di due punti con normali permette di ridurre la complessità computazionale del matching, in quanto fissa tutti i gradi di libertà della trasformazione rigida. Di conseguenza, il numero di tentativi necessari si riduce da $O(m^3)$ a $O(m^2)$ e La probabilità di successo del metodo è:
$$
1 - (1 - p^2)^N,
$$
dove $p$ è la probabilità di selezionare una corrispondenza corretta e $N$ è il numero di campioni testati.

La [[Trasformazioni Lineari Geometriche|traslazione]] può essere calcolata come:$$
t = \frac{\mathbf{p}_1' + \mathbf{p}_2'}{2} - \frac{\mathbf{p}_1 + \mathbf{p}_2}{2},
$$mentre la [[Trasformazioni Lineari Geometriche|rotazione]] $R$ allinea il sistema di riferimento $[\mathbf{n}_1, \mathbf{n}_2, \mathbf{d}]$ con il sistema $[\mathbf{n}_1', \mathbf{n}_2', \mathbf{d}']$.

![[IMG - Rigid matching con RAMSAC con featur point con normali.png]]

 un altro descrittore valido è la **[[Curvatura di una superfice|curvature principali]]**. Se le direzioni principali di curvatura $n_{1},n_2$ sono distinte, ovvero il punto non è su una sfera, il punto possiede una struttura locale sufficiente a determinare una trasformazione rigida da solo. In questo caso, è sufficiente un’unica corrispondenza per determinare la rototraslazione.
 
in questo modo si porta il numero di tentativi attesi da $O(m^2)$ a $O(m)$ e la probabilità di successo del metodo è:$$
1 - (1 - p)^N,
$$dove $p$ è la probabilità di selezionare una corrispondenza corretta e $N$ è il numero di campioni testati.

La [[Trasformazioni Lineari Geometriche|traslazione]] può essere calcolata come:$$
t = \mathbf{p}' - \mathbf{p},
$$mentre la [[Trasformazioni Lineari Geometriche|rotazione]] $R$ allinea il sistema di riferimento $[\mathbf{n},\mathbf{n}_1, \mathbf{n}_2]$ con il sistema $[\mathbf{n}',\mathbf{n}_1', \mathbf{n}_2']$.
![[IMG - Rigid matching di geometrie con RAMSAC con feature point ricchi, con curvatura.png]]
L’affidabilità nella stima delle curvature dipende fortemente dal rumore presente nei dati infatti questo approccio è raramente usato in pratica.

Quello che si ottiene da questa procedura è un rough aligment
![[IMG - Rigid matching di geometrie rough aligment.png]]