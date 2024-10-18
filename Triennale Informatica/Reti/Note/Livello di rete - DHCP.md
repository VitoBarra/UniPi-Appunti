---
Course: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti]]

# Livello di rete - DHCP
---
il DHCP è protocollo client server di supporto usato nel assegnazione dinamica degli [[Livello di rete - IP|inidirzzi IP]]


-  Un indirizzo IP può essere attribuito all'interfaccia di un host secondo due distinte modalità: 
- Configurazione manuale: l'amministratore configura direttamente nell'host l'indirizzo IP ed inserisce ulteriori informazioni di servizio (indirizzo gateway/router, netmask e indirizzo IP di almeno un server DNS) 
- DHCP (RFC 2131): l'host ottiene il proprio indirizzo e le altre informazioni in modo automatico

Il protocollo _DHCP_ ha l obbiettivo di assegnare dinamicamente un Ip ad un host che si aggiunge alla rete cosi facendo può
- Cambiare indirizzo ad un host
- Permettere il riuso di un indirizzo precedentemente assegnato
- Supporto per utenti in mobilita che si uniscono/lasciano la rete

#### fasi del protocollo DHCP 
![[Pasted image 20230106231027.png]]
-  L’host invia in broadcast un messaggio _DHCP discover_ [opzionale] 
- Il server _DHCP_ risponde con un messaggio _DHCP offer_ [opzionale] 
- L’host richiede un indirizzo IP: messaggio _DHCP request_ 
- Il server _DHCP_ invia un messaggio _DHCP ack_ (se la richiesta va a buon fine)
![[Pasted image 20230114175519.png]]

il Server DHCP oltre al IP può invaiare anche:
- indirizzo del gateway/router 
- Netmask 
- Nome e indirizzo IP di almeno un server DNS

>[!note]
>il Server DHCP puo essere anche istallano direttamente sul router
>
>DHCP Utilizza [[Livello trasporto - UDP|UDP]]

