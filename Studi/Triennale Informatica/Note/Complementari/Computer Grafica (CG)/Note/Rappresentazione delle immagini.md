---
Course: "[[Computer Grafica (CG)]]"
Subject: Computer Grafica
Area: 
Topic: 
SubTopic: 
tags:
  - CG
---


# Rappresentazione delle immagini
---
nella computer grafica è importante capire come sono _rappresentate le immagini_ sia dal punto di vista del hardware che software.

Ci sono due famiglie di grafiche

##### Vector Graphic
Sono formati di _immagini rappresentate_ forme semplice come punti, linee, cerchi e altre forme basilari. 
in questo modo _le immagini_ possono essere descritte da una lista di proprietà, compreso il colore, degli oggetti basilari.
Un esempio è il sottostante.
![[IMG_0718.jpeg]]
il formato piu diffuso è _SVL_ (_Scalable Vector graphic_). e il _PC_ (PostScript).
dove l _SVG_ viene solitamente usato per rappresentare solo immagini e il _PC_ è un _Linguaggio di programmazione_ usato per descrivere _immagini vettoriali_ e per dare comandi a dispositivi di stampa, infatti questo formato supporta operazioni per la stampante come il controllo della quantità di _inchiostro_.



#### Raster Images
è un Modo per rappresentare le immagini è tramite l utilizzo di _Pixel_ (__*Pic*ture *El*ement__), ovvero delle piccole celle che rappresentano una piccola parte del immagine.
![[IMG_0719.jpeg]]
I _pixel_ posso essere rapresentati in modo diverso a seconda del tipo di immagine che si vuole rappresentare.
Ad esempio possono essere un solo _scalare_ che indica la _lucentezza_ di un dato pixel, risultando cosi in una scala di grigio, oppure puo avere un _vettore_ di scalari per rappresentare i casi in cui ci sono piu colori. il numero di valori nel vettore è chiamato il _numero di canali_, solitamente si usano 3 Channel, _Red, Green, Blue_, una combinazione di questi esprime il colore finale in accordo al [[Funzionamento della vista umana (HVS)|sistema visivo umano]]. I canali possono essere eventualmente isolati e visti singolarmente.
![[IMG_0720.jpeg]]
in aggiunta a questi solitamente i aggiunge un quarto _canale_ chiamato _alpha channel_ che rappresenta la _trasparenza_
![[IMG_0724.jpeg]]


le  immagini resterizate dipendono fortemente sulla risoluzione del immagine. 
la _risoluzione_ del immagine è definita come $\cfrac{px}{inch}$ ovvero il numero di pixel che sono in un _pollice_, questa la possiamo vedere una misura di quanto possiamo mettere vicine due linee sullo stesso schermo senza che appaiano una singola linea

Più _comunemente_ pero si usa direttamente il numero di pixel presenti in un immagine contati come $Width \times Hight$, questo siccome ogni dispositivo è pensato per essere visto ad una certa _distanza_ il che fa variare la porzione di _campo visivo_ occupata dal dispositivo.


#### Confronto rasterizate vs Vettoriali
Se l immagine che si vuole rappresentare ha _meno pixel_ rispetto allo scherno si cui si sta proiettando l immagine si vedranno i pixel creando un effetto _pixelato_.

questo succede solo con le immagini _rasterizate_ mentre le immagini vettoriali hanno risoluzione _infinita_ siccome basta scalare le primitive che rappresentano l immagine per uno scalare e non si perde di qualita. Questo non è possibile con un immagine rasterizata.
![[IMG_0721.jpeg]]
 Le _immagini vettoriali_ pero non sono adatte a rappresentare scenari molto complessi siccome ci vorrebbero troppe primitive per riuscire a ricreare ad esempio un paesaggio. Infatti queste sono solitamente impiegate in _loghi_ o _trade marks_.
 le _immagini rasterizate_ invece riescono a cogliere la complessità e sono piu adatte a le comuni foto.