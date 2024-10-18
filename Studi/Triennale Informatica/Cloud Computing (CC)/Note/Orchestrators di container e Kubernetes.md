---
Course: Cloud Computing
topic: nota
tags: CC
---

Prev: [[Cloud Computing (CC)]]

# Orchestrators di container e Kubernetes
---
l orchestrazione di  [[Container e Docker|Container]] è il gruppo di operazioni che si fanno in certo casi verificabili durante il Runtime del applicazione/[[Microservices|microservizio]] alcuni esempi sono
- fallimento  di un container 
- la macchina che fa girare un container fallisce
- in cui più container devono comunicare come gestiamo il networking tra containers
- se abbiamo più macchine come decidiamo quali container vanno su quale machina

## Kubernetes 
è un software per l _orchestrazione dei container_. abbreviato spesso con K8s
- questo gestisce l intero ciclo di vita di un container. li avvia se servono e li uccide se non sono necessari.
- fornisce un meccanismo di comunicazione tra le appi anche se i container sottostanti vengono creati o distrutti
- dato un certo _work load_  e un insieme di macchine in un cluster. k8s analizza ogni container e assegna il task al macchina ottimale 


#### Dichiarativita
Kubernetes utilizza l approccio _dichiarativo_. quindi dichiariamo lo stato che vogliamo nel sistema e poi kubernetes se ne occuperà. 
Kubernetes:
- si accorge che lo stato corrente del sistema non è quello dichiarato.
- lo corregge rendendo il sistema self-healing
la _dichiarazione_ dello stato è fatta un un file .yaml

lo _stato_ è definito come una collezione di oggetti
- ogni oggetti ha specificato lo stato desiderato e uno status che rappresenta lo stato corrente
- k8s richiede a gli oggetti di controllare se lo stato corrente è uguale allo stato desiderato
	- se un oggetto non risponde k8s lo sostituisce con uno nuovo 
	- se un oggetto ha lo stato diverso da quello disiderato k8s eseguirà i rispettivi comando per risolvere il problema 
#### Distribuzione
k8s procede a unificare l interfaccia per l interazione tra _cluster di macchina_
![[IMG_0564.jpeg]]
#### Disaccoppiamento 
k8s funziona molto bene con le architettura a [[Microservices|microservizi]]. supporta nativamente l’idea di [[Principi di progettazione e qualità di un progetto#Disaccoppiamento|decoupled service]] quindi ogni funzionalità può essere modificata e scalata indipendentemente

#### Immutable infrastructure
per ottenere il meglio da k8s dobbiamo fare il deployment di _Infrastrutture immutabili_. ovvero di immagini che non cambiano il suo stato interno e possono essere spente ed avviate senza doversi preoccupare dello stato corrente del _container_. essenzialmente i container sono _stateless_.
- se vogliamo fare aggiornamenti, modifichiamo l immagine terminiamo la vecchia versione e avviamo la nuova.
le modifiche di stato dei _container_ devono essere fatte tramite [[Volumi|volumi]]  esterni. ad esempio montando un file di configurazione. 


#### Manifest
il file di dichiarazione dello stato di kubernetes è chiamato _manifest_ ed è una collezione di oggetti Chiamati _Pod_ (branco)
![[IMG_0565.jpeg]]
questo consistono in 
- uno o più container tra loro connessi
- un network layer condiviso
- Volume Condiviso

una collezione di _pod_ è detta _Deployment_
![[IMG_0566.jpeg]]
un _Deployment_ Specifica i vari pod e il numero di repliche associate a quel pod 
![[IMG_0567.jpeg]]

ad ogni pod è assegnato un [[Livello di rete - IP|IP]] unico che si può usare per comunicare con esso

Siccome gli esatti pod possono cambiare velocemente per via di rescaling o fallimenti dei pod, k8s offre un _Servizio_ che è un endpoint stabile che si occupera di direzionare il traffico al pod desiderato. anche se questo è cambiato nel frattempo.
- il servizio conosce a quale _pod_ dove mandare il traffico grazie a delle associazione i chiavi valori definite nei metadata.
![[IMG_0568.jpeg]]

![[IMG_0569.jpeg]]
gli oggetti _ingress_ è un oggetto che fornisce un _endPoint_ stabile per rendere accessibile l applicazione al esterno.
![[IMG_0571.jpeg]]
![[IMG_0572.jpeg]]


### K8S control plane 

il sistema di kubernetes funziona con la presenza in un cluster di macchine di uno o più nodi _master_ (se ne vuole più di uno per _fail tollerance_) e nodi _worker_.

#### master node
il master Node è diviso in put componenti


l utente interagisce solo con il _nodo master_ che conterrà il _Server API_. questo avvilente tramite manifest. 
l _API server_ prima valida il manifesto e poi lo memorizza in un database distribuito nel cluster detto _etcd_.
_etcd_ questo contiene 
- cluster confiugration
- object specification
- object statuses
- nodi sul cluster
- assegnamento oggetto-nodo 
![[IMG_0574.jpeg]]


lo _scheduler_ del master node determina dove l dovrebbe essere messo in esecuzione. questo
- chiede al API server quali oggetti non sono ancora stati assegnati alle macchine
- determina a quali macchine questi oggetti dovrebbero essere assegnati
- comunica al API Server lo stato degli assegnamenti 
![[IMG_0575.jpeg]]

il _Controller-Manager_ monitora lo stato del cluster tramite le API server
- ha il compito di controllare Se lo stato dichiarato coincide con lo stato del cluster
- lo fa facendo richieste al API server
![[IMG_0576.jpeg]]
#### WorkerNode

il _kublet_ è un componente del nodo worker che
- agisce come l agente del nodo e comunica al API Server re sapere se del workLoad è stato assegnato a quel worker
- è responsabile di avviare pod per far eseguirei quel workload 
quando un nodo inizialmente si aggiunge al _cluster_ kubelet comunica la sua esistenza al master node in modo che gli possa essere assegnato un workload
![[IMG_0577.jpeg]]

il _kube-Proxy_ permette ai container di comunicare tra di loro attraverso i vari nodi sul _cluster_
![[IMG_0578.jpeg]]


## Confronto con [[Container e Docker|docker]]
![[IMG_0579.jpeg]]


