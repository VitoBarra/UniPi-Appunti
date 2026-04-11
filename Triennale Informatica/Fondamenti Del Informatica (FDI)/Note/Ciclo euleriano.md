---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area:
SubTopic:
---
# Ciclo euleriano
---
Il [[Ciclo euleriano|ciclo euleriano]] è un ciclo di un [[Graph Theory|grafo]] che percorre ogni arco esattamente una volta. Un [[Graph Theory|grafo]] che ammette almeno un ciclo euleriano si dice euleriano.

Il [[Ciclo euleriano|cammino euleriano]] è un cammino che percorre ogni arco esattamente una volta senza imporre la coincidenza tra vertice iniziale e finale; ogni [[Ciclo euleriano|ciclo euleriano]] è quindi un cammino euleriano, ma non ogni cammino euleriano è chiuso.

Il [[Ciclo euleriano|ciclo euleriano]] riguarda gli archi, mentre il [[Ciclo Hamiltoniano|ciclo hamiltoniano]] riguarda i vertici.

Per un [[Graph Theory|grafo]] non orientato connesso, esiste un [[Ciclo euleriano|ciclo euleriano]] se e solo se ogni vertice ha grado pari.

Per un [[Graph Theory|grafo]] non orientato connesso, esiste un cammino euleriano aperto se e solo se esattamente due vertici hanno grado dispari; in tal caso il cammino inizia in uno di essi e termina nell'altro.

Per un [[Graph Theory|grafo]] orientato, esiste un [[Ciclo euleriano|ciclo euleriano]] se il [[Graph Theory|grafo]] è fortemente connesso sugli archi non isolati e ogni vertice soddisfa $\deg^+(v)=\deg^-(v)$. Esiste invece un cammino euleriano aperto se tutti i vertici, salvo al più due, soddisfano $\deg^+(v)=\deg^-(v)$, un vertice soddisfa $\deg^+(v)=\deg^-(v)+1$ e un altro soddisfa $\deg^-(v)=\deg^+(v)+1$.

La caratterizzazione euleriana è particolarmente utile perché fornisce un criterio necessario e sufficiente semplice, a differenza del caso [[Ciclo Hamiltoniano|hamiltoniano]], per cui non esiste una caratterizzazione altrettanto immediata.
