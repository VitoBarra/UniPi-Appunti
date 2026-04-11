---
Course: Ingegneria del software
topic: nota
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
	- ![[IMG - Design pattern - Proxy 1.jpeg]]
	- ![[IMG - Design pattern - Proxy 2.jpeg]]
2.  _ProtectionProxy ( aka firewall proxy)_ 
	- Il Proxy implementa un controllo sugli accessi 
3. _Cache Proxy_ 
	- Il Proxy mantiene coppie richiesta-risposta sgravando il server
4. _Synchronization Proxy_
	- Gestisce gli accessi concorrenti a un servizio
5. _Virtual Proxy_
	-  un segnaposto per oggetti "costosi da creare".
	- ![[IMG - Design pattern - Proxy 3.jpeg]]

### Quando Usarlo 
 a seconda di se sono utili uno dei tipi di proxy scelti 

#### Come Applicarlo 
Implementando una classe che richiama tutte le funzioni di un altra classe con la stessa interfaccia 

### Vantaggi
- differenti a seconda del tipo di proxy
- permette pre o post processing
#### Struttura 
![[IMG - Design pattern - Proxy 4.jpeg]]

##### Componenti 
- _client_: utilizzatore del oggetto sui cui si applica un proxy
- _SeriveceInterface_: l interfaccia comune tra _Proxy_ e oggetto _OriginalService_ su cui si applica 
- _Proxy_: la classe che mantiene un riferimento entro al servizio originale e implementa dei comportamenti prima di chiamare quei servizi.
- _OriginaService_: Il servizio originale