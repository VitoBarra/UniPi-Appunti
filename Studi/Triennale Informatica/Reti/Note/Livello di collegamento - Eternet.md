---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Livello di collegamento - Eternet
---
Eternet è una tecnologia di connessione [[Livello di collegamento]]
### Topologia
![[Pasted image 20230113151810.png]]
topologia a stella ovvero tutti collegati ad un nodo centrale che fa storage and forwarding dividendo cosi il dominio di collegamento.

il livello Collegamento Ethernet utilizza questo frame
![[Pasted image 20230113152001.png]]
- _Preambolo_:
	- I pacchetti Ethernet iniziano con un campo di otto byte: sette hanno i bit 10101010 e l’ultimo è 10101011. 
	- Servono per “attivare” gli adattatori dei riceventi e sincronizzare i loro orologi con quello del trasmittente. 
- _Dati_: 
	- ’unità massima di trasferimento MTU varia da 46 byte ad un max di 1500 byte. Se il datagramma è più grande allora deve essere frammentato. Se il campo dati è più piccolo il campo dati deve essere riempito (stuffed)
- _Indirizzo di destinazione_: 6 byte 
	- Quando un adattatore riceve un pacchetto con indirizzo di destinazione corrispondente al proprio indirizzo MAC o l’indirizzo broadcast (es.: un pacchetto ARP), trasferisce il contenuto del campo dati del pacchetto al livello di rete. 
	- I pacchetti con altri indirizzi MAC vengono ignorati. 
- _Indirizzo sorgente_: 6 byte. Indirizzo dell’adattatore (scheda di rete) che trasmette il frame 
- _Campo tipo_ (2 byte): consente a Ethernet di supportare vari protocolli di rete (i.e., IP, ARP) (in gergo questa è la funzione di “multiplexare” i protocolli). 
- _Controllo CRC_: consente all’adattatore ricevente di rilevare la presenza di un errore nei bit del pacchetto.



### Diversi standard Ethernet 
![[Pasted image 20230113152410.png]]

### Evoluzione Ethernet 
![[Pasted image 20230113152506.png]]


### Repeater e Hub
- _Repeater_ 
	- operano solo a livello fisico 
	- Rigenerano il segnale che ricevono 
	- in passato usati per collegare segmenti di Ethernet con topologia a bus 
- _Hub_ 
	- repeater multi-porta 
- Repeater e hub non hanno capacità di filtraggio

![[Pasted image 20230113152553.png]]
### Switch
_Operano_
- _livello fisico_: rigenerando segnale 
- _livello link_: verificando indirizzi MAC contenuti in frame 
- Hanno una tabella che usano per filtraggio 
- ![[Pasted image 20230113152713.png]]
- Non modificano indirizzi MAC in intestazione frame
- Trasparente agli host
![[Pasted image 20230113152656.png]]
se lo switch non al inoltro del messaggio invia i messaggi sulla porta giusta leggendo dal frame il MAC destinazione e confrontandolo con la _tabella di inoltro_. se l associazione non é presente fa _Floating_ ovvero invia il messaggi su tutte le porte.
per costruire la tabella di inoltro utilizza i frame di arrivo, siccome le porte sono associate 1:1 con un dispositivo e quindi con un solo indirizzo MAC lo switch riesce a imparare su quali porte ci sono i vari indirizzi MAC dal indirizzo MAC mittente dei frame che processa 
![[Pasted image 20230113153341.png]]
when frame received at switch: 
1. record incoming link, MAC address of sending host 
2. index switch table using MAC destination address 
3. _if_ entry found for destination then 
	1.  _if_ destination on segment from which frame arrived then drop frame 
	2. _else_ forward frame on interface indicated by entry  
4. _else_ flood, forward on all interfaces except arriving interface 

##### Switch gerarchico
anche in questo caso funziona l auto apprendimento siccome lo swtich è trasparente 
![[Pasted image 20230113153854.png]]

### Vantaggi dello switch
- Gli switch bufferizzano i pacchetti 
- _no collisions_; _full duplex_ 
	- Ogni link ha il suo proprio dominio di collisione 
- _switching_: A-to-A’ and B-to-B’ possono trasmettere simultaneamente senza collisioni

![[Pasted image 20230113153436.png]]