---
Course: "[[Cloud Computing (CC)]]"
topic: nota
tags:
  - CC
---
# Container e Docker
---


### Cointainer 
un __container__ è un modo per fare virtualizzazione dei sistemi operativi in sostituzione a gli Hypervisor. in particolare si installa il Container Manager.

![[IMG_0517.jpeg]]
funzionano perché sfruttano la capacita del [[Sistemi Operativi|OS]] linux di fa convivere più istanze User-space isolate. 
questo porta ai _vantaggi_ dei container che sono:  
- Piu leggeri ed efficienti in termini di velocità e memoria
- piu veloci da avviare 
ma portano ad uno _svantaggio_
- utilizzano tutti lo stesso sistema operativo 
	- meni sicuri 


### Docker
docker ha aggiunto alle tecnologie gia presenti dei container la possibilità di fare le cose facilmente e velocemente rendendo cosi questa tecnologia accessibile.
usa le due piattaforme:
- _Docker Engine_: per creare e avviare container
- _Docker Hub_: per distribuire containers


#### Che problemi affronta docker
con docker si puo risolvere il problema della portabilità del software
#### Come l affronta
le componenti del software come il software che si sta sviluppando e tutte le sue dipendenze vengono impacchettata in un file chiamato _Images_ o imagini che sono template per creare e mandare in esecuzione _Containers_. Questi container sono _volatili_ il che vuol dire che una volta cancellati si cancellano anche tutti i suoi file
- per affrontare questo problema si possono montare dei _[[Volumi|volumi]]_ esterni per garantire la persistenza dei dati salvati su quel volume.
 

### Docker Images
- Read Only template da usare per crare container
- Conservati in _Repository_ private e publiche
- le _repository_ sono salvate nei _Docker registry_.il docker registry piu grande è Docker hub 
- ogni _repository_ contiene un set di immagini che rappresentano le varie versione del software
- le _versioni_ sono identificate come _Repository:tag_
- piu _immagini_ si possono comporre per creare software arbitrariamente complesso
	- il piu basso viene chiamato _base image_
	- i container avviati possono  scrivere solo nel Top Layer di questa composizione, queste modifiche possono essere salvate creando una nuova imagine 
	 
![[IMG_0518.jpeg]]

###  Comandi Docker
per costruire delle imagini si utilizza il _DockerFile_. 
in questi file si parte da delle immagini prese dai i _docker registry_. si parte da altre porte per fare lo stack di immagini che volgiamo utilizzare 

Comandi Docker file:
- _FROM_ {Imagine}:{Tag} 
	- immagine di partenza
- _COPY_ {Path nel imagine} {path nel immagine}
- _RUN_ : {command}
	- è uno step di esecuzione di building del immagine. dopo l esecuzione di RUN viene fatto il commit dello stato del container nel immagine.  
- _EXPOSE_ {Port}
	- questo comando rendere possibile accedere alla [[Interfaccia Socket#Identificare un processo|porta]] {port} utilizzata al interno del container (ed esempio 80 nel caso di PHP apache
- _CMD_: \[{cmd command},{command arg}\] 
	- avvia un comando di default nel cmd una volta avviato il container
	  

Comandi Docker:
- Docker _build_ - t {images nome}:{tag}
	- costruisce l immagine a partire da quel _docker file_
	- -t {images nome }:{tag} specifica il nome del immagine che sis ta creando  
- Docker _run_ -p {host port}{cointainer port} {nome imagine}:
	-  per mandare in esecuzione un immagine come container.
	-  Flag
		- -p {host port}{cointainer port}: per il forwarding delle porte
		- -v {host path}{container path} per montare una carrella come [[Volumi]]

il _Forwarding_ delle porte è necessario altrimenti i dati arriverebbero solo al _OS host_ e si fermerebbero li. cosi facendo vengano inviate anche al container. si puo immagine come la porta del _container_ che si mette in ascolto _sulla porta del host_ che aspetta i dati  

### Ciclo di vita del container
il container muore con il finire del primo processo avviato. il che significa che conviene avviare un solo processo al interno el container 


### Docker compose 
_Docker compose_ ci permette di avviare insieme più container e permettere la comunicazione tra questi.
per creare un _docker compose_ si utilizza il _docker-compose.yml_ dove si specificano 

- _versione_: {numero} 
	- la versione del docker-compose file
- _service_:
	- Una lista di container da creare
	 
>[!tip]- Docker doc
>	Allegare link docker doc

internamente _docker compose_ construire un [[Livello di collegamento - VLAN|network virtuale]]  
questo risolve un problema difficile. ovvero semplifica l accesso di container a gli altri container passando per i nomi che specifichiamo sotto _services_. traducendo quei nomi nei relativi ID di processo 

Docker compose command:
- _docker-compose up_: per avviare il file _docker compose_ quest’oro costruirà le varie immagini se necessario e le mandare in esecuzione
- _docker-compose stop_: spegnere un compose di container 

### Docker Sworm
docker possiamo mandarlo in _sworm mode_ ovvero  una modalità che gestisce dei cluster di docker host chiamati _Swarm_
![[IMG_0519.jpeg]]
- i nodi dello Sworm possono funzionare come manager delegando task a i workers che eseguiranno quel task
- si puo definire lo stato desiderato e il numero di task che devono essere eseguiti da ogni servizio
- i nodi di _swarm manager_ assegnano ad ogni _nodo_ un nome [[Livello Applicativo - DNS|DNS]] e fa bilanciamento del carico di lavoro tra i nodi
- i nodi di _swarm manager_ monitorano lo stato del cluster e cercano di colmare la differenza tra lo stato attuale del cluster e quello _dichiarato_
	- un esempio è se dichiariamo di avere 10 servizi attivi di un immagine e ne cade una. i nodi _manager_ provvederanno ad avviare una nuova istanza 
![[IMG_0521.jpeg]]![[IMG_0520.jpeg]]
questo approccio si chiama _Declarative approach_