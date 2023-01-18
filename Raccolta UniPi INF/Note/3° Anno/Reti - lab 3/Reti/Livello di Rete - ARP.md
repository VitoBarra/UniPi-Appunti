 ---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3]]

# Livello di Rete - ARP
---
_Adress Resoluziont Protocol_  è un [[Protocollo]] utile al livello collegamento ma viene tipicamente considerato un protocollo di [[Livello di rete]] . serve per convertire gli indirizzi in di una LAN in  [[Livello di collegamento - indirizzi MAC|indirizzi MAC]].

![[Pasted image 20230113021725.png]]

### funzionamento

![[Pasted image 20230113021917.png]]
- Ogni nodo IP (host, router) nella LAN ha una tabella _ARP_. 
- _Tabella ARP_: contiene la corrispondenza tra indirizzi IP e MAC.
	- entry della tabella fatta come: _<Indirizzo IP; Indirizzo MAC; TTL>_ 
	- _TTL (tempo di vita)_: valore che indica quando bisognerà eliminare una data voce nella tabella (il tempo di vita tipico è di 20 min
	- ![[Pasted image 20230113022150.png]]
ogni tabella si riferisce ad una sola sottorete LAN se ci sono più sottoreti ci saranno più tabelle.

#### Richiesta
![[Pasted image 20230113022512.png]]
il _payload_ ARP ha molti campi siccome c è bisogno di una buona generalità per poter far funzionare tutte le tecnologie disponibili a livello collegamento
- _Hardware Type_: protocollo a livello di collegamento (es. Ethernet 1) 
- _Protocol Type_: protocollo di livello superiore (es. IP) 
- _Source hardware address e source protocol address_: indirizzi del nodo mittente a livello link e superiore. Lunghezza variabile. Campi Hard. Length e prot. Length 
- Destination hard. Address (vuoto nelle richieste) e destination protocol address.

1. ![[Pasted image 20230113023028.png]]
2. ![[Pasted image 20230113023039.png]]
1. Il protocollo _ARP_ interagisce direttamente con il livello collegamento 
2. Il pacchetto _ARP_ viene incapsulato in un frame e spedito in broadcast sulla rete 
3. L’header del frame di livello 2 specifica che il frame contiene un pacchetto _ARP_ 
4. Ogni nodo nella rete locale riceve ed elabora il pacchetto di richiesta _ARP_. 
5. Il nodo che riconosce il proprio indirizzo IP restituisce un pacchetto di risposta ARP che contiene il proprio indirizzo IP e indirizzo MAC. Il pacchetto di risposta viene inviato in modalità _unicast_ al nodo originario

## Suscettibilità agli attacchi
- ARP è stato progettato in modo tale da essere il più possibile efficiente. 
	- Vulnerabilità che possono essere sfruttate (e vengono di fatto utilizzate) per sferrare attacchi. 
	- Risposte MAC con dati alterati 
	- Scopo: 
		- _man in the middle attack_: i pacchetti che hanno un certo host destinatario vengono ridirezionati verso un host malevolo e da lì verso il destinatario;
		- _Denial of service_: i pacchetti non arrivano al destinatario 
	- Alterando l'indirizzo MAC associato ad un determinato IP di un dispositivo connesso alla rete, tutti i pacchetti dati vengono automaticamente inviati al sistema che ha lanciato l'attacco ARP poisoning. I dati possono essere a questo punto analizzati, eventualmente modificati e quindi inviati al reale destinatario.