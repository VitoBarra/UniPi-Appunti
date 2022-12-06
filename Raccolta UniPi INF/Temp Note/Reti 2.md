

2022-10-26 :

## FTP 
serve per il trasferimento di fil e

un programma che implementa il protocolla ftp di solito ha un interaffia che comunica con il file system locale e il client FTP che si collega al server FTP e questo ci da accesso al file system della macchina remota. 

si possono scaricare risorse anche con HTTP ma FTP ha funzionalità in più come riorganizzare la struttura delle cartelle. 


## Modello di protocollo
due connessioni 
1. connessione DI controllo: scambio di comanda e risposte tra client e server. segue il protocollo telnet 
2. Connessione di daito: Connessione sui cui i dati sono trasferiti con modi e tipo specificati i dati trasferiti possono essere parte di un file,un file o un set di file
3. entrambi usano TCP
4. è un protoclosso statefull

> [!note]
>Porta di default: 2

appena si contata il server si apre una connessione controllo e solo quando il client vuole trasferire un file allora si procede con l apertura della connessione dati.

la connessione controllo è una connessione persistente mentre quella dei dati si chiude dopo il trasferimento.

PRendere da Slide lista Dei
- comandi di controllo.
- Codici di controllo (risposte



# Protocolli di trasporto
GEstisce la connesione logica END-TO-END.

## Protocollo TCP
è orientato alla connessione full- duplex ovvero la connessione si accorda tra chlient e serve e  una  volta stabilita si sia il client puo mandare messaggi al server che viceversa. 
opera per stream di byte: nello specifico i byte del messaggio sono una sequenza di byte ordinate ma non strutturati. 

non si limitare la velocità di trasferimento sulla connessione, il che puo portare a perdita di messaggi se i buffer del riceventi si saturano. in questo caso  se ci sono eventuali perdite il protocollo si assicura di rimandare i pacchetti persi.


\[IMMAGINE dei DUE BUFFER \]

il flusso di byte viene partizionato in segmenti e ogni segmento viene aggiunto un HEADER TCP

HEADER:

\[AGGIUNGERE IMMAGINE PARTIZIONE HEADER\]

- numero di sequenza: indica il numero il numero del primo byte che ho messo nel segmento
- numero di riscronto: numero del ultimo byte +1 che sono state i correttamente ericevuti dal destinatario.
- FLAG:
	- immagine flag 






## Protocollo UDP


