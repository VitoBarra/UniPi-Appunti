---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Mesh zippering
---
il **Mesh zippering** è un algoritmo di [[Ricostruzione di superfici del mondo reale con rappresentazioni point base|ricostruzione di superfice]]  che utilizza usa le [[Range map|Range map]].

questo algoritmo risolvere il problema delle [[Range map|Range map]] dove le [[Acquisizione modelli 3D dal mondo fisico|acquisizioni]] non sono alleate correttamente.
![[IMG - mesh zippering-1.png]]
L idea generale del algoritmo è il seguente:
- **Rimozione delle porzioni sovrapposte**: quando due superfici triangolate si intersecano, si procede a eliminare le aree duplicate per mantenere una sola rappresentazione per ciascuna porzione della superficie.
- **Clipping reciproco**: ciascuna range map viene ritagliata rispetto ai bordi dell’altra, mediante un’operazione di taglio dei triangoli. Formalmente, dato un triangolo $T_1$ appartenente alla mesh $M_1$, si identifica l’intersezione con i bordi dei triangoli $T_2$ di $M_2$, producendo sottotriangoli che rispettano il confine condiviso.
![[IMG - mesh zipering punti di giuntura.png]]
- **Rimozione dei triangoli piccoli**: al termine del processo, i frammenti di triangoli generati nelle zone di clipping vengono filtrati in base alla loro area. Siano $A_i$ le aree dei triangoli risultanti; si impone una soglia $\epsilon$ tale che ogni $A_i < \epsilon$ venga rimosso.
![[IMG - mesh zippering pulizia finale.png]]
Questo approccio, sebbene concettualmente semplice, presenta una notevole complessità nella sua implementazione robusta. Il motivo risiede nella gestione dei numerosi casi limite che si presentano durante il clipping, nella corretta riconnessione delle mesh, e nella necessità di "tappare" i buchi residui che si formano nelle zone di sovrapposizione mal definite.
![[IMG - mesh zippering overlapping surface.png]]

