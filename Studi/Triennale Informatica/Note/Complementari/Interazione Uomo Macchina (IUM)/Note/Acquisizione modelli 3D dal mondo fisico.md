---
Subject: "[[Interazione Uomo Macchina (IUM)]]"
tags:
  - IUM
Area: 
topic: 
SubTopic:
---
# Acquisizione modelli 3D dal mondo fisico
---
Un sensore d'immagine è un dispositivo che rileva e trasmette informazioni utilizzate per creare un'immagine. Ciò avviene convertendo l'attenuazione variabile delle onde luminose (man mano che passano attraverso o si riflettono sugli oggetti) in segnali, piccole raffiche di corrente che trasmettono le informazioni. Le onde possono essere luce o altre radiazioni elettromagnetiche. I sensori d'immagine sono utilizzati in dispositivi di imaging elettronico di tipo analogico e digitale, che includono fotocamere digitali, moduli fotocamera, telefoni con fotocamera, dispositivi ottici per mouse, apparecchiature di imaging medicale, dispositivi di visione notturna come dispositivi di imaging termico e altri.

i tipi di sensori d'immagine elettronici sono il dispositivo a carica accoppiata (CCD) e il sensore a pixel attivi (sensore CMOS). Sia i sensori CCD che i sensori CMOS si basano sulla tecnologia a metallo-ossido-semiconduttore (MOS), con i CCD basati su condensatori MOS e i sensori CMOS basati su amplificatori MOSFET (transistor a effetto di campo MOS). I sensori analogici per radiazioni invisibili tendono ad utilizzare tubi a vuoto di vario tipo.

#### Scansione 3D
La scansione 3D è il _processo di analisi di un oggetto_ o di un ambiente reale per raccogliere dati sulla sua forma e, eventualmente, sulla sua apparenza (ad esempio, il colore). I dati raccolti possono quindi essere utilizzati per creare modelli digitali 3D. 
I _dati 3D_ sono utili per una vasta gamma di applicazioni. 

Questi dispositivi sono ampiamente utilizzati dall'industria dell'intrattenimento nella produzione di film e videogiochi, inclusa la realtà virtuale. 

Altre applicazioni comuni di questa tecnologia includono la realtà aumentata, la cattura del movimento, il riconoscimento dei gesti, la mappatura robotica, il design industriale, l'ortopedia e la protesi, l'ingegneria inversa e la prototipazione, il controllo qualità/ispezione e la digitalizzazione di manufatti culturali.

  
Uno scanner 3D può essere basato su diverse tecnologie, ognuna con i propri limiti, vantaggi e costi.

Sono ancora presenti molte limitazioni nella tipologia di oggetti che possono essere digitalizzati. Ad esempio, la tecnologia ottica può incontrare molte difficoltà con oggetti lucidi, riflettenti o trasparenti. Le tecnologie di scansione 3D possono essere suddivise in due categorie principali: 
- _passive_: non emettono alcun tipo di radiazione, ma si basano invece sul rilevamento della radiazione ambientale riflessa. 
	- La maggior parte delle soluzioni di questo tipo rileva la luce visibile perché è una radiazione ambientale facilmente disponibile. Altri tipi di radiazione, come l'infrarosso, potrebbero essere utilizzati. 
	- necessitano soli di semplici telecamere digitali e sono quindi metodo economici
- _attive_: emettono qualche forma di radiazione o luce e rilevano il suo riflesso o la radiazione che attraversa l'oggetto al fine di esaminare un oggetto o un ambiente.
	-  I tipi di emissioni utilizzate possono includere luce, ultrasuoni o raggi X. 


##### La scansione passiva
I _sistemi stereoscopici_ sono i sistemi più comuni per lo Scanner 3D passivo e di solito utilizzano due telecamere video, leggermente distanziate, che guardano la stessa scena.
Analizzando le piccole differenze tra le immagini viste da ciascuna telecamera, è possibile determinare la distanza in ogni punto delle immagini. Questo metodo si basa sugli stessi principi alla base della visione _stereoscopica umana_.
![[Pasted image 20230616175340.png]]

I _sistemi fotometrici_ di solito utilizzano una singola telecamera, ma scattano più immagini in _diverse condizioni di illuminazione_. Sfruttando luce e ombre si reisce a recuperare l'orientamento della superficie in ogni pixel.
![[Pasted image 20230616175405.png]]


Le _tecniche di silhouette_ utilizzano contorni creati da una sequenza di fotografie intorno a un oggetto tridimensionale su uno sfondo ad alto contrasto. Queste _silhouette_ vengono estese e intersecate per formare un'approssimazione della forma visiva dell'oggetto. 

Con queste approccio alcune cavità di un oggetto (come l'interno di una ciotola) potrebbero non essere rilevate.
![[Pasted image 20230616175433.png]]

##### Scanner 3D Attivi
Il _time-of-flight 3D laser scanner_ è uno scanner attivo che utilizza la luce laser per esaminare l'oggetto.
questo tipo di scanner utilizza  un _misuratore laser_ di distanza basato sul _Time-of-flight_, ovvero il tempo di andata e ritorno di un impulso luminoso.
Un laser emette un impulso di luce e viene misurato il tempo impiegato prima che la luce riflessa venga rilevata da un sensore. Circa 3,3 picosecondi è il tempo impiegato dalla luce per percorrere 1 millimetro.
Il _misuratore laser_ di distanza rileva solo la distanza di un punto nella sua direzione di vista. Pertanto, lo scanner scandisce l'intero campo visivo un punto alla volta cambiando la direzione del misuratore di distanza.

per farlo funzionare c è bisogno di hardware adatto siccome i tempi di risposta devono essere nel ordine di picosecondi

![[Pasted image 20230616175627.png]]

gli scanner 3D basati sulla _triangolazione_ sono scanner attivi che utilizzano la luce laser per esaminare l'ambiente.
la _triangolazione laser_ proietta un raggio laser sull'oggetto e sfrutta una telecamera per individuare la posizione del punto laser.

A seconda della distanza a cui il raggio laser colpisce una superficie, il punto laser appare in diverse posizioni nel campo visivo della telecamera.
- angolo più grande se l oggetto è più vicino 
- angolo più piccolo se l oggetto è più lontano
- dopo una certa distanza la relazione si inverte

Questa tecnica è chiamata triangolazione perché il punto laser, la telecamera e l'emettitore laser formano un triangolo.
![[Pasted image 20230616175642.png]]

gli _scanner 3D a luce strutturata_ sono una tipologia di scanner attivo, questi proiettano un pattern di luce sull'oggetto e _osservano la deformazione del pattern_ sull'oggetto.
Il _pattern_ viene proiettato con una fonte di luce
Una _telecamera_, leggermente spostata rispetto al proiettore del pattern, osserva la forma del pattern e calcola la distanza di ogni punto nel campo visivo.

questo tipo di scanner 3D è molto vantaggioso siccome puo scannerizzare tutto i punti nel campo visivo della telecamera. 
cosi facendo si elimina anche il problema della deformazione aggiunta dal movimento
![[Pasted image 20230616175728.png]]

I _scanner 3D a luce modulata_ sono un tipo di scanner attivo e proiettano una luce in _continuo cambiamento_ sull'oggetto. Di solito, la sorgente di luce modula semplicemente la sua ampiezza secondo un modello sinusoidale.
Una telecamera rileva la luce riflessa e la quantità di spostamento del pattern determina la distanza percorsa dalla luce. La luce modulata consente anche allo scanner di ignorare la luce proveniente da altre fonti diverse dal laser, eliminando così le interferenze.
![[Pasted image 20230616175757.png]]



il _Kinect_ è una linea di dispositivi di input per il rilevamento del movimento prodotti da Microsoft e lanciati per la prima volta nel 2010.
La tecnologia comprende un insieme di hardware sviluppato originariamente da PrimeSense, che include telecamere RGB, proiettori infrarossi (luci strutturate attive) e sensori che mappano la profondità utilizzando calcoli basati sulla luce strutturata o sul tempo di volo, oltre a un'array di microfoni. Questo insieme di hardware è combinato con il software e l'intelligenza artificiale di Microsoft, che permette al dispositivo di effettuare riconoscimento in tempo reale dei gesti, riconoscimento vocale e rilevamento dello scheletro corporeo per un massimo di quattro persone, tra altre funzionalità. Questo consente a Kinect di essere utilizzato come un dispositivo di interfaccia utente naturale senza contatto
![[Pasted image 20230616175820.png]]