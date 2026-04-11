---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area:
SubTopic:
---
# Ciclo Hamiltoniano
---
Il [[Graph Theory|ciclo hamiltoniano]] è un ciclo di un [[Graph Theory|grafo]] che visita tutti i vertici esattamente una volta, salvo la coincidenza tra vertice iniziale e finale. Un [[Graph Theory|grafo]] che ammette almeno un ciclo hamiltoniano si dice hamiltoniano.

Il [[Graph Theory|cammino hamiltoniano]] è invece un cammino che visita tutti i vertici esattamente una volta senza imporre il ritorno al vertice iniziale; ogni [[Ciclo Hamiltoniano|ciclo hamiltoniano]] contiene quindi un cammino hamiltoniano, ma il viceversa non vale in generale.

Il [[Ciclo Hamiltoniano|ciclo hamiltoniano]] riguarda i vertici, mentre il [[Ciclo euleriano|ciclo euleriano]] riguarda gli archi. Le due nozioni sono indipendenti: un [[Graph Theory|grafo]] può essere hamiltoniano senza essere euleriano e può essere euleriano senza essere hamiltoniano.

Se un [[Graph Theory|grafo]] è hamiltoniano, allora è connesso e ogni suo vertice ha grado almeno $2$; queste condizioni sono necessarie ma non sufficienti.

Due criteri sufficienti classici sono i seguenti:
- Teorema di Dirac: se $G$ è un [[Graph Theory|grafo]] semplice con $n\geq 3$ vertici e $\deg(v)\geq n/2$ per ogni vertice $v$, allora $G$ è hamiltoniano.
- Teorema di Ore: se $G$ è un [[Graph Theory|grafo]] semplice con $n\geq 3$ vertici e per ogni coppia di vertici non adiacenti $u,v$ vale $\deg(u)+\deg(v)\geq n$, allora $G$ è hamiltoniano.

Il problema di stabilire se un [[Graph Theory|grafo]] ammetta un [[Ciclo Hamiltoniano|ciclo hamiltoniano]] è computazionalmente difficile; per questo il concetto è centrale in molti problemi di ottimizzazione combinatoria.

In un [[Grafo bipartito|grafo bipartito]] ogni ciclo ha lunghezza pari; di conseguenza un [[Ciclo Hamiltoniano|ciclo hamiltoniano]] può esistere solo se il numero dei vertici è pari e, nel caso connesso, le due parti della bipartizione hanno la stessa cardinalità.
