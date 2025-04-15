---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Indici spaziali
---
Gli **indici spaziali** sono delle [[strutture dati|strutture dati]] utilizzate nel contesto della [[Computer Grafica (CG)|computer grafica]] e nel [[3D Geometry for Modeling and Processing (3GMP)|mesh processing]] quando si vogliono risolvere **query geometriche**, ovvero quando si vuole rispondere a domande del tipo 
- quale è la [[Computer grafica - Primitive Geometriche|primitiva geometrica]] piu vicina rispetto ad un punto
- l' intersezione tra due primitive
Sono necessarie in casi in cui si affrontano problemi che coinvolgono un gran numero di [[Computer grafica - Primitive Geometriche|primitive geometriche]], Infatti l'approccio senza strutture dati spaziali risulta inefficiente, con [[Complessita|complessità temporali]] lineari $O(n)$ nel numero di primitive o addirittura quadratiche $O(n^2)$ nel caso della rilevamento delle collisioni, usando **indici spaziali** invece si puo
ottenere una [[Complessita|complessità]] quasi costante o almeno logaritmico al medio. 
Sebbene esistano limiti teorici inferiori che garantiscono anche il caso peggiore logaritmico ma questi spesso si applicano a contesti inrealistici.


Gli **indici spaziali** si dividono in due categorie principali:
- Le **strutture non gerarchiche**, basate su una suddivisione piatta dello spazio, sono semplici ed efficienti in contesti con distribuzioni uniformi o quando si vuole evitare l’overhead delle strutture gerarchiche.
- Le **strutture gerarchiche**, invece, adottano un approccio **divide et impera**, suddividendo ricorsivamente lo spazio per gestire meglio distribuzioni non uniformi delle primitive. Si basano solitamente su [[Struttura dati - Alberi|alberi]] e quindi le querry corrispondono a visite dell’albero. Ad ogni nodo corrisponde una regione dello spazio![[IMG - Indici gerarcici.png]]










### Quad Tree




