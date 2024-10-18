---
Course: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Rappresentazione di modelli 3D]]"
SubTopic:
---

# Point Cloud
---
Le __Point cloud__(__nuvole di punti__) sono un modo per [[Rappresentazione di modelli 3D|rappresentare oggetti in 3D]] .
Una __nuvola di punti__ è definita come una collezione di sample da una superfice, L'[[Insiemi Matematici|insieme]] e completamente destrutturato, ovvero non c é nessun informazione di connessione tra i punti.
Ogni ponto è rappresentato da un __surfel__ (surface element) quest descrive una piccolo pezzo della superfice e ha dati come 
- la posizione $p(x,y,z)$ 
- la [[Normale di una superfice|normale]] 
- il colore
- La dimensione del disco
![[Pasted image 20240224030942.png]]
La dimensione del disco varia con la densità di punti, la distanza dal osservatore e la curvatura della superfice. 
![[Pasted image 20240224030548.png]]
I punti possono avere del numero o degli Outliner a seconda di come questi sono generati 

Si possono generare le __nuvole di punti__ partendo dalle [[Acquisizione modelli 3D dal mondo fisico|Acquisizione dal mondo reale]] 
![[Pasted image 20240224030414.png]]


#### Pro e contro
questo modo di rappresentare gli oggetti è comodo siccome è facile fare le acquisizione ed è facile da raddrizzare su una GPU siccome usa solo l [[Computer grafica - Primitive algebriche|primitiva]] punto.

dal punto di vista matematico non definiscono una [[Superfici|superfice]] e quindi è difficile capire se un altro punto e o non è al interno del oggetto

dal punto di vista algoritmo non formano un grafo non si puo dare una nozione di vicinato, il che pure rendere difficile scrivere degli algoritmi.

per via del rumore alcuni modelli verranno rindirizzati male