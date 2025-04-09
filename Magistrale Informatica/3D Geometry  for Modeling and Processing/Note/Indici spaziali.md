---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Indici spaziali
---
Spazio l index:

Affrontare dal lato continuo della mesh e non da quella combinatoria.

Servono a rispondere a domande diverse rispetto alle query combinatorie. ad esempio capire i punti di intersezioni o la selezione con un interfaccia utente.


Utili anche per fare simulazione fisica.
![[IMG - Indici spaziali griglia uniforme 1.png]]

 ![[IMG - Indici spaziali griglia uniforme.png]]
si usano strutture dati che permettono di capire le collisioni in tempi sub logaritmi quasi costanti.


le strutture si dividono non genrarchiche e gerarchiche.


le non gerarchiche ha senso avvolte in caso in cui l overhead di gestire una struttura piu grande supera la non ottimalita che danno queste strutture.


quella non gerarchica costruisce3 una griglia con celle uniformi , ogni cella mantiene i riferimenti a tutte le primitive che toccano quella cella. 


La griglia occupa molta memoria e ciò non è buona anche per la cache.


per risolverla si utilizzza una funzione di hashing 
spagina hashi. Trovare la dimensione delle cellu non è facile e il che viene risulto cn le strutture gerarchiche.

Hierarchical Indexing:



BSP. vengon usati in DOOM
Binari space partitionTree:
si divide uno spazio con un piano e ogni meta è un nodo di un albero. finche ogni nodo ha una sola primitiva
Query con albero bilanciato




Importante la scelta del puano, ortogonalmente si possono scegliere un piano che agilità per la divisone per massima re  la profondità o il bilanciamento


kD-Tree:
Specializzazione di BSP dove ogni piano è allineato a gli assi.



Quad_Tree: 
Si divide la regione in 4 parti uguali nel caso 2D o in 8 in caso 3D 

memorizzazione con Z ordering per ottimizzare sulle cache.

tutte cose viste anche in computer grafica.

![[IMG - Occupazione in griglia.png]]



![[IMG - Spatial hashing.png]]Nel contesto dell'intersezione con un raggio all'interno di strutture spaziali come le griglie uniformi o l'hashing spaziale, il procedimento prevede inizialmente l'identificazione di tutte le celle attraversate dal raggio. Per ogni cella individuata, si esegue un test di intersezione con i primitivi contenuti in essa. Un'accortezza importante per ottimizzare le prestazioni è l'uso del cosiddetto "mailboxing", che serve a evitare test multipli sugli stessi primitivi già verificati.

Dal punto di vista computazionale, nel caso peggiore il costo di questo processo è 
$$
\mathcal{O}(\#cells + n)
$$
dove $n$ è il numero totale di primitivi. In media, invece, il costo diventa 
$$
\mathcal{O}(d\sqrt[d]{\#cells} + \sqrt[d]{n})
$$
dove $d$ rappresenta la dimensionalità dello spazio.

La griglia uniforme è una delle strutture più semplici da implementare. L'occupazione di memoria è data da 
$$
\mathcal{O}(\#cells + n)
$$
Tra i vantaggi principali troviamo la semplicità di implementazione e la rapidità nelle query. Tuttavia, presenta degli svantaggi significativi: è piuttosto esosa in termini di memoria e le sue prestazioni dipendono fortemente dalla distribuzione spaziale dei primitivi. Se questi ultimi non sono distribuiti in modo uniforme, la griglia può diventare inefficiente.

L'hashing spaziale offre un'alternativa alla griglia uniforme, mantenendo gli stessi costi teorici ma introducendo il rischio di collisioni nella funzione di hash. In tali casi, l'accesso a una cella può diventare 
$$
\mathcal{O}(\#cells)
$$
nel caso peggiore. L’occupazione di memoria, invece, è generalmente più contenuta: nel caso peggiore si memorizzano tutte le celle volumetriche, mentre in media si alloca memoria solo per le celle che intersecano le superfici.

Tra i vantaggi dello spatial hashing vi sono le query rapide (se la funzione di hash è ben progettata), la semplicità di implementazione e un consumo di memoria inferiore. Tuttavia, anche qui le prestazioni sono fortemente influenzate dalla distribuzione dei primitivi nello spazio, rendendo la struttura sensibile in contesti con alta densità o irregolarità.


![[IMG - scelta della cella.png]]




![[IMG - Indici gerarcici.png]]




## Binary space partition - tree
![[IMG - Indici spaziali BSP.png]]



![[IMG - BSP Costruzione.png]]

## KD - Tree

![[IMG - Indici spaziali KD-tree.png]]



![[IMG - KD-tree construction.png]]

![[IMG - Indici spaziali KD-tree query.png]]

# Quad-tree e Octa-tree
![[IMG - Indici spaziali quad-tree 2D.png]]

![[IMG - Indici spaziali Quad-tree uso per terreni.png]]


![[IMG - Octa-tree uso.png]]