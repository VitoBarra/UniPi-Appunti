---
type: nota
course: Reti e Laboratorio di reti
topic: 
tags: RETI_LAB3 
---

Prev: [[Reti - lab 3 MOC]]

# Livello di rete - Router
---
parte della [[Livello di rete]] 


il router svolge due funzioni principali 
- _Inoltro_ :  questo vive nel _paino data_ ote al trasferimento dei dati
	- Utilizza da tebella di inoltro 
- _routing_: questo vive nel _Control pale_ e potrebbe essere implementato anche piu in alto rispetto al livello rete 
	- è il processo decisionale di scelta del percoso verso una destinazione
		- riempe la tabella di inoltro
	- utilizza _Algoritmi di routing_

Ci sono due paradigmi che convivono al momento su internet
quello dove il Control plane è implementato direttamente nei router
![[Pasted image 20230108011454.png]]
- i router stessi applicano algoritmi di routirng per rimpire la tebella di inoltro 
- i router si scambiano messaggi tra di loro 

e quelli che si affidano a un controllore anche detta _Software-defined Networking (SDN)_
![[Pasted image 20230108011531.png]]
- applicabile solo per una porzione di router che sono controllato da una singola organizazione
- visione _più globale_ sul insieme di router gestiti quindi routing  e controllo di congestione più ottimali
- molti _pacchetti_ che vanno verso il controllore per la gestione delle statisstiche della connessioni, quindi _overhead_
- introduzione di un possibile _single point of failure_


### Struttura generale Router
![[Pasted image 20230108012907.png]]
- _Routing processor_: implementato in _software_ gestisce gli algoritmo di routing, eventi rari
- tutto il resto è _hardware_ e gestisce l inoltro

- ##### Porte di input:
![[Pasted image 20230108013230.png]]
	- _Line termination_: Recezione dei bit [[LIvello fisico]]
	- _link layer Protocol_: [[Livello di collegamento]]
	- _Lookup forwarding_: 
		- Ha una copia della tabella di inoltro, usa i valori dell’header per determinare la porta di output 
		- Elaborazione alla velocità “line rate” 
		- _Accodamento_: se la velocità con cui arrivano I datagrammi supera la velocità di inoltro nella struttura di commutazione (_switching fabric_)
- ##### Switching fabric:
	- trasferisce il pacchetto dal buffer di input al buffer di output appropriato
	- velocità di commutazione: velocità con cui i pacchetti possono essere trasferiti dagli ingressi alle uscite 
		- N input: velocità di commutazione auspicabile N volte la velocità di linea
![[Pasted image 20230108013450.png]]
- ##### Porte di output:
	-  _buffering_ richiesto quando i datagrammi arrivano dalla struttura di commutazione ad una velocità maggiore della velocità di trasmissione sul collegamento in uscita 
	- _Scheduling_: politiche per definire l’ordine di trasmissione dei datagrammi
![[Pasted image 20230108013734.png]]

Se ci sono ritardi e perdite di solito sono per l attesa nei buffer o se questi sono pieni.

### Protocolli di routing
questi protocolli cercano di determinare percorsi _buoni_ per arrivare da un mittente a un destinatario
- per _buono_ : sipossono prendere varie metriche come il numero di hop o meno congestionato
- _percorso_: inteso come sequenza di router
- ![[Pasted image 20230108015257.png]]

per il calcolo del percorso minimo si astrare la rete utilizzando un [[Grafo]] pesato 
![[Pasted image 20230108015335.png]]
Ci sono piu tipo di soluzione al problema del routing e possiamo categorizarli
![[Pasted image 20230108015943.png]]
	 • Nel routing statico le righe (entry) della tabella vengono configurate manualmente dall’operatore. Tale metodo viene usato per reti di piccole dimensioni e la cui topologia non varia molto, dove è possibile prevedere tutti i possibili percorsi di un pacchetto IP nella rete. • Nel routing dinamico esistono protocolli specifici che provvedono automaticamente ad inserire nella tabella del router le entry relative ai possibili percorsi. Viene usato nelle reti di medie-grandi dimensioni e con topologia variabile (grandi reti locali private e Internet)
	 • Gli algoritmi di instradamento si possono classificare in: • Globali, se si basano sulla conoscenza della topologia di tutta la rete. Il calcolo può essere fatto in un unico sito (es. SDN) o in più nodi, utilizzando informazioni sulla connettività di tutti i nodi e sui costi di tutti i link (es. algoritmo Link State). – L’algoritmo riceve in ingresso informazioni su tutti i collegamenti tra i nodi e i loro costi. • Decentralizzati, quando nessun nodo conosce la topologia di tutta la rete, all’inizio ha informazioni solo sui nodi e link vicini. Il calcolo del percorso è iterativo e distribuito (es. algoritmo Distance Vector). – Ogni nodo elabora un vettore di stima dei costi (distanze) verso tutti gli altri nodi nella rete. – Il cammino a costo minimo viene calcolato in modo distribuito e iterativo scambiandosi informazioni con i nodi vicini.


## Distance vector
#### Categorizazione
Un algoritmo DI Routing Dinamico Decentralizzato è
- _Distribuito_: 
	- ogni router riceve parte delle informazione da uno  più nodi direttamente connessi
- _iterativo_:
	- ci vongolaio più passaggi prima che l algoritmo converga  verso la fine
- _Asincrono_: 
	- I router possono lavorare indipendentemente da gli altri e possono farlo contemporaneamente
##### Terminalogia
- _Costo_ $c(x,z)$: distanza tra nodo sorgente x e un nodo _vicino_ z 
- _Distanza_ $d_{cy}$ ovvero la distanza tra un nodo c e un nodo y passando per n nodi _intermedi_
l algoritmo si basa sul [[Equazione di bellman-Ford]] che bevemente dice
- sapendo il costo tra un sorgente x e un nodo vicino z 
- sapendo la distanza da v a y passando per nodi intermedi
si puo calcolare la distanza tra x e y
$$d_{xy}=min_v\{c(x,v)+d_{vy}\}$$
sclego il minimo tra tutte le possibili v
![[Pasted image 20230108021107.png]]
![[Pasted image 20230108021902.png]]
- inizialmente tutti i nodi conoscono solo il costo per arrivare ai vicini e interattivamente guardando i distance vector dei vicini si aggiornano i percorsi da nodo in questione e un altro scelto, facendo più volte questo passaggio si converge a valori stabili
- questa operazione può essere fatta da tutti i nodi contemporaneamente.

#### Aggiornamento dei pesi
Se un costo cambia si reitera l algoritmo e si ristabilizzano i valori
- Se i cosi migliorano si stabilizza velocemente 
- se i costi peggiori potrebbe mettermi molto tempo a stabilizzare i valori
##### Count to infinity Problem
per motivi di asincronia puo capitare che un nodo si ritrovi ad essere in un percorso piu vantagioso del collegamento diretto quando questo non è ancora stato aggiornato portando cosi a contare l infinito 


y si accorge che il collegamento verso x ha un nuovo costo di 60, ma z ha detto che la sua distanza da x è 5. Quindi y calcola la nuova distanza verso x, 6, e invia una notifica a z. z apprende che il percorso verso x tramite y ha costo 6, così aggiorna la sua distanza verso x (7) e invia una notifica a y … e così via…
![[Pasted image 20230108023311.png]]
una soluzine è 
_Split-horizon with poisoned reverse_



### Link-State algorithm
Algoritmo per il Routing dinamico
#### categorizazione
- _Globale_
#### Funzionamento
1. ogni nodo manda inizialmente consce solo il collegamento ai suoi vicini
	1. ![[Pasted image 20230108232839.png]]
1. ogni nodo manda in broad cast i costi che conosce
2. si Crea un link-state database ovvero una matrice che indica i costi ad un nodo ad un altro 
	1. ![[Pasted image 20230108233109.png]]
3. su questa si applica l [[Algoritmo di Dijkstra]] per la ricerca del cammino minimo e si utilizza questo per scegliere dove inoltrare i pacchetti


### Protocolli di routing 
internet non è una struttura piatta di router ma funziona gerarchicamente diversi _sistemi autonomi_ (SA), queste possono avere internamente diversi algoritmo e protocolli 
 - un AS è un gruppo di router sotto lo stesso controllo amministrativo
 - un amministrazione puo contenere piu AS es ISP che partizione i suoi router in piu AS
![[Pasted image 20230108235111.png]]
i protocolli di routirng si differenziano tra 
1. _Interior gateway Protocolo_ (IGP): ovvero protocolli che lavora con i router nella stessa AS
	- Routing Information Protocol (RIP)
	- Open Shortest Path Frist (OSPF)
 2. _Exterior Gateway Protocol_ (EGP): ovvero protocolli  di routing tra AS.
	 - Border gatawey Protocol (BGP)

i IGP da soli determinano il routing tra router della stessa amministrazione e
iGP E EGP insieme calcolano il routing tra AS diversi.


### Routing Information Protocol: RIP
- Utilizza il [[#Distance vector]] 
- il costo é contato come numero di stalti
- aggiornamenti mandati ogni 30 secondi o prima se la tabella cambia 
- ![[Pasted image 20230109003111.png]]
### Pen Shortest path Frist OSPF
- utilizza [[#Link-State algorithm]]
- utilizza Ip per mandare i messaggi brodcast
- la metrica puo essere impostata
- questo algoritmo è pensato per reti molto grandi ma potrebbero andare a geenrare troppo traffico di controllo quindi si divide gerarchicamente in 2 parti
	- backbone
	- Aree di touter
	- ![[Pasted image 20230109003129.png]]

### Border Gateway Proocol (BGP)
- Permette definire come arrivare da un sistema autonomo ad un altro
- i router di bordi propagano i AS ragiungibii scambiando dei messaggi con gli atro router di bordo
- ha sia sessioni interne che esterne al AS
- in caso di multiple rotte si va a scgliere con le _Local-PREF_ che vanno a configurare i parametri di preferenze
	- permette di configurare parametri di preferenza di passaggi tra AS
		- Ad esempio se si vuole evitare di passare par un AS per una data posizione fisica

## IPv6
Motivazioni (e soluzioni)
-  Esaurimento indirizzi a 32 bit 
	- indirizzi a 128 bit 
- Velocizzare elaborazione e forwarding pacchetti 
	- lunghezza fissa (40 byte) dell’header 
	- eliminato checksum 
- Risparmiare ai router costo frammentazione 
	- ICMPv6: msg “packet too big” (sorgente deve preoccuparsi della frammentazione) 
- Facilitare QoS 
	- introdotta “flow label” per identificare datagram appartenenti allo stesso “flow”
	- (p.e. insiemi di pacchetti che richiedono un trattamento speciale come QoS p.e. audio video, high-priority traffic)
![[Pasted image 20230109004557.png]]
#### Tunneling
se si lavora in IpV6 e ci sono dei percorsi che hanno segmenti di rete con ipv4 
![[Pasted image 20230109004908.png]]
per garantire la consegna si utilizza il tunneling ovvero
il datagramma che viaggia con il pv6 prima di passare ad un router ipv4 è incapsulato in un datagramma IPv4. una volta uscito da tunnel si decapsula e torna a viaggiare il datagramma originale 
nel ipv4 del header aggiunto la sorgente sara l indirizzo ipv4 di B e come destinazione E
![[Pasted image 20230109005738.png]]
Se c è Frammentazione nel tunnel viene riassemlato dal router che supporta Ipv6 alla fine dle tunnel quindi in questo esempio E 


