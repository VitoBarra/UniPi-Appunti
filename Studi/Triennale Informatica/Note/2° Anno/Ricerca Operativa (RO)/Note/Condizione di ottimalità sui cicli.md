---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Condizione di ottimalità sui cicli
---

>[!tip] #### osservazione
> Se ad un [[Albero di copertura|albero di copertura]] $T$ viene aggiunto un arco $(u,v) \not\in T$ si forma un ciclo (perché in $T$ esiste un cammino da $u$  a $v$)

### Teorema

si $T$ un albero di copertura

$T$ è un [[Albero di copertura|albero di copertura]] di costo minimo se e solo se per ogni arco $(u,v) \not\in T$ si ha $c_{uv} \geq c_{ij}$ per ogni arco $(i,j)$ appratente al ciclo ottenuto aggiungendo a $T$ l’arco $(u,v)$

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 2.png]]

![[Studi/Triennale Informatica/Note/2° Anno/Ricerca Operativa (RO)/Media/Untitled 1 1.png]]
