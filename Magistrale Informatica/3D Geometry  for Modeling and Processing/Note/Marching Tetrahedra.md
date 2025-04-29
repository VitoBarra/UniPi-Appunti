---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Marching Tetrahedra
---
il __Marching Tetrahedra__ è un **[[Algoritmi|algoritmo]]** per trasformare un [[Superfici implicite|rappresentazione implicita]] (campo salare) 3D in una [[Mesh Poligonali|mesh poligonale]].


Il metodo del ***Marching Tetrahedra*** è una variante del [[Marching cube|Marching cube]] dove le celle sono  tetraedriche. Questa scelta abbassa notevolmente la complessità del problema, dato che una cella tetraedrica possiede solo quattro vertici, riducendo il numero delle possibili configurazioni a $2^4 = 16$. Tenendo conto di simmetrie e complementarità, il numero effettivo di configurazioni si riduce ulteriormente a tre: 
- tutti i vertici sopra o sotto la soglia
- un solo vertice sopra o sotto la soglia (generando un triangolo), 
- due vertici sopra e due sotto la soglia (generando un quadrilatero).
![[IMG - Marching Tetrahedra.png]]
Un aspetto cruciale di questo approccio è che si assume che il campo scalare all'interno della cella sia interpolato linearmente tra i vertici. 
L'[[interpolazione lineare|interpolazione lineare]] in un tetraedro implica che la funzione descritta sia lineare su tutto il volume della cella. Pertanto, l'isosuperficie risultante coincide esattamente con il pezzo di piano corrispondente al valore isosuperficiale. in piu ogni quadrilatero generato da questo metodo è sempre planare.

La tecnica del **Marching Tetrahedra** è stata anche proposta su rappresentazioni volumetriche regolari. In particolare, partendo da una griglia cubica, ogni cubetto può essere decomposto in tetraedri per applicare la tecnica. Esistono diversi modi per effettuare tale decomposizione:
- Una prima decomposizione prevede di suddividere ogni cubo in cinque tetraedri. Si sfrutta la presenza di un tetraedro regolare nascosto all'interno del cubo: prendendo i due vertici superiori e inferiori collegati dalla diagonale principale, si ottiene un tetraedro regolare. Il volume restante viene completato con quattro piccole piramidi che si appoggiano sulle facce del tetraedro. Tuttavia, questa decomposizione è orientata, e quindi presenta disallineamenti nelle diagonali quando si accostano due cubi adiacenti. Questo comporta la necessità di attenzioni particolari nella costruzione della mesh.
- Una seconda decomposizione divide il cubo in sei tetraedri. Si prende la diagonale principale del cubo e si utilizzano triangoli isosceli piegati a $90^\circ$ rispetto ad essa. In questo modo si ottengono sei tetraedri allungati ma identici. Questo approccio presenta il vantaggio che le diagonali delle facce adiacenti risultano corrispondenti, garantendo il corretto matching tra cubi.
- Una terza decomposizione, più complessa, prevede l'aggiunta di un ulteriore vertice al centro di ogni cubo. Collegando questo vertice ai vertici originali si ottiene una divisione in ottaedri. Successivamente ogni ottaedro può essere suddiviso in quattro tetraedri. Questo metodo rappresenta una via di mezzo: la qualità dei tetraedri risultanti è migliore rispetto agli altri due metodi, soprattutto grazie alla presenza di un tetraedro centrale molto ben proporzionato, mentre gli altri risultano solo leggermente deformati.
![[IMG - marching thedaedral.png]]
La scelta del tipo di decomposizione dipende dal compromesso tra semplicità di implementazione, qualità della mesh risultante e fedeltà nella rappresentazione dell'isosuperficie.
