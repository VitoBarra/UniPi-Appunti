---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Sicurezza di una rete
---
la sicurezza di rete si occupa di evitare le interferenze nei raggiungimenti di certi obbiettivi
![[Pasted image 20230113181449.png]]

### Cifratura
1. [[Cifrari a chiave Simmetrica]]
	1. ![[Pasted image 20230113182043.png]]
	-  Cifrari monoalfabetici 
		- Es. [[Cifrario di Cesare|Cifratura di Cesare]] (k-shift) 
	- [[Classificazione di cifrari|Cifrari polialfabetici]] 
		- Es. [[Cifrario di Alberti|Cifrario di Alberti]] 
	- [[Cifrario simmetrico DES|DES]]: Data Encryption Standard 
		- Cifrario a blocchi 
		- Chiave di cifratura 56 bit 
	- [[Cifrario simmetrico AES|AES]]: Advanced Encryption Standard 
		- 2001 standard, sostituisce DES, 
		- Elabora dati in blocchi di 128 bit, chiave di 128, 192, o 2
1. [[Cifrari a chiave Asimmetrica]]
	-  ![[Pasted image 20230113182058.png]]
	- Ognuno possiede
		- una sua chiave pubblica nota a tutti 
		- una sua chiave privata segreta, nota solo a lui

#### Message digest
per i casi in cui l integrità è più importante della riservatezza 
- _[[Funzioni Hash One-Way|Funzione hash]]_: Riceve un messaggio di lunghezza arbitraria e produce un digest di lunghezza fissa 
	- Esempi MD4 MD5 SHA

![[Pasted image 20230113182432.png]]
per essere sicuri che quel messaggio sia stato mandato esattamente ad quel utente
![[Pasted image 20230113182501.png]]
si utilizza una chiave segreta condivisa.

la chiave segreta può essere pero ripudiata si implementa cosi la 
#### Firma digitale
![[Pasted image 20230113182906.png]]
nella [[Protocolli di firma digitale|firma digitale]] si cripta il messaggio con la chiave privata e lo si decripta con la pubblica
- Problema ancora non risolto perché A può cambiare chiave
- ci si affida a terza parti le [[Certification Authority|Certification Authority]]

### IPSec
Insieme di protocolli per fornire sicurezza a livello rete 
- Autenticazione e confidenzialità dei pacchetti IP
	- Modalità trasporto 
	- Modalità tunnel

Modalità trasporto: protegge dati passati da liv. trasporto a liv. rete
![[Pasted image 20230113183151.png]]
Modalità tunnel: protegge l’intero pacchetto IP
![[Pasted image 20230113183159.png]]

![[Pasted image 20230113183221.png]]
Obiettivi: Autenticazione sorgente, Integrità, Riservatezza 
1. Viene aggiunto trailer ESP 
2. Payload e trailer ESP vengono crittografati 
3. Viene aggiunta intestazione ESP 
4. Intestazione ESP, payload e trailer ESP vengono usati per generare dati autenticazione (che vengono aggiunti dopo trailer ESP) 
5. Viene aggiunta intestazione IP (impostando campo protocollo a 50)
![[Pasted image 20230113183329.png]]



IPsec viene utilizzato per vare VPN
![[Pasted image 20230113183457.png]]