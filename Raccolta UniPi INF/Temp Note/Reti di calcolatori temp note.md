R2022-09-21 RETI TEORIA
Reti di calcolatori: modello architettura le e stack di protocolli alla base di internet 

Protocolli
- Routing 


Cos é internet? Interoperabilità di multiple reti diverse sia in tipo che in dimensione 

### protocolli :
- regole di comunicazione definito dallo standard IETF
### Componenti di una rete su internet:
- end Device (o sistemi terminali ) (Host):
	- Dispositivi  (pc, smartphone, ecc)
	- Server (di solito in data center)
- Link :
	- Infrastrutture di collegamento
- Dispositivi di interconnessione:
	- Router : connette Una rete a internet 
	- Nore: l internet provider è fatto da solo router e fa da snodo alla connessione 
- Switch: collega gli host al router 
### servizi
- I servizi è ciò che la rete offre al livello applicativi  


# tipi di reti Divisi per grandezza:
- LAN: Local Area network
	- Topologia di comunicazione :
		- BUS (non più usato per problemi di collisione)
		- A Stella  (punto di comunicazione centralizzato, più comune oggi ) 
- WAN: Wide Area Network:
	seve a connettere tra di loro più LAN
	- Topologia di comunicazione:
		- Punto Punto:
		- Commutazione: in comunemente usata da  un internet service provide 
	- Esempi:
		- Rete di Ricerga GARR


# ISP
Per collegare I vari Host c è bisogno di ISP (internet servic pprovider) che danno i percorsi per connettere i diversi host. Per connettere gli ISP  si utilizza degl Internet exchange point che servono per mettere in comunicazione host che si connetto ad ISP diversi. Possono esserci anche delle connessione dirette. c è una gerarchia degli ISP 

(aggiungere foto )




tim Bernal clive Ted X  (vedere per lo standard HTTP)

# livelli di stack 
- Application
- Network 
- Link 


# Modello dati top-Down vs bottom-up
modello a clessidra inserire immagine 


Negli anni la richiesta di stress sulla rete è in aumento (inserire immagine Grafico )


2022-09-23: RETI  

## Commutazione di pacchetti e commutazione di circuito 

Una internet e una interconnessione di reti composte da link e dispositivo capaci di. Scambiarsi informazioni.
- sistemi terminali (host)
- Dispositivi di intercomunicazione che si trovano sul percorso

### problema:
  bisogna trovare un percorso da l host sorgente al hos t destinatario. Per fare questo abbiamo le _tecniche di commutazione_: 
  - ## circuit-switch: 
	  - dedicare le risorse alla comunicazione che si vuole fare 
	  - dura per tutta la durata della comunicazione
		  - pro: 
			  - la performance è garantita siccome la connesione resta stabile 
			  - Tariffazione facile
		  - contro:
			  - Fase di SetUp: gestire la richiesta di comunicazione che arriva alla rete, calcolare le risorse necessarie e assegnare quelle risorse  
			  - Spreco di risorse: queste restano in attive se non utilizzate 
				  - (es.  nelle telefonate durante i silenzi non si sta usando la risorsa assegnata )
	  - tecnica di riserva delle risorse: 
		  - _Frequency Division Multiplexing_ (FDM):  la bambina totale di frequenza viene divisa in sotto bande più piccole e ogni comunicazione diversa ha una manda fissa per tutta la durata della comunicazione 
		  - _Time Division Multiplexing_(TDM): divido l intervallo in tempi più piccoli e per ogni intervallo di tempo un utente puo utilizzare tutte le frequenze 
  - ## commutazione di pacchetto: 
	  - il messaggio viene diviso in unita Della comunicazione chiamati pacchetti.
	  - i pacchetti vengono inviati sulla rete che li instrada vero l host destinazione.
	  - La rete è in condivisione di risorse ovvero più pacchetti di comunicazioni anche diverse possono usare la stessa risorsa per arrivare a destinazione 
	  - pacchetti della stessa comunicazione possono seguire strade diverse per arrivare a destinazione. 
		  - Questo perchè la strada iniziale potrebbe vararla siccome potrebbe congestionare o i potrebbe aprire una  percorso migliore.
		  - I router utilizzano le tabelle di inoltro per instradare i pacchetti che si aggiornano meno spesso del tempo di trasmissione di un messaggio 
	  - _stora e forward_ : 
		  - Il router deve ricevere l intero pacchetto prima di poterlo inviare
			  - Facendo cosi c è un ritardo di accostamento siccome devono arrivare pi pachetti
			  - Se i pacchetti sono troppi non entrano nel buffer e quindi c è una perdita dei pacchetti
	  - i pacchetti sono grandi mediamente 500 byte
  - Pro:
	  - Risorse trasmissive usate solo se necessario
	  - Segnalazione non richiesta
  - Svantaggi:
	  - Tecnologie di inoltro non efficienti (necessita di selezionare l uscita per ogni pachetto
	  - tempo di elaborazione ai router (rooting table lookup )
	  - Accostamento al router
	  - Protocolli necessari per un trasferimento dati affidabile controllo della congestione 
  -  La commutazione di pacchetti gioca sul fatto spesso non tutti gli utenti sono attivi sul mezzo di comunicazione quindi ad esempio se una reta dovesse essere in grado di supportare 10 utenti attivo potrebbe supportare 35 utenti in totale che attività ”alternate”


Parametri delle reti:
- larghezza di Banda (bandwitdth):
- Velocità di trasmissione:
- Throughput: quantità di dati che possono essere trasmessi con successo da un nodo siorgente ad un nomo destinazione in un cero intervallo di tempo 
- Throughput < velocità di trasmissione 
	- Casi di collo di bottiglia 
- Il Throughput Non ha una definisiozne precisa dipende da cosa dobbiamo misurare
	- Caso di mezzo trasmissivo : il rate massimo oltre il quale si hanno sistematicamente perdite 
- Latenza:
	- Ritardo di accostamento:
		- Dipende dal intensità e dal tipo di traffico
		- _difficile da gestire_
	- RItardo di elaborazione al nodo: 
		- Controllo errori sui bit 
		- Decidere indirizzo di destinazione (ritardo di elaborazione)
		- 
	- Ritardo di trasmissione: 
		- Devo conservare e mandare l intero pacchetto e il ritardo provocato da questo arrivo si calcola con Lunghezza del pachetto / velocità di tarasmissione 




Standard: IO-OS