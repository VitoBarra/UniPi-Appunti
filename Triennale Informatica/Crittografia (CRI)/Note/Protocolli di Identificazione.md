---
Course: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Protocolli di Identificazione
---
Questo _protocollo_ serve per risolvere il problema del [[Identificazione, autentificazione, Firma digitale|identificanezione]]. 

questi metodi si applicano nei casi in cui c è un _utente_ $U$ che vuole accedere a dei dato i servizi di un sistema $S$ che sono riservati solo a _certi tipi di utenti_, un esempio sono i membri di una data organizzazione.

Per fare cio si utilizza fare il login dove si presenta un _identificativo e una password_ per identificarsi come utente facente parti di quella cerchia.

Assumendo Password abbastanza sicure, vanno distinti due casi 

### Canale sicuro
in un _canale protetto_ in lettura e scrittura le password non possono essere intercetta in chiaro ma esiste ancora un problema. 
Se le informazioni riservate come password fossero conservate in chiaro un _super utente_ o un _hacker_ che è riuscito ad intrufolarsi nel sistema potrebbe leggere le password facilmente dal file dove sono conservate.
Per ovviare a questo problema si usa il seguente metodo

Quando l utente $U$ fornisce la propria _password_ $P_{U}$ invece di essere salvata in chiaro viene salvata come  un [[Generatori di numeri Pseudo Casuali|numero generato casualete]] detto $S$ Seme e ed $Q = h(P_{U}S)$ dove $h$ è una [[Funzioni Hash One-Way|funzione hash one way]] e $P_{U}S$ è la stringa della password concatenata con il seme $S$

abbiamo quindi il file delle associazioni utente password come
![[Pasted image 20230814181120.png]]
al momento del _login_ quando l utente proverà ad accedere verrà recuperato $S$ dal file e ricalcolato $Q =h(P_{U}S)$ se coincide con la _sequenza salvata_ sul file allora l utente è identificato.

_Concatenare la password con un seme_ $S$ evita a chi guarda il file di capire se più utenti hanno usato la stessa password, essendo $S$ generato casualmente anche nel caso in cui due utenti abbiano la _stessa password_ genereranno due sequenza $Q$ diverse.


>[!note]
>questo sistema è ancora oggi usato in [[Sistemi Operativi|UNIX]]


### Canali insicuri
Se siamo in un sistema insicuro l eventuale password mandate dal utente può essere intercettata in chiaro durante la _trasmissione_ quindi è bene che il sistema non operi mai direttamente la password in chiaro, per fare coi si può usare il seguente metodo funzionante con qualsiasi [[Cifrari a chiave Asimmetrica|cifrario a chiave assimetrica]]

il protocollo è spiegando prendendo come cifrario d esempio l [[Cifrario asimmetrico RSA|RSA]]

_siano_ $k[pub]=\langle e,n\rangle$ la chiave pubblica e $k[prv]=\langle d\rangle$ la chiave privata
1. Alla richiesta di un un utente $U$ Il sistema $S$ genera un _numero casuale_ $r<n$ e lo invia in chiaro a $U$ 
2. $U$ decifra il messaggio $r$ calcolando $f=\mathcal{D}(r,k[prv])=r^{d}\mod n$ e spedisce a $S$ il valore $f$.
	1. $f$ è detto _firma_ di $U$ su $r$
3. $S$ verifica il valore ricevuto _cifrando_ $f$, abbiamo quindi $r'=\mathcal{C}(f,k[pub])=f^{e}\mod n$ _se_ $r'=r$ allora l utente è identificato. 

Invertire le operazioni di [[Cifratura e Decifratura|cifratura e decifratura]] da risultati corretti solo perche le due funzioni sono _[[Proprietà del operazioni - Commutatività|commutative]]_

#### Attacchi a questo sistema
nel sistema sopra descritto si assume che $r$ sia _generato casualmente_, ma si potrebbe struttura un attacco dove si sceglie $r$ a doc per estrarre informazioni dalla _trasformazione_ di $r$ in $f$, questo diventa ancora piu pericoloso se si può scegliere una sequenza mirata di $r$ con identificazioni multiple.

questo tipo di problema è risolto con le tecniche [[Protocolli Zero Knowledge|Zero Knowledge]]
 