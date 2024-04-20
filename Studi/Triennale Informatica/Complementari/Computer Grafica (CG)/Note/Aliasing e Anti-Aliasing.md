---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Pipeline di Rasterizazione]]"
SubTopic: "[[Trasformazione Frammenti in Pixel]]"
---

# Aliasing e Anti-Aliasing
---
l' __Aliasing__ è una problematica della  [[Trasformazione Frammenti in Pixel|trasformazione da frammenti in pixel]] e ci si riferisce al fatto che siccome stiamo approssimando una rappresentazione in coordinate reali con delle coordinate discrete può succedere che [[Computer grafica - Primitive Geometriche|segmenti]] diversi possono essere mappati negli stessi pixel, infatti una data lineea può essere mappata dai infiniti segmenti, e senza una conoscenza a priori non possiamo sapere a quale segmenti la linea si riferisce.
![[Pasted image 20240216143210.png]]
L effetto visivo di cio e' l avere delle linee dentellate chhe non danno l effetto di essere un effettiva linea ma ci sono delle tecniche dette di __anti-aliasing__ che mitigano questo effetto. 
![[Pasted image 20240216143230.png]]


##### Area averaging thecnique
si interseca una retta di spessore $1$ con i pixel e poi si utilizza l area di intersezione per decidere quanto l intensita del [[Color Space|colore]] deve essere altra, se solo meta del pixel e coperto dal poligono allora l intensita sara ridotta della meta, e cosi via.
calcolare l intersezione pero richiede molte  operazioni floating point e  questo bisognerebbe evitarlo.

##### Super sampling anti aliasing (SSAA)
la tecnica di Anti-Aliasing di super Sampling consiste nel renderizare la scena in un framebuffer piu grande e poi fare l average per calcolare il valore vero da mettere nel framebuffer della dimensione giusta.
![[Pasted image 20240216143243.png]]
Questo funziona ma costa molto in memoria infatti, se si usa un sample $n \times n$ costerà $n^2$ volte la memoria che sarebbe servita normalmente

##### Multi sampling anti-Aliasing (MSAA)
per ogni pixel si utilizzano piu "sample" ovvero piu punti dello stesso pixel oltre al centro, se almeno un punto e' coperto dalla primitiva allora il frammento si attiva con un intensità del colore proporzionale al numero di sample coperti
![[Pasted image 20240216143254.png]]
questo richiede solo piu memoria per il depth buffer e lo stencill buffer.