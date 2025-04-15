---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
Course 2: "[[Computer Grafica (CG)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Indici Spaziali - Binary Space Partition-Tree (BSP)
--- 
I **Binary space partition** (**BSP**) so una [[Indici spaziali|indice spaziale]] di tipo **gerarchico** basati su un [[Struttura dati - Alberi binari|alberi binari]]

Si costruisce un **albero binario** [[Partizione di un insieme|partizionando]] ricorsivamente lo spazio mediante l aggiunta di iperpiani ad ogni step fino a che ogni primitiva o un numero costante di primitive appartengono ad una sola regione. 
Per via del fatto che si divide in semi spazzi ogni nodo dell'albero corrisponde sempre a una regione [[Convessità|convessa]].  
![[IMG - Indici spaziali BSP.png]]
Per quanto riguarda la query che verifica se un punto $p$ è all'interno di una primitiva, il processo inizia dalla radice dell'albero. Si procede spostandosi verso il figlio associato al semispazio che contiene il punto $p$.
![[IMG - indici spaziali BSP ricerca.png]]
Il costo computazionale del accesso ai semi spazzi e quindi alla primitive dipende dalla struttura dell'albero. In particolare un buna performance si ottiene con un albero bilanciato, infatti considerando $n$ in numero di nodi il
- *caso medio*: $O(\log n)$
- caso pessimo:  $O(n)$

Il **caso peggiore** avviene siccome non è garantito che si possa costruire un albero bilanciato, infatti non è neanche garantito che si possa creare un albero che separi esattamente ogni oggetto. A seconda di come gli oggetti sono distribuiti potrebbe essere necessario suddividerli per partizionare lo spazio, il che al caso pessimo porta ad alberi lineari e quindi a [[complessita|complessita]] $O(n)$
![[IMG - BSP Costruzione.png]]
Mentre per altre query come individuare la [[Computer grafica - Primitive Geometriche|primitiva]] piu vicina non è detto che basti discendere l albero in quando si potrebbe accedere ad una regione che non contiene la primitiva piu vicina, infatti per assicurarsi di trovarla bisogna risalire l albero e vedere anche le regioni adiacenti, in caso pessimo questo rende la complessità $\mathcal{O}(n)$. 


Nella costruzione di un **BSP-Tree** la scelta del piano di partizionamento è cruciale.
Una strategia comune prevede di utilizzare una delle primitive stesse come piano di splitting, decomponendo le altre rispetto ad essa.  

Il costo di costruzione del **BSP-Tree** dipende fortemente da come viene scelto il piano di partizionamento e la scelta puo essere fatta in base al obbiettivo che può essere
- Bilanciare l'albero
- Minimizzare il numero di split 
 generalmente questi due obbiettivi sono ortogonali l'uno al altro e si cerca quindi un bilanciamento a seconda delle necessita. 
Il costo $C(T)$ di un albero può essere espresso come:  $$ C(T) = 1 + \mathcal{P}(T_L) \, C(T_L) + \mathcal{P}(T_R) \, C(T_R) $$ dove $\mathcal{P}(T_L)$ e $\mathcal{P}(T_R)$ rappresentano le [[Definizione di Probabilita|probabilità]] di visitare i sottoalberi sinistro e destro.  

Per scegliere la [[Variabili Aleatorie Notevoli - Geometrica|primitiva]] per lo splitting ottimale, si può quindi stimare il costo [[Problemi di ottimizzazione|minimizzando]] una funzione che tiene conto del numero di primitive nei sotto alberi ($S(T_L)$ e $S(T_R)$) e di quelle divise ($s$). Si vuole quindi minimizzare:  $$ \frac{1}{1+|S(T_L)|} \alpha + |S(T_R)| \alpha + \beta s $$ dove $\alpha$ e $\beta$ sono degli iperparametri che influenzano la struttura dell'albero:
- alto $\alpha$ e basso $\beta$  favoriscono un albero bilanciato, 
- alto $\beta$ e basso $\alpha$ tende a ridurre in numero di split, producendo un albero più compatto.  