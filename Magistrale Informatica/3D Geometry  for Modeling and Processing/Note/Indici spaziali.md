---
Course: "[[3D Geometry for Modeling and Processinga (3GMP)]]"
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

