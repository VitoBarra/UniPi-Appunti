---
type: nota
course: Ingegneria del software
topic: 
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Design pattern - Proxy
---

tipo di [[GoF Design Patterns]]  Strutturale


Un proxy fornisce un surrogato o segnapost per un altro oggetto, per controllarne l accesso
- è simile ad [[Design pattern - Adapter|Adapter]] perché introduce un intermediario
- sono diversi in quanto il proxy ha stessa interfaccia  del oggetto originale nel adapter questa cosa nel adapter non è vera
- il proxy può eseguirei pre e post elaborazioni

## Tipi di proxy
1. _Remote Proxy_ 
	- Il Proxy permette l’accesso a un oggetto remoto
	- Usato in Protection RMI e in Corba 
	- ![[1712BDD0-6ACF-4D6E-967A-F4BD3BFD2072.jpeg]]
	- ![[1C52B6ED-9A71-4398-B524-DA4A9A7D9293.jpeg]]
2.  _ProtectionProxy ( aka firewall proxy)_ 
	- Il Proxy implementa un controllo sugli accessi 
3. _Cache Proxy_ 
	- Il Proxy mantiene coppie richiesta-risposta sgravando il server
4. _Synchronization Proxy_
	- Gestisce gli accessi concorrenti a un servizio
5. _Virtual Proxy_
	-  un segnaposto per oggetti "costosi da creare".
	- ![[D15D71A6-096D-4A4A-8B02-0CE2584C3C78.jpeg]]

### Quando Usarlo 
 a seconda di se sono utili uno dei tipi di proxy scelti 

#### Come Applicarlo 
Implementando una classe che richiama tutte le funzioni di un altra classe con la stessa interfaccia 

### Vantaggi
- differenti a seconda del tipo di proxy
- permette pre o post processing
#### Struttura 
![[74B52F9A-EB5C-41BF-BC8B-C93FA5AB4830.jpeg]]

##### Componenti 
- _client_: utilizzatore del oggetto sui cui si applica un proxy
- _SeriveceInterface_: l interfaccia comune tra _Proxy_ e oggetto _OriginalService_ su cui si applica 
- _Proxy_: la classe che mantiene un riferimento entro al servizio originale e implementa dei comportamenti prima di chiamare quei servizi.
- _OriginaService_: Il servizio originale