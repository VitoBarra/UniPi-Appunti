---
Course: "[[Reti]]"
topic: nota
tags:
  - RETI_LAB_III
---
# Livello di rete
---
il livello di rete è un livello del modello [[Modello TCP-IP]] ed è responsabile della consegna dei datagrammi tra gli host

- offre servizi allo [[Livello di trasporto]]
- utilizzza i servizi dell [[Livello di collegamento]]


### Funzionamento generale
![[Pasted image 20230106192904.png]]
1. L’entità a livello di rete riceve i segmenti dal [[Livello di trasporto]] nell’host _mittente_, e incapsula i segmenti in datagrammi 
2. I datagrammi sono inoltrati al prossimo nodo _host o router_ 
	1. Il _router_ esamina i campi intestazione in tutti i datagrammi IP che lo attraversano e li _inoltra_ da un collegamento in ingresso ad un collegamento in uscita 
3. Sul lato destinatario, consegna i segmenti al [[Livello di trasporto]] demux [[Livello trasporto - TCP|TCP]] o [[Livello trasporto - UDP||UDP]]


### Motif dello Strato di rete
lo scopo del livello di rete e mettere in interconnessione logica reti fisiche
lo fa fornendo un astrazione sulla fisicita e permettendo cosi a [[WWW - Word Wide Web|internet]] di funzionare come se fosse un unica rete logica

Con il modello si vede come lo strato di rete e in mezzo fa da interfaccia per sopra e sotto cosi facendo ci può essere innovazione nei livelli superiori e inferiori
![[Pasted image 20230106193945.png]]


### Servizi offerti
- Suddivisione in pacchetti
- Instradamento o _routing_
- Inoltro o _forwarding_