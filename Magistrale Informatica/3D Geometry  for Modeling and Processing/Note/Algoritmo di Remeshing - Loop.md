---
Course: "[[3D Geometry for Modeling and Processinga (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Loop
---

Algorito duale e approssimante:
Doo sabin: dopo il primo passo si hanno solo vertici di grado 4





Primale aprossimante
Catmull Clark: dopo il primo paso si hanno vertici con gerardo irregolari, preserva i gradi originali
Proprietà comoda: la mesh diventa solo quad dopo il primo step.

ed esiste una forma chiusa per trovare la superficie. 
Se non ci sono



Loop:
Suddivisione per mesh triangolori primale aprossimante :

PReserva i triangoli in triangolo generando da un triangolo 4 triangolo.


Primale e interpolante
Butterfly suddivisione: si mantiene la posizione originale tra i vertici 
geometricamente fa cagare siccome per lasciare i punti fermi fa ondulare le superfici che dovrebbero essere dritte. Funiziona bene geometria molto curve di base tipo un toro.



Semplificazione:
Utile per semplificare delle parti della mesh che non ha bisogno di tanti triangolo per essere rappresentata.
 Si fa per efficentee per implementare i Level od detail (LOD)


Complessità e accuratezza non hanno una relazione lineare.

va gestito l errore, e questa è definito in due modi
si milita geometrica e similarità di apparenza.

la differenza in apparenza è difficile da misurare perche ci sono molti fattori in gioco. 

quella geometrticaè facile: 

trovare un errore sotto un certo epsilon è Np-Hard ma si usano delle uristiche che funnzionano bene tranne nei casi con occhi poligoni ma va bene perche l interesse e nello spettro dove l errore è molto minore.


si Usano algoritmi gready : 

si scegli l operazione migliore che alza di meno l errore. 

solitamente si usa la versione con gli edge che ha parte combinatoria facile e geometrica leggermente piu difficile, mentre quelli con la faccia meno.

con i vertici la parte combinatoria è difficile, non c è un unico modo per collegare i vertici restanti.


si vuole anche migliorare la mesh durante questo processo.

Puo creare situazione non manifold ma ci sono dei sistemi per controllare quando questo accade. 

Valutazione efficiente del errore:
