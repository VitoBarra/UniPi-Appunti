---
Course: "[[Computer Grafica (CG)]]"
Course 2: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - CG
Area: 
topic: 
SubTopic:
---

# Marching cube
---
il __marching cube__ è un **[[Algoritmi|algoritmo]]** per trasformare un [[Superfici implicite|rappresentazione implicita]] (campo salare) 3D in una [[Mesh Poligonali|mesh poligonale]].


è una versione della [[Marching Squere|Marching Squere]] in 3D si utilizza le celle sono cubiche e quindi il campo scalare puo essere ricostruito con [[Interpolazione Trilineare|Interpolazione Trilineare]] invece che quella [[Interpolazione Bilineare|lineare]]  ogni cubo avra $8$ vertici e quindi andrebbero definiti $2^8=256$ poligoni uno per ogni permutazione di possibili intersezioni. Pero queste possono essere ridotte ad un set piu piccolo di solo 14 ottenendo le mancanti per Rotazione o mirroring e complementazione 
![[IMG - Marcing cube cases.png]]
e per ognuna di queste combinazioni si puo tenere in una [[Struttura dati - Hash Table|hash table]] una triangolazione![[IMG - Marching cube lookUpTable.png]]
 Alcune delle problematiche del algoritmo: 
 - **consistenza**: **non** garantisce che la superficie risultante sia [[Continuità di una funzione|continua]] ($C^0$) o che possieda proprietà [[Manifolds (Varieta)|manifold]] corrette. Esistono configurazioni ambigue che, se non risolte mediante tecniche aggiuntive, possono generare superfici con errori topologici.
- **Correttezza**: mentre si presuppone un'interpolazione trilineare del campo, la superficie viene **approssimata** tramite facce triangolari.
- **Complessità della mesh**: il numero di triangoli generati dipende esclusivamente dalla densità di campionamento e non dalla reale complessità. Pertanto, anche superfici semplici come piani possono essere rappresentate con un numero eccessivo di triangoli.
- **Qualità di triangoli**: Quando l'[[Superfici implicite|isosuperficie]] passa molto vicino a due vertici adiacenti, si formano triangoli estremamente allungati e sottili.
 


I casi di ambiguità in 3D si verificano quando, su una stessa faccia del cubo, i vertici presentano valori sopra e sotto la soglia in modo non uniforme.  
![[IMG - Marching cube caso ambiguo.png]]  
Per gestire correttamente tali situazioni, le facce della cella devono essere trattate separatamente. Il controllo viene effettuato valutando il valore interpolato nel centro di ciascuna faccia, seguendo un principio analogo a quello adottato nel [[Marching Squere|marching squere]]. In base al valore ottenuto nel centro di ogni faccia, si seleziona una [[Struttura dati - Hash Table|look up table]] adeguata, che consente di disambiguare correttamente la topologia della superficie all'interno della cella.  
![[IMG -  hash di disembiguazione Marching cube.png]]
il calcolo dei valori del campo scalare nei centri serve solo quando la configurazione iniziale dei vertici lo rende indispensabile

La valutazione nei centri delle facce si basa sull'[[Interpolazione Trilineare|interpolazione trilineare]]. Nel caso specifico della faccia in cui $x=0$, la funzione interpolata assume la forma:$$
T(0, y, z) = c yz + f y + g z + h
$$Per individuare il punto critico sulla faccia, si calcolano le derivate parziali rispetto a $y$ e $z$, ponendole uguali a zero:

$$
\frac{\partial T(0, y', z')}{\partial y} = c z' + f = 0 \quad \Rightarrow \quad z' = -\frac{f}{c}
$$

$$
\frac{\partial T(0, y', z')}{\partial z} = c y' + g = 0 \quad \Rightarrow \quad y' = -\frac{g}{c}
$$

Questa procedura consente di determinare con precisione la posizione dei punti critici, migliorando l'accuratezza della ricostruzione della superficie anche in presenza di configurazioni ambigue. Un approccio analogo si applica alle altre facce, adattando opportunamente la forma della funzione interpolata in funzione della faccia considerata.  
![[IMG - Marching cube sadle point.png]]  
una cosa che si tende a fare è quella di applicare uno step di [[Remeshing - Raffinamento|raffinamento]] un volta scelto quale poligono aggiungere, questo funziona molto bene nei casi in cui la funzione scalare segue un [[Interpolazione Trilineare|andamento tri-lineare]] cosa che pero è un assunzione forte e spesso ![[IMG - Marching cube step di raffinamento.png]]


![[IMG - esempio rendenring Marching cube1.png]]