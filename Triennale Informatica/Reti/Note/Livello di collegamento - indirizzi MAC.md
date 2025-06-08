---
Course: "[[Reti]]"
topic: nota
tags:
  - RETI_LAB_III
---

# Livello di collegamento - indirizzi MAC
---
### Indirizzo MAC (Media access control)
- Un indirizzo del [[Livello di collegamento]] 
- è associato alla _scheda di rete_, non al nodo, ed è tipicamente permanente (anche se è possibile modificarlo); 
- è detto indirizzo fisico o indirizzo LAN o indirizzo _MAC_(Media Access Control); 
- per le LAN Ethernet e IEEE 802.11 è lungo 6 byte ($2^{48}$ possibili indirizzi) ed è espresso in notazione esadecimale (12 cifre esadecimali). 
	- Esempio: 1A-63-F9-BD-06-9B 
- Come viene garantita l’univocità? 
	- IEEE definisce ed assegna i primi 24 bit (_OUI_ Organization Unique Identifier), mentre i rimanenti 24 bit vengono gestiti dalle aziende ed assegnati a livello locale. 
	- Quando una società vuole costruire adattatori, compra un blocco di spazio di indirizzi (univocità degli indirizzi).


### Comunicazione con MAC

### Forwarding diretto
tutti gli Host sono nella stessa LAN
![[Pasted image 20230113024526.png]]
1. Se non si conosce già l indirizzo MAC del destinatario lo si attiene con [[Livello di Rete - ARP|ARP]]
2. si spedisce il frame con indirizzo di mittente MAC l indirizzo del mittente e come indirizzo del destinatari MAC l indirizzo preso con della tabella _ARP_ 
3. a seconda della tipologia di rete i vari host leggono il frame e se l indirizzo MAC destinatario corrisponde al proprio inviano il fare al [[Livello di rete]] 


### Forwarding Indiritto
gli host sono su due LAN separate
![[Pasted image 20230113025749.png]]
1.  il promo host crea un frame con indirizzo mittente il proprio MAC e come  destinazione l indirizzo del [[Livello di rete - Router|Router]] 
2. il frame arrivato al router lo inoltrerà al prossimo salto mettendo come indirizzo MAC mittente il MAC della la sua l interfaccia di uscita e destinatario il prossimo  il MAC del prossimo nodo (host o router)

