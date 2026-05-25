---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Global attention
---

# Graph Transformer
Il **Graph Transformer** applica il paradigma dei [[Transformer|transformer]] al dominio dei grafi sostituendo o affiancando il [[Message Passing Neural Network (MPNN)|message passing]] locale con meccanismi di attenzione globale. L'idea centrale e che ogni nodo possa interagire direttamente con tutti gli altri, senza dover propagare l'informazione hop dopo hop lungo gli archi.

Se i nodi del grafo vengono trattati come token con feature $x_1,\dots,x_n$, il modello costruisce rappresentazioni in cui ogni nodo puo attendere globalmente tutti gli altri. Questo migliora la trasmissione di informazione a lungo raggio; operativamente, dipendenze lontane diventano accessibili in un solo strato di attenzione invece di richiedere una profondita proporzionale alla distanza sul grafo.

Il problema e che l'attenzione globale non incorpora automaticamente la topologia. Per questo si introducono **structural encodings**, cioe informazioni che descrivono la posizione del nodo nel grafo o la relazione tra coppie di nodi. Tra le scelte piu comuni ci sono autovettori del Laplaciano, statistiche di random walk e distanze relative. Questi encoding non sostituiscono il bias strutturale del message passing, ma cercano di reintrodurlo come informazione ausiliaria.

Molti modelli moderni usano una forma ibrida. Il ramo locale preserva il bias induttivo del grafo, mentre il ramo globale migliora la comunicazione a lungo raggio. Il costo principale resta la complessita dell'attenzione globale, che cresce tipicamente come $O(n^2)$ nel numero di nodi e limita la scalabilita su grafi grandi.

Proprieta chiave:
- portano l'attenzione globale dei transformer sui grafi
- migliorano l'accesso a dipendenze a lungo raggio
- richiedono structural encodings per reintrodurre informazione topologica
- spesso vengono usati in forma ibrida con message passing locale



## Graph transformer
Il **Deep Learning for Graph** incontra infine i transformer quando la comunicazione locale viene sostituita da self-attention globale. Se i nodi sono trattati come token con feature $x_1,\dots,x_n$, ogni nodo puo attendere direttamente tutti gli altri, migliorando il trasferimento di informazione a lungo raggio; il costo e che la topologia non e piu incorporata nativamente nell'operatore. Per questo si introducono structural encodings, per esempio autovettori del Laplaciano, random walk features o distanze relative, ma il bias strutturale resta piu debole di quello del message passing. I modelli ibridi, come GPS, combinano quindi un ramo locale e uno globale; operativamente, il compromesso principale e la complessita quadratica $O(n^2)$ dell'attenzione nel numero di nodi, in continuita con il quadro generale dei [[Transformer|transformer]] e piu specificamente dei [[Graph Transformer]]. ![[IMG - graph transofrmer.png]]
![[IMG - inductive bias.png]]
![[IMG - ML su grafi GPD.png]]
