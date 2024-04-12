---
Subject: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Identificazione, autentificazione, Firma digitale
---
L _[[Protocolli di Identificazione|Identificazione]], [[Protocolli di Autenticazione|autentificazione]], [[Protocolli di firma digitale|Firma digitale]]_ sono tre nuove necessita che si sono venute a creare con l espandersi del bacino di untenza di [[Struttura di Internet|internet]] e sono definite come 

_Identificazione_: 
	Un sistema di elaborazione isolato o inserto in una rete deve essere in grado di _accertare l identità_ di un utente che richiede di accedere ai suoi servizi

_autentificazione_: 
	Il destinatario di un messaggio deve essere in grado di accertare l _identita del mittente_ e l _interita del crittoramma_ ricevuto ovvero che questo non sia stato modificato o sostituito nella trasmissione. Deve quindi essere difficile ad un intruso spacciarsi per un altro utente o modificare i messaggi da questo inviati

_Firma digitale_: la Firma digitale deve avere 3 requisiti
- il mittente non deve poter negare di aver inviato il messaggio $m$
- il destinatario deve poter accertare l identità del mittente e l integrità del crittogramma ricevuto (deve _autenticare_ il messaggio)
- il destinatario non deve poter sostenere che un messaggio $m' \not = m$ è quello inviatogli dal mittente.
questi requisiti devono essere verificati da una terza parte
