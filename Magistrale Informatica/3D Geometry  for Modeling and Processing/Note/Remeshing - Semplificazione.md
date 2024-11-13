---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Remeshing - Semplificazione
---
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
