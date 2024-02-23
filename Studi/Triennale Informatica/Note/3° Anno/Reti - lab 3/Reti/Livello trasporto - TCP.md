---
Subject: Reti e Laboratorio di reti
topic: nota
tags: RETI_LAB_III
---

Prev: [[Reti - lab 3]]

# Livello trasporto - TCP
---
il [[Protocollo]] TCP è un protocollo di [[Livello di trasporto]] 

questo protocollo è _orientato_ alla connessione nonostante si basi sul utilizzo di [[Livello di rete - IP|IP]] che è connection-less
- _orientato_: perché lo stato della connessione risiede sui punti terminali non sugli elementi intermedi della rete

_Funzioni base per il trasferimento di dati_: 
- capacità di trasferire un flusso continuo di byte 
- trasferimento bidirezionale (full duplex) 
_Multiplexing/demultiplexing_ 
- consente di assegnare una data connessione ad un particolare processo (permette una comunicazione da processo a processo)
- ![[Livello di trasporto#Demultiplexing con connessione - TCP]]
_Controllo della connessione_ 
- meccanismi di inizio e fine trasmissione (controllo di sessione)
_Trasferimento dati ordinato e affidabile_
- si intende la capacità di correggere tutti i tipi di errore, quali:
	- dati corrotti 
	- segmenti persi 
	- segmenti duplicati 
	- segmenti fuori sequenza 
_Controllo di flusso_ 
- evitare di spedire più dati di quanti il ricevitore sia in grado di trattare 
_Controllo di congestione_ 
- ha lo scopo di recuperare situazioni di sovraccarico nella rete
_Trasferimento bufferizzato_: 
- Il software del protocollo TCP è libero di suddividere il flusso di byte in segmenti in modo indipendente dal programma applicativo che li ha generati. Per fare questo è necessario disporre di un BUFFER dove immagazzinare la sequenza di byte. Appena i dati sono sufficienti per riempire un segmento ragionevolmente grande, questo viene trasmesso attraverso la rete. 
-  La bufferizzazione consente una riduzione del traffico sulla rete "ottimizzando" il numero di segmenti da trasmettere
![[Pasted image 20230105192435.png]]
Questo flusso di byte viene diviso in segmenti 
![[Pasted image 20230105193418.png]]


## Segmento TCP
![[Pasted image 20230105193953.png]]
il Segmento TCP è composta da due parti intestazione e Dati
Intestazione: 
- Porte di sorgente e arrivo:  Utili per distinguere una connessione da un altra
- _Numero di sequenza_ : è il numero del primo byte di dati nello stream totale
	- Se è settata la flag _SYN_ allora il numero di sequenza è _ISN_ (Initial sequence number) e il primo byte di dati è _ISN+1_
- _numero di riscontro_: solo se la flag _ACK_ è settata questo campo contiene il valore del prossimo numeri di sequenza che il mittente del segmento si aspetta di ricevere dal altro host. 
	-  una volta che la connessione è stabilita è sempre inviato
	- se $ACK = x+1$ si interpreta come ho ricevuto tutti i precedenti $x$ byte
- _Hlen_: lunghezza del header TCP espressa in parole da 4 byte
	- Solitamente vale 0101 ovvero 5 parole. quindi 20 byte totali

#### Flag
- _URG_: Il campo Puntatore Urgente contiene dati significativi da trasferire in via prioritaria 
- _ACK_: Il campo Numero di Riscontro contiene dati significativi 
- _PSH_: Funzione Push (trasferimento immediato dei dati in un segmento dal trasporto al livello applicativo) 
- _RST_: Reset della connessione 
- _SYN_: Sincronizza il Numero di Sequenza 
- _FIN_: Non ci sono altri dati dal mittente – chiusura della connessione
- ![[Pasted image 20230105203729.png]]

- _Finestra di ricezione_ : indica il numero di byte di dati a partire da quello indicato nel campo Numero di Riscontro che il mittente di questo segmento è in grado di accettare. Serve per il controllo di flusso 
-  _Checksum_: checksum dell’intero pacchetto (dati, header TCP + parte dell’header IP) per rilevare errori (se i bit del segmento sono stati alterati). Si calcola come per UDP (per TCP è obbligatorio).
- _Opzioni_ (facoltativo, lunghezza variabile, max 40 byte): negoziazione di vari parametri: ad es. dimensione massima segmento (MSS), selective acknowledgement supportato e blocchi di dati riscontrati selettivamente. Le opzioni sono sempre multipli di 8 bit e il loro valore è considerato per il calcolo della checksum.
- _Puntatore Urgente_: questo campo è un offset positivo a partire dal Numero di Sequenza del segmento corrente. E' interpretato solo se il bit URG è uguale ad 1. Punta al primo byte di dati non urgenti a partire dal Numero di Sequenza, e consente di far passare i dati urgenti in testa alla coda di ricezione. Nel segmento contenente dati urgenti deve essere presente almeno un byte di dati. 
	- Ad esempio se un segmento contiene 400 byte di dati urgenti e 200 byte di dati non urgenti, il puntatore urgente vale 400
	- la loro gestione però è affidata all’applicazione



# Gestione della connessione TPC

## Handshake a tre vie
è l algoritmo per l pretura della connessione tra client e server con TPC

![[Pasted image 20230105205839.png]]
1. Il client invia una richiesta di connessione a un server TCP è attivo il bit _SYN_, il segmento _non contiene dati_ si trasmette anche un numero di _sequenza iniziale casuale_ (ISN)
2. Il server estrae il segmento, alloca i 2 buffer (ingresso uscita) e le variabili TCP per il controllo di flusso, invia poi in risposta un segmento di connessione garantita al client (chiamato SYNACK) 
	1. è attivo SYN, il numero di sequenza è il valore iniziale (es. server_isn = 78) 
	2. è attivo ACK, il server aspetta client_isn+1 (es. 42) 
	3. _Esempio_ SYN=1, ACK = client_isn +1, proprio numero di sequenza iniziale server isn. Segmento SYNACK
3. il client alloca buffer e variabili di connessione manda un riscontro positivo del messaggio del server. 
	1.  _SYN_=0. Questo segmento può già trasportare dati 
	2. il prossimo dato sarà client_isn+1 (42) ed il client attende _acq_= server_isn+1 (79) 
	3. _SYN_=0, riscontro server_isn+1. 
4. Connessione instaurata, inizio scambio dati

>[!note]
>Dopo l handhaking a livello di trasporto non c è più distinzione tra client e server

![[Pasted image 20230105212739.png]]


#### Perche tre vie
![[photo_2023-01-05_21-40-24.jpg]]
![[Pasted image 20230105214222.png]]
## Chiusura della connessione
![[Pasted image 20230105215055.png]]
- _TIME_WAIT_ è lo stato finale in cui il capo di una connessione che esegue la chiusura attiva resta prima di passare alla chiusura definitiva della connessione 
	- due volte la _MSL_ (Maximum Segment Lifetime). 
		- _MSL_: è la _stima_ del massimo periodo di tempo che un pacchetto IP può vivere sulla rete; questo tempo è limitato perché ogni pacchetto [[Livello di rete - IP|IP]] può essere ritrasmesso dai [[Livello di rete - Router|Router]] un numero massimo di volte (detto hop limit). 
	- Ogni implementazione del TCP sceglie un valore per la _MSL_ (RFC 793 2 minuti, Linux 30 o 60 secondi). 
- Lo stato _TIME_WAIT_ viene utilizzato dal protocollo per due motivi principali: 
	- implementare in maniera affidabile la terminazione della connessione in entrambe le direzioni. 
		- Se l’ultimo _ACK_ della sequenza viene perso, chi es egue la chiusura passiva manderà un ulteriore _FIN_, chi esegue la chiusura attiva deve mantenere lo stato della connessione per poter reinvitare l'_ACK_ 
	- consentire l'eliminazione dei segmenti duplicati in rete. (come no capito)
#### Half-Closed
![[Pasted image 20230105215821.png]]
![[Pasted image 20230105215843.png]]

#### Chusare con HandShake 3 vie
![[Pasted image 20230105220237.png]]


### Schema generale apertura e chiusura 
![[Pasted image 20230105220529.png]]
![[Pasted image 20230105220552.png]]

-  _LISTEN_ - represents waiting for a connection request from any remote TCP and port. 
- _SYN-SENT_ - represents waiting for a matching connection request after having sent a connection request. 
- _SYN-RECEIVED_ - represents waiting for a confirming connection request acknowledgment after having both received and sent a connection request. 
- _ESTABLISHED_ - represents an open connection, data received can be delivered to the user. The normal state for the data transfer phase of the connection. 
- _FIN-WAIT-1_ - represents waiting for a connection termination request from the remote TCP, or an acknowledgment of the connection termination request previously sent
- _FIN-WAIT-2_ - represents waiting for a connection termination request from the remote TCP. 
- _CLOSE-WAIT_ - represents waiting for a connection termination request from the local user. 
- _CLOSING_ - represents waiting for a connection termination request acknowledgment from the remote TCP. 
- _LAST-ACK_ - represents waiting for an acknowledgment of the connection termination request previously sent to the remote TCP (which includes an acknowledgment of its connection termination request). 
- _TIME-WAIT_ - represents waiting for enough time to pass to be sure the remote TCP received the acknowledgment of its connection termination request. 
- _CLOSED_ - represents no connection state at all.

## Trasferimento dati affidabile
TPC iplementa il trasferimento affidabile di dati al di sopra del protocollo ip che di perse non lo è  per farlo utilizza i campi _checksum_ e i messaggi di riscontro con _numero di sequenza_, _numero di riscontro_, _riscontro cumulativo_

![[Pasted image 20230105223542.png]]
puo anche arrivare in pipeline
![[Pasted image 20230105223908.png]]

#### Lato Mittente
- TCP riceve i dati del applicazione dell [[Livello Applicativo]] 
- Incapsula i dati in uno o più segmenti e assegna numero di sequenza 
- _Avvia il timer_ di ritrasmissione (timeout di ritrasmissione - _RTO_) 
	- Il timer viene avviato se non è già in funzione per un qualche altro segmento
- Ritrasmissione dei segmenti in caso di: 
	- _Timeout_ 
		- Ritrasmette il segmento che non è stato riscontrato e che ha causato il timeout
		- Il timer viene riavviato 
	- Ricezione di tre _ACK duplicati_ 
		- Se il mittente riceve tre _ACK_ duplicati, il segmento successivo a quello riscontrato è andato perso. quindi si fa la  _Ritrasmissione veloce_(fast retransmission), ovvero si ritrasmette prima della scadenza del timer
- _Segmenti fuori sequenza_ : messaggi Urgenti  
	- I dati possono arrivare fuori sequenza ed essere temporaneamente memorizzati dall’entità TCP destinataria 
	- Il TCP non dice come il destinatario deve gestire i pacchetti fuori sequenza, dipende dall'implementazione 
	- Nelle versioni più recenti si implementa la Selective ACK (SACK) 
		- i pacchetti ricevuti fuori sequenza vengono memorizzati 
		- riscontro di pacchetti fuori sequenza e duplicati inviato in OPTIONS
![[Pasted image 20230105224041.png]]
#### Lato Destinatario
1.  Tutti i segmenti inviati per trasmettere dati includono ACK 
2. Se destinatario non ha dati da inviare e riceve segmento «in ordine» ritarda invio ACK di 500ms a meno che non riceva nuovo segmento 
3. Se destinatario riceve segmento atteso e precedente non è stato riscontrato allora invia immediatamente ACK 
4. Se destinatario riceve 
	1. segmento _fuori sequenza_ 
	2. _«mancante»_ («buco» in una sequenza) 
	3. duplicato
5. allora invia immediatamente un segmento ACK (indicando prossimo numero atteso)

##### Operativita normale 
![[Pasted image 20230105225514.png]]
##### Segmento smarrito
![[Pasted image 20230105225538.png]]
##### Ritrasmissione veloce
![[Pasted image 20230105225555.png]]
##### Riscontro smarrito 
![[Pasted image 20230105225622.png]]
##### Riscontro perso corretto da ritrasmissione
![[Pasted image 20230105225659.png]]


#### Graficamente come macchina a stati
![[Pasted image 20230105225734.png]]
![[Pasted image 20230105225749.png]]

### Calcolo del time out
- Il _tempo di timeout_ (RTO) è fondamentale per il funzionamento di TCP 
- Deve essere maggiore di _RTT_ (Round Trip Time) 
	- _RTT_: tempo trascorso da quando si invia un segmento a quando se ne riceve il riscontro 
- Viene calcolato analizzando gli RTT dei segmenti non ritrasmessi (Sample RTT, stimato per un segmento trasmesso – non per ogni invio)
		$$RTT_{ESTIMATED}= (1 - \alpha) * RTT_{ESTIMATED} + \alpha * RTT_{SAMPLE}$$
- _SampleRTT_ può fluttuare. Si considera _EstimatedRTT_: combinazione dei precedenti valori di EstimatedRTT con il nuovo valore SampleRTT
- viene posto  $\alpha=1/8$ in modo da rendere via via meno importanti gli RTT dei pacchetti più vecchi (RFC 2988)
- ![[Pasted image 20230105231152.png]]
- è necessario anche una stima della variabilità di RTT data dalla seguente formula 
- $$RTT_{DEV} = (1-\beta)\ RTT_{DEV} + \beta |RTT_{SAMPLE} - RTT_{ESTIMATED} |$$
- Stima di quanto _SampleRTT_ si discosta da _EstimatedRTT_ 
- viene posto $\beta=1/4$   (RFC 2988) 
- Una volta ottenuti questi valori, il timeout viene normalmente calcolato come $$RTO = RTT_{ESTIMATED} + 4 RTT_{DEV} $$
- In molte implementazioni, dopo un errore (es. ACK non ricevuto) si raddoppia il timeout: si tratta di un primo meccanismo di controllo della congestione

### Finestra di trasmissione 
- I dati inviati dal processo a livello applicativo sono mantenuti nel buffer di invio
- La trasmissione dei dati si basa sulla finestra di trasmissione (_sliding window_). 
	- finestra sovrapposta sulla sequenza\ da trasmettere 
	- _negoziata dinamicamente_ 
	- viene fatta avanzare alla _ricezione_ di un ACK
![[Pasted image 20230105232323.png]]
- _Sf_ (SendFirst): numero di sequenza del primo byte in attesa di essere riscontrato 
- _Sn_ (Send Next): prossimo byte da inviare (prossimo numero di sequenza da inviare)

### Finestra di Ricezione 
![[Pasted image 20230105232149.png]]
- _Rn_: Receive next 

## Controllo di flusso 
-  Ogni host imposta _buffer_ di invio e di ricezione 
- Il processo applicativo destinatario legge i dati dal buffer di ricezione (non necessariamente nell'istante in cui arrivano)
- Si intende con controllo di flusso la capacità del mittente di evitare la possibilità di saturare il buffer del ricevitore. 
	- Mette in relazione la frequenza di invio del mittente con la frequenza di lettura dell'applicazione ricevente
- TCP implementa questa caratteristica tramite una variabile detta finestra di ricezione (_rwnd_) mantenuta nel mittente: questa variabile fornisce un'idea di quanto spazio è ancora a disposizione nel buffer del ricevitore. 
- Tale valore è comunicato nel campo window dell'_header_ TCP
![[Pasted image 20230105232237.png]]
-  Spazio disponibile nel buffer del destinatario 
- $Rwnd= RcvBuffer-(LastByteReceived-LastByteRead)$ 
- Rwnd è dinamica 
- L'host destinatario comunica la dimensione di rwnd al mittente 
- Il mittente si assicura che $LastByteSent-LastByteAcked ≤ Rwnd$ Quantità di dati trasmessi e non ancora riscontrati 
>[!nota]
 N.B. se $rwnd=0$, il mittente manda segmenti «sonda» di 1 byte per ricevere l’aggiornamento sulla dimensione di rwnd
 
![[Pasted image 20230105232258.png]]


### Controllo di congestione
Il controllo della conestione serve per modulare la velocita di trasmissione di TPC a secondo della _congestione percepita_ sulla rete
la congestione è alta se ci sono troppe sorgenti che trasmettono troppi dati a una velocita elevata ciò può portare a 
- Lunghi ritardi  per gli accodamenti nei buffer dei router
- perdita di pacchetti per l overflow dei buffer dei router

![[Pasted image 20230106000414.png]]
questa gestione cambia la finestra di invio di TCP rendendola $=min(rwnd,cwnd)$
Quindi rate di invio non può superare $min(rwnd,cwnd)/RTT$

#### Congestion Windows: cwnd
-  Si misura tipicamente in MSS 
- 1 _MSS_ (Maximum Segment Size) è la quantità massima di dati trasportabili da un segmento. 
	- Determinato in base alla _MTU_ (unità trasmissiva massima) 
		- _MTU_: lunghezza massima del payload del frame di [[Livello di collegamento|collegamento]] inviabile dall’host mittente 
	- MSS scelto in modo tale che il segmento TCP, incapsulato in pacchetto [[Livello di rete - IP|IP]], stia dentro un singolo di frame di collegamento 
- _RTT_ (Round Trip Time) è il tempo impiegato da un segmento per effettuare il percorso di andata e ritorno


### Fasi gestione Congestione
#### Additive Increase Multiplicative Decrease: AIMD
- TCP del mittente aumenta proporzionalmente la propria finestra di congestione ad ogni ACK ricevuto.
- Ad ogni ACK $cwnd= cwnd+1/cwnd$
	- che vuol dire che ogni volta che raggiunge la sua finestra di congestione in  ACK questa aumenta di uno
 ![[Pasted image 20230106003113.png]]
- ogni Perdita dimezza la cwnd quindi $cwnd = \frac{cwnd}{2}$
![[Pasted image 20230106003249.png]]
#### Slow Start
1. al inizio la finestra di congestione è settata ad 1
2. per ogni _ACK_ non duplicato ricevuto aggiungo 1 _MSS_ alla finestra di congestione
	1. Crescita esponenziale 
![[Pasted image 20230106002515.png]]


### TCP RENO
1. Inizialmente viene definita una variabile “_soglia_”, alla quale è assegnato un valore alto (es. 64 KB). 
2. La soglia determina quando termina la partenza lenta (_slow start_) ed inizia la fase di _congestion avoidance_ (AI)
	1. Se _cwnd < soglia_, cwnd aumenta esponenzialmente (slow start) 
	2. Se _cwnd > soglia_, cwnd aumenta linearmente (Additive Increase) 
3. Evento di perdita 
	1. Se ho _3 ACK duplicati_ 
		1.  soglia =  metà di cwnd 
		2.  cwnd = soglia + 3 MSS (_fast recovery_) 
	2. Se ho un ACK perso per _timeout_ 
		1.  soglia a metà di cwnd 
		2. pongo cwnd = 1 MSS (_slow start_) 
4. Nella fase fast recovery: 
	- se avviene un timeout si va in _slow start_ 
	- finché continuano ad arrivare ACK duplicati cwnd=cwnd+1 
	- se arriva un nuovo ack (non duplicato) si va in
		- _congestion avoidance_ 
		- cwnd=soglia
![[Pasted image 20230106004045.png]]
![[Pasted image 20230106004104.png]]
![[Pasted image 20230106004132.png]]


### TPC Tahoe
simile al TCP RENO ma senza fast recovery
![[Pasted image 20230106004214.png]]
![[Pasted image 20230106004230.png]]



### TCP CUBIC
-  _Wmax_: rate di invio quando è stata rilevata congestione 
- Lo stato di congestione del collegamento “collo di bottiglia” probabilmente (?) non è cambiato molto 
- Dopo aver dimezzato la finestra in seguito ad un evento di perdita, in una prima incremento verso _Wmax_ più veloce, ma poi avvicinamento a Wmax più lento
![[Pasted image 20230106005203.png]]
- K: punto nel tempo in cui la cwnd raggiungerà Wmax 
- K stesso è configurabile 
- Incrementi maggiori quando siamo lontani da K 
- Incrementi più piccoli (cauti) quando siamo più vicini a K



### Explicit congestion notification (ECN)
-  Le implementazioni TCP spesso implementano un meccanismo di controllo di congestione network-assisted: 
	- due bit in header IP (campo _ToS_) settati dai router per indicare la congestione 
	- Informazione di congestione inviata a destinazione 
	- La destinazione imposta il bit ECE (ECN-Echo) bit nel segmento di riscontro per notificare la congestione al mittente 
	- Il mittente setta il bit CWR (Congestion Window Reduced) per indicare che ha ricevuto la notifica di congestione 
- Coinvolge sia [[Livello di rete - IP|IP]] che TCP
![[Pasted image 20230106005326.png]]



## Fairness TPC
 - Ipotesi:
	 - K connessioni TCP insistono su un unico link di capacità R bit/s 
	 - Le connessioni hanno gli stessi valori di MSS e RTT 
	 - Non ci sono altri protocolli che insistono sullo stesso link 
 - Risultato: 
	 - Ognuna delle connessioni TCP tende a trasmettere R/K bit/s
![[Pasted image 20230106005518.png]]



>[!note]
>connessioni con RTT più piccolo variano più velocemente congwin e raggiungono throughput superiori a connessioni con RTT maggiore
>Connessioni TCP parallele 
>-  Un’applicazione può aprire connessioni multiple in parallel tra due host 
>- Tipico per i web browsers e.g.,  
>- Collegamento con rate R con 9 connessioni esistenti connections: 
>	- new app apre 1 sessione TCP, ottiene un rate R/10 
>	- new app apre 11 sessioni  TCP ottiene  R/2