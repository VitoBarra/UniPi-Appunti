---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3]]

# Livello di collegamento - MAC
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
