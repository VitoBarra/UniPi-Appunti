---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Tasselizazione di Voronoi
---
Una **Tasselizazione di Voronoi** (**VT**) è una [[Partizione di un insieme|partizione]] del [[Spazio Euclideo|piano]] determinata da un insieme finito di punti distinti. 
**Data**
- $\Omega$ un domino 
- $S = \{s_1, s_2, \dots, s_n\} \subset \Omega$ un [[Insiemi Matematici|insieme]] di punti  $p_i$ detti **semi** o **generatori**
- $d$ una [[Definizione di distanza|distanza]] 
**allora** una ***Tasselizazione di Voronoi**  è un [[Partizione di un insieme|partizionamento]] dello dominio $\Omega$ in $n$ regioni dette **cella di Voronoi** o **[[poliedro|poliedri]] di Voronoi** dove tutti i punti appartenenti alla regione sono i punti più vicini a $s_i$ che a qualunque altro punto di $S$. Formalmente le regioni sono definite:$$
V(s_i) = \{ x \in \Omega \mid \forall j \neq i,\; d(x ,s_i) \leq d(x, s_j) \}
$$

Prendendo il caso in cui il dominio $\Omega= \mathbb{R}^2$ Le regioni associate ai punti di $S$ si possono visualizzare con il  **diagramma di Voronoi**. I bordi tra due celle $V(s_i)$ e $V(s_j)$ sono costituiti dai punti equidistanti da $s_i$ e $s_j$, cioè da quei punti $x \in \mathbb{R}^2$ per cui vale $d(x, s_i) = d(x, s_j)$. La frontiera complessiva del diagramma è quindi composta da segmenti e, più in generale, da porzioni di [[Rette|rette]].
![[IMG - Diagramma di voronoi 2.png]]
Le **celle di Voronoi** risultano sempre **[[poligoni|poligoni]] [[Convessità|convessi]]**, eventualmente non limitati, nel caso in cui si adotti la distanza euclidea. Queste celle coprono completamente il piano, senza sovrapporsi e senza lasciare spazi vuoti. Ogni **vertice** del diagramma, ovvero ogni punto in cui si incontrano tre o più celle, è equidistante da almeno tre semi distinti.

Il **diagramma di Voronoi** ha un grafo duale che si può costruire connettendo due semi $s_i$ e $s_j$ se esiste un lato in comune tra le rispettive celle $V(s_i)$ e $V(s_j)$. Il grafo risultante è chiamato **triangolazione di Delaunay**.
![[IMG - Diagramma di voronoi triangolazione di veloni.png]]
La triangolazione di Delaunay è considerata una **buona triangolazione** perché soddisfa la cosiddetta **proprietà del circoncerchio vuoto**: per ogni triangolo della triangolazione, il suo **circoncerchio** non contiene alcun altro seme nel suo interno.
![[IMG - Diagramma di voronoi proprita del circoncerchio vuoto.png]]
Questa proprietà implica che i triangoli della triangolazione tendano a essere quanto più possibile **equilateri**, evitando triangoli allungati e degeneri. In questo senso si dice che la triangolazione è **bella**, perché ottimizza la forma dei triangoli in termini geometrici.

in piu se vale la **proprietà del circoncerchio vuoto** si ha per ogni coppia di triangoli adiacenti che condividono una diagonale, è possibile **scambiare** (operazione detta *flip*) e la **somma delle lunghezze dei lati resta invariata**.


vale anche che data una **triangolazione NON di Delaunay** scambiando le diagonali si può arrivare ad una **triangolazione di Delaunay** e quindi a far valere la proprietà del **circoncerchio vuoto**.

Questo rende la **triangolazione di Delaunay** unica a meno di casi degeneri e localmente **ottimale** rispetto al criterio delle lunghezze delle diagonali.




La qualità geometrica e visiva di un **diagramma di Voronoi** dipende fortemente dalla distribuzione dei **semi**. Se i punti sono distribuiti casualmente è molto facile ottenere punti troppo vicini tra loro che generano celle con dimensioni e forme molto variabili.  Per ottenere un diagramma armonioso, con celle regolari e ben proporzionate, è importante che i punti siano distribuiti in modo omogeneo sul dominio di interesse.
![[IMG - Diagramma di voronoi brutto.png]]

### Tasselizazione di Voronoi centroidali
le **Tasselizazione di Voronoi centroidali** (**CVT**) sono delle **tasselizazioni di voronoi** dove i semi coincidono con il centroide della cella, formalmente si ha che 
**sia** 
- $S = \{s_1, s_2, \dots d, s_n\} \subset \Omega$ l insieme dei **semi**
- $V(s_i)$ la **cella di voronoi** associata al punto $s_i$
-  $\rho(x)$  una funzione di densità definita nel dominio $\Omega$
**allora** vale che un seme è posizionato sul centroide quindi:$$
p_i = \frac{\displaystyle\int_{V_i} x \rho(x) \, dx}{\displaystyle\int_{V_i} \rho(x) \, dx}
$$e vale che una configurazione di questo tipo corrisponde al [[Massimi e minimi|minimo]] della seguente funzione di energia:$$
\mathcal{F}(S, \mathcal{V}) = \sum_{i=1}^{n} \int_{V_i} \rho(x) \, \|x - s_i\|^2 \, dx
$$questo tipo di **Tasselizazione** garantisce di essere **ben fatto** ovvero ha celle di dimensione uniforme.


per costruire una **Tasselizazione di Voronoi centroidali** a partire da **tasselizazione di voronoi** si usa un algoritmo iterativo, noto come **algoritmo di Lloyd**:
Sia $S$ l'[[Insiemi Matematici|insieme]] di punti definiti in un dominio $\Omega$
1. Si genera la tassellazione di Voronoi $V(S)$ associata all'insieme corrente di generatori all'interno del dominio $\Omega$.
2. Per ciascun $s_i \in S$, si calcola il centroide $p_i$ della corrispondente regione di Voronoi $V_i$, e si aggiorna la posizione del seme $s_i$ spostandolo in $p_i$.
3. Si verifica una condizione di arresto: se i nuovi siti soddisfano un criterio di convergenza (ad esempio, se lo spostamento totale dei punti è inferiore a una soglia prefissata), l'algoritmo termina. In caso contrario, si ritorna al primo passo e si ripete il processo.
Questo metodo tende a produrre una distribuzione di punti più regolare e, di conseguenza, una partizione dello spazio in **celle di Voronoi** più uniformi.
![[IMG - procedura di loid.png]]
Questo metodo tende a convergere lentamente e a tasselizazione troppo regolare.


#### Tasselizzazione di voronoi su superfici
Quando invece il dominio è una [[Superfici|superfice]] $\Omega=R \subseteq \mathbb{R}^3$ è facile definire una **[[Tasselizazione di Voronoi|tasselizazione di Voronoi]]** semplicemente usando come distanza $d$ la [[Distanza geodetica]]  mentre è più difficile costruire una **tasselizazione di voronoi centroidale** a partire da quella **Tasselizazione di Voronoi**.

Infatti, per usare l'**[[algoritmo di Lloyd|algoritmo di Lloyd]]** bisogna definire il modo di calcolare il baricentro, ma questo non è ben definito in quanto il **centrolde** geometrico di una regione $R$ può trovarsi all’esterno della superficie stessa. In formule, se consideriamo
$$
\mathbf{c} = \frac{1}{|R|} \int_R \mathbf{x} \, dA
$$
è possibile che $\mathbf{c} \notin \Omega$, il che rende il metodo inapplicabile direttamente.

per risolvere questo problema si usa la [[Distanza euclidea|distanza euclideiana]] $d=\|x-y\|$ definisce il centroide come il minimo della somma delle distanze al quadrato da tutti i punti della regione:$$
p^*_i = \arg\min_{p \in \Omega} \int_{V_i} \| \mathbf{x} - p \|^2 \, dx
	$$ed è garantito che $p^*\in \Omega$, minimizzare questa è una [[Quadratic optimization Problem|funzione quadratica]] che si può calcolare in tempo costante e poi si puo applicare a tutti i punti della superficie, che quindi nel caso discreto delle [[Mesh Poligonali|Mesh]] diventa di [[complessita|complessita]] lineare nel numero di punti.


Un alternativa è usare la [[distanza geodetica|distanza geodetica]] è prendere come centroide il punto con distanza massima dal bordo della regione $V_i$


Quando la superficie ha un bordo, come nel caso di superfici aperte o con confini, è inoltre utile **vincolare i semi posti sul bordo** a rimanere fissi durante i passi dell'algoritmo. Questo evita distorsioni nella struttura della tassellazione dovute al movimento dei punti lungo direzioni non ammissibili.
![[IMG - Diagramma di voronoi su un toro vincolando i semi sui bordi.png]]

È possibile **modificare la distribuzione spaziale delle celle** introducendo un **bias** nella costruzione del diagramma di Voronoi. Questo si ottiene controllando la **densità** del pattern tramite un campo scalare $\rho(\mathbf{x})$, il quale viene utilizzato per pesare la [[distanza geodetica|distanza geodetica]]. La distanza effettiva diventa quindi:$$
d_\rho(p, \mathbf{x}) = \rho(\mathbf{x}) \cdot d_{\text{geo}}(p, \mathbf{x})
$$In questo modo, le regioni del dominio in cui $\rho$ è maggiore avranno una tassellazione più fine, adattando la struttura del diagramma alle caratteristiche locali della superficie.
![[IMG - Diagramma di voronoi non isotropico.png]]
un altro modo riguarda **l’orientamento e la forma delle celle** del diagramma. Non solo la densità, ma anche **l'anisotropia** può essere controllata. Questo si ottiene introducendo un **campo di frame locali** (frame field), che definisce le direzioni preferenziali in ogni punto della superficie. Tale approccio consente di **deformare le celle di Voronoi** lungo direzioni specifiche.
![[IMG - Diagramma di voronoi non isotropici direzione.png]]









