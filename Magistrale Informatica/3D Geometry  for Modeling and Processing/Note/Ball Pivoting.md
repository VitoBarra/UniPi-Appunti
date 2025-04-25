---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Ball Pivoting
---
Il **Ball Pivoting** è un metodo **esplicito** per [[Ricostruzione di superfici del mondo reale con rappresentazioni point base|ricostruzione di superfici]] che approssima la costruzione di uno $\alpha$-[[Alpha Shape]] facendo “rotolare” una palla di raggio $\alpha$ sul campionamento $S$. 

L'idea centrale consiste nell'appoggiare una sferetta di raggio $\alpha$ sul punto di una [[Point Cloud (nuvola di punti)|nuvola di punti]] e farla ruotare lungo gli edge (o i vertici, nel caso 2D) fino a quando non tocca un altro punto del campionamento. A ogni contatto valido viene generata una nuova faccia o un nuovo edge in 2D.
![[IMG - alpha shape ball pivoting.png]]

Dal punto di vista implementativo
il Ball Pivoting è relativamente semplice: si parte da un triangolo iniziale e si mantiene una lista di edge attivi. Per ciascun edge, si cerca un punto che, rispettando i vincoli geometrici (raggio, angolo minimo), consenta di formare un nuovo triangolo. L’algoritmo procede quindi per crescita, espandendo la lista degli edge e chiudendo progressivamente la superficie. Tuttavia, la presenza di rumore nei dati o la variabilità locale della densità possono far sì che il primo vertice utile individuato non corrisponda a quello che sarebbe stato scelto in condizioni ideali, introducendo piccole discrepanze nella ricostruzione.
![[IMG - Ball Pivoting1.png]]
![[IMG - Ball Pivoting2.png]]
![[IMG - Ball Pivoting3.png]]
![[IMG - Ball Pivoting 4.png]]
![[IMG - Ball Pivoting5.png]]
![[IMG - Ball Pivoting6.png]]
![[IMG - Ball Pivoting8.png]]
![[IMG - Ball Pivoting9.png]]
![[IMG - Ball Pivoting10.png]]
![[IMG - Ball Pivoting11.png]]
Uno dei problemi di questo algoritmo è che se il  sampling non è abbastanza uniforme potrebbe perdersi dei triangolari.

In piu la parti planari vengono costruite molte facce non manifold 