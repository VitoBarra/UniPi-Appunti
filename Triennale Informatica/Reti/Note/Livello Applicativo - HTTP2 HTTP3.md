---
Course: "[[Reti]]"
topic: nota
tags:
  - RETI_LAB_III
---


# Livello Applicativo - HTTP2 HTTP3
---
### HTTP 2
- si può definire priorità degli oggetti
- il server può inviare in modo push degli oggetti non ancora richiesti dal client
- si mandano dei frame, non oggetti, l invio del ordine di questi frame può essere negoziato
- ![[Pasted image 20230114194739.png]]
- gestione a stream per richiesta, gestiti con priorità e pesi
	- ![[Pasted image 20230114194833.png]]
- si mitiga il problema del _Head of Line blocking_
- ![[Pasted image 20230114195010.png]]
- ma se c è perdita bisogna aspettare il reinvito del frame perso prima di poter inviare gli altri

### HTTP3
risolve il problema della HOLB utilizzando [[Livello trasporto - UDP]] cosi e mettendo un nuovo protocollo che implementa l sicurezza di trasmissione ma pensato per gestire l HOLB. 
![[Pasted image 20230114195353.png]]
in particolare QUIC ha una connessione UDP e creare più Stream di invii uno per richiesta
- questi sono indipendenti
- la sicurezza è garantita su i singolo stream
![[Pasted image 20230114195158.png]]
- se si perde un pacchetto rallenta solo quello stream gli altri possono andare avanti senza dover aspettare la ritrasmissione del pacchetto sullo stream dove si è perso un pacchetto


![[Pasted image 20230114195328.png]]