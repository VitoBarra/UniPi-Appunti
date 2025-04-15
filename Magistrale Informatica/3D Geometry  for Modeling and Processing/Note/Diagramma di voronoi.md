---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Diagramma di voronoi
---
Un diagramma di Voronoi è una partizione del piano determinata da un insieme finito di punti distinti, chiamati siti o generatori. Dato un insieme $S = \{p_1, p_2, \dots, p_n\} \subset \mathbb{R}^2$, ciascun punto $p_i$ genera una regione, detta cella di Voronoi, formata da tutti i punti del piano che sono più vicini a $p_i$ che a qualunque altro punto di $S$. Formalmente, la cella di Voronoi $V(p_i)$ associata al punto $p_i$ è definita come:

$$
V(p_i) = \{ x \in \mathbb{R}^2 \mid \forall j \neq i,\; \|x - p_i\| \leq \|x - p_j\| \}
$$

dove $\|x - p_i\|$ indica la distanza euclidea tra $x$ e $p_i$.

Il bordo tra due celle $V(p_i)$ e $V(p_j)$ è costituito dai punti equidistanti da $p_i$ e $p_j$, ovvero l'asse del segmento che li unisce. La frontiera complessiva del diagramma è quindi composta da segmenti e semirette che sono parti delle bisettrici dei segmenti tra i vari punti generatori.

Il diagramma di Voronoi è strettamente legato alla triangolazione di Delaunay, che è il duale del diagramma stesso: un arco tra due siti nel diagramma di Delaunay esiste se le rispettive celle di Voronoi condividono un lato. Questo legame permette di utilizzare proprietà geometriche delle triangolazioni per studiare i diagrammi di Voronoi, e viceversa.

Le celle di Voronoi sono sempre convessi poligoni (eventualmente non limitati) nel caso euclideo, e coprono l'intero piano senza sovrapposizioni. Inoltre, ogni vertice del diagramma (cioè ogni punto dove si incontrano più di due celle) è equidistante da almeno tre siti distinti.

Questa struttura è di grande interesse sia teorico che applicativo, trovando impiego in campi come la geografia, l'informatica, la robotica, la fisica computazionale e molti altri.

 
 ![[IMG - diagramma di voronoi.png]]
![[IMG - Diagramma di voronoi 2.png]]
Tutti i poliedri di voronoi sono [[Poliedro|poliedri]] [[Convessità|convessi]] perche sono intersezioni di semi spazzi

Il duale dei diagrammi di voronoi sono una triangolazione detta "triangoloazione di delloni"
![[IMG - Diagramma di voronoi triangolazione di veloni.png]]
ed è una bella triangolazione perche vale la proprieta del circoncerchio vuoto
![[IMG - Diagramma di voronoi proprita del circoncerchio vuoto.png]]
Il che indica il fatto che la triangolazione sia **bella**, questo avviene perche avere questa proprietà significa che tutti i triangoli siano piu o meno equilateri.

vale la proprita che per ogni coppia di triangoli si puo scambiare la diagonale e la lunghezza di questa resta invariata




La qualità geometrica e visiva di un diagramma di Voronoi dipende fortemente dalla distribuzione dei punti generatori. Se i punti sono distribuiti in modo irregolare o troppo vicini tra loro in certe zone, le celle risultano distorte, con dimensioni e forme molto variabili. In particolare, punti troppo vicini generano celle molto piccole, mentre regioni con pochi generatori presentano celle molto grandi e squilibrate. Per ottenere un diagramma armonioso, con celle regolari e ben proporzionate, è importante che i punti siano distribuiti in modo omogeneo sul dominio di interesse.
![[IMG - Diagramma di voronoi brutto.png]]
Una classe speciale di diagrammi, chiamati **diagrammi di Voronoi centroidali**, migliora questo aspetto. In un diagramma di questo tipo, ogni punto generatore coincide con il baricentro (cioè il centroide) della sua cella di Voronoi. Se si indica con $V(p_i)$ la cella associata al punto $p_i$, allora nel caso centroidale vale:

$$
p_i = \frac{1}{|V(p_i)|} \int_{V(p_i)} x \, dx
$$

dove $|V(p_i)|$ rappresenta l'area della cella e l'integrale restituisce la posizione del centro di massa della regione.

Questa condizione viene solitamente raggiunta attraverso un algoritmo iterativo, noto come **algoritmo di Lloyd**, che consiste nel calcolare il diagramma di Voronoi, determinare i centroidi delle celle, spostare i generatori nei rispettivi centroidi, e ripetere il processo fino alla convergenza. Il risultato finale è un diagramma con celle più uniformi, spesso utilizzato in problemi di quantizzazione, ottimizzazione spaziale, e campionamento uniforme.
![[IMG - procedura di loid.png]]


Il metodo di Lloyd è un algoritmo iterativo impiegato per ottenere diagrammi di Voronoi centroidali. Si parte con un insieme iniziale di punti generatori $S$ definiti in un dominio $\Omega$. Il procedimento prevede tre passi fondamentali da ripetere fino al raggiungimento della convergenza.

1. Si genera la tassellazione di Voronoi $V(S)$ associata all'insieme corrente di generatori all'interno del dominio $\Omega$.

2. Per ciascun sito $s_i \in S$, si calcola il centroide $p_i$ della corrispondente regione di Voronoi $V_i$, e si aggiorna la posizione del generatore spostandolo in $p_i$. Questo passaggio garantisce che il nuovo generatore sia esattamente il baricentro della regione che rappresenta.

3. Si verifica una condizione di arresto: se i nuovi siti soddisfano un criterio di convergenza (ad esempio, se lo spostamento totale dei punti è inferiore a una soglia prefissata), l'algoritmo termina. In caso contrario, si ritorna al primo passo e si ripete il processo.

Questo metodo tende a produrre una distribuzione di punti più regolare e, di conseguenza, una partizione dello spazio in celle di Voronoi più uniformi, rendendolo utile in molte applicazioni di ottimizzazione spaziale e clustering.






I metodi iterativi per la costruzione di un diagramma di Voronoi centroidale si basano sull’ottimizzazione della posizione dei punti generatori rispetto a una funzione di energia. L’idea di fondo è quella di spostare i generatori in modo tale da minimizzare un'energia associata alla distanza dei punti dal loro generatore, ponderata da una funzione di densità.

Una tassellazione di Voronoi centroidale (CVT, Centroidal Voronoi Tessellation) è una partizione in cui ogni punto generatore coincide con il centroide della propria regione di Voronoi. In presenza di una funzione di densità $\rho(x)$ definita nel dominio, il centroide della cella $V_i$ si calcola come:

$$
p_i = \frac{\int_{V_i} x \rho(x) \, dx}{\int_{V_i} \rho(x) \, dx}
$$

dove $\rho(x)$ è una funzione positiva che può rappresentare, ad esempio, una distribuzione di massa o importanza spaziale.

La configurazione CVT corrisponde al minimo della seguente funzione di energia:

$$
\mathcal{F}(S, \mathcal{V}) = \sum_{i=1}^{n} \int_{V_i} \rho(x) \, \|x - s_i\|^2 \, dx
$$

Questa espressione misura l'energia totale del sistema, e la minimizzazione di $\mathcal{F}$ porta a una distribuzione ottimale dei siti $s_i$, in modo che ogni generatore rappresenti al meglio, in media, i punti della propria regione.

Il valore minimo della funzione $\mathcal{F}$ si ottiene proprio quando ogni generatore si trova nel centroide della propria regione secondo la misura indotta da $\rho(x)$, ossia quando si è raggiunta una configurazione di Voronoi centroidale.



usando la [[Distanza geodetica|distanza geodesica]] ![[IMG - Diagramma di voronoi su superfici.png]]
per usare il metodo di loid bisogna definire i centroidi sulla superfiche che non è banale 
![[IMG - Diagramma di voronoi su un toro vincolando i semi sui bordi.png]]



una variante è usare una campo su cui pesare la distanza geodesica in modod da avere un sampling diverso,
![[IMG - Diagramma di voronoi non isotropico.png]]
questi sono sampling non isotropici
![[IMG - Diagramma di voronoi non isotropici direzione.png]]