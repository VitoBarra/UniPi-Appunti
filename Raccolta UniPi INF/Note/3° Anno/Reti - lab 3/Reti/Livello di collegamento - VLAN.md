---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3]]

# Livello di collegamento - VLAN
---
una _virtual local area Network_ VLAN è un operazione software che opera a [[Livello di rete]] e serve per partizionare una LAN in più LAN virtuali cosi da cambiare il dominio del broadcast riducendo cosi il traffico e rendendo più facile implementare la sicurezza    
- _dominio del broadcast_: i dispositivi che ricevono i frame in broadcast 
![[Pasted image 20230113155334.png]]
le VLAN lavorano a livello rete e creano due reti logicamente separate il che significa che c è bisogno di un [[Livello di rete - Router|Router]] per poter far comunicare tue reti
![[Pasted image 20230113160345.png]]
- _dynamic membership_: le porte possono essere assegnate dinamicamente alle VLANs

### Spaning multiple Switches
![[Pasted image 20230113162950.png]]
- _trunk port_: per trasportare frame tra VLAN tra più switch
	- i frame per supportare questo trasferimento devono essere estesi con un VLAN id in modo da poterle distinguere
	- _802.1q_ protocollo che aggiunge gli header per la gestione delle VLAN
	- ![[Pasted image 20230113163136.png]]
	- altri standard hanno più bit di tag per supportare un numero più alto di VLAN


### VLAN con subnet
di solito ad ogni VLAN viene associata una sottorete diversa cosi da poter usare il router per mettere in comunicazione diverse VLAN. non è obbligatorio che sia questo il caso ma è una best practis
