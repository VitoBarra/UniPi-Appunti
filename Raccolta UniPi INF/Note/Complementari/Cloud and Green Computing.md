# Cloud and Green Computing

# Introduzione

- Cos’è un container
- Cos’è un microservice
- Conoscere modelli di servizio del cloud
- AWS amazon web services

---

<aside>
❓ Cos’è cloud e green computing?

</aside>

### What:

- *IaaS*
- *Paas*
- *FaaS*
- *Containers*
- *Microservices*
- *Datacenters*
- *Cloud-IoT continuum (cloud continuo)*
- Green computing *101*
- Business models

cgc21-22! psw corso

---

## Servizi come beni

L’economia mondiale ha subito un trend di conversione dei beni in servizi. Va a mancare in sostanza la proprietà dell’oggetto che si utilizza, magari per un prezzo più accomodante.

---

## Contratto per servizio

I consumatori non hanno (né vogliono avere) idea di com’è realmente implementato il servizio che viene utilizzato.

I consumatori scelgono (dovrebbero scegliere) quale servizio usare o no in base al *contratto* che dovrebbe essere mostrato, da parte del provider.

<aside>
❓ Ma i consumatori leggono effettivamente i contratti?

</aside>

---

# SLA

L’SLA (service level agreement) rappresenta uno statement legale prodotto dalla compagnia per descrivere le conseguenze di un down del proprio servizio.
Si valuta quindi l’affidabilità del servizio

Vengono riportati tre tipi di SLA come esempio:

1. L’SLA di S3 Amazon:da nessuna parte è riportato che abbiampo un qualche tipo di garanziao indicie di affidabilità,
c’è soltanto la spiegazione su quanto “credito” l’utente può ricevere se si dovessero verificare dei disservizi. Leggendo attentamente le clausole si arriva alla conclusione che un eventuale rimborso `e quasi impossibile da ricevere (”InternalError”, ”ServiceUnavaible” avete ottenuto? quando?)
2. L’SLA di Microsoft Cloud:non garantisce neanche che il Cloud sia sicuro, anzi ci invita a fare regolarmente un backup
dei nostri dati del Cloud su un’altra piattaforma
3. L’SLA Facebook:avverte che qualsiasi contenuto condiviso pubblicamente puo essere utilizzato da Facebook o es- `
sere ceduto a terzi in tutto il mondo che possono utilizzarlo a loro volta per qualsiasi scopo

# ESD

Prima del cloud si avevano due scelte in caso di Estimated Service Demand: overprovisioning (waste of resources) o underprovisioning (customer rejecting)

Ora grazie al cloud il customer ha l’erronea opinione di avere un’infinita quantità di risorse hardware per supportare le proprie necessità.

### Definizione di Cloud Computing di NIST (National Institute of Standards and Technology)

> Cloud computing is a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g. networks, servers, storage, applications and services) that can be rapidly be provisioned and released with minimal management effort or service provider interaction.
>

(Trad) “Il cloud computing è un modello per permettere un accesso tramite network ad un pool di risorse computabili e configurabili, in modo onnipresente e conveniente. Esso può essere rapidamente distruibuito e rilasciato con minimo sforzo di gestione o di interazione con il gestore.

[[Raccolta UniPi INF/Note/Complementari/Cloud and Green Computing/Untitled.png]]

**Idee chiave:**

- Ragruppamento efficiente di infrastrutture virtuali on-demand autogestite, consumate come servizi
- Distribuire risorse virtualizzate, scalabili dinamicamente tramite internet a più clienti

[[Raccolta UniPi INF/Note/Complementari/Cloud and Green Computing/Untitled 1.png]]

**Economics**

- Eliminazione del costo di acquisto di nuovi asset a lungo termine, eliminando la necessità di pre-attenzione da parte degli utilizzatori di cloud computing resources
- Pay-Per-Use
    - I clienti lo adorano!
    - Anche se più costoso a lungo andare, il costo sarà surclassato dai benefici economici dell’elasticità e di trasferimento del rischio.

[[Raccolta UniPi INF/Note/Complementari/Cloud and Green Computing/Untitled 2.png]]

# Gli intralci alla cloud adoption

### Confidenzialità dei dati:

- Dove saranno conservati i nostri dati, concretamente?
- La privacy e l’integrità dei dati sarà garantita? Come?
- Come possiamo accorgerci di un guasto in corso?

### Continuità del servizio:

- Che succede se il provider del cloud fallisce?
- Mantra dell’informatica “No single point of failure”

### Vendor lock-in?

---

# Nuovi modelli di Business

> *“Se avessi chiesto alle persone che cosa volevano, mi avrebbero risposto ‘Cavalli più veloci!”*                                                                                                         *-Henry Ford*
>

L’innovazione delle enterprises è scaturito dalla capacità di vedere i problemi da un punto di vista differente, che ha poi permesso di sviluppare business models completi e redditizi:

[[Raccolta UniPi INF/Note/Complementari/Cloud and Green Computing/Untitled 3.png]]

---

# **IaaS**

---

# **Containers**

### Introduzione: Docker

Docker è una piattaforma che permette di eseguire applicazioni in ambiente isolato. Permette anche di sviluppare ed eseguire applicazioni sfruttando i **container.**

[[Raccolta UniPi INF/Note/Complementari/Cloud and Green Computing/Untitled 4.png]]

## La metafora spieata in breve:

[[Raccolta UniPi INF/Note/Complementari/Cloud and Green Computing/Untitled 5.png]]

## Macchine virtuali

Le applicazioni vengono eseguite su Macchine virtuali, diverse applicazioni possono essere conservate sullo stesso server fisico.

Ogni VM ha bisogno di:

- Allocazione di Risorse (CPU, Memoria, Archiviazione)
- Installazione di un SIstema Operativo Guest

## Container

Il kernel dei sistemi operativi permette l’esistenza di istanze spazio-utente isolate. Queste istanze sono chiamate **containers.**

## VM vs. Containers

[[Raccolta UniPi INF/Note/Complementari/Cloud and Green Computing/Untitled 6.png]]

Comparate alle macchine virtuali i containers sono:

- Più leggeri
- Più veloci nell’avvio
- Più semplici per lo sviluppo
- Meno sicuri (meno isolamento rispetto alle macchine virtuali)



## Quanti anni hanno i container?

Per decenni, il comando UNIX chroot ha fornito una forma semplice di isolamento di filesystem:

- 1998 - FreeBSD jail utility ha esteso il sandboxing (isolamento) ai processi
- 2005 - Google cominciava a sviluppare *CGroups* per il kernel Linux e comincia a trasferire la propria infrastruttura ai containers
- 2008 - I Linux Containers (LXC) forniscono una soluzione containeristica completa
- 2013 - Docker aggiunse i pezzi mancati - immagini portatili e UI amichevole - al puzzle della containerizzazzione, e i container entrano nel mainstream

    La piattaforma docker consisteva in:

    - Docker Engine (creazione e esecuzione di containers)
    - Docker Hub (per distribuire said containers)

## Docker

Docker sfrutta la virtualizzazione container-based per eseguire istanze guest isolate sullo (stesso) OS. I componenti del software sono impacchettati in **“Immagini”,** che sono sfruttate come template read-only per creare ed eseguire **Containers**.

Volumi esterni possono essere montati per assicurare la persistenza dei dati.

*“Build, ship, and run any app anywhere”*

## Immagini Docker

- (read-only) template usati per creare containers
- Archiviati in un Docker **registry** (privato o pubblico):
    - Il registry è strutturato in forma di repositories
    - Ogni repository contiene un set di Immagini, per versioni differenti del software
    - Le immagini sono identificate da una coppia **repository:tag**
    - [Docker Hub](https://hub.docker.com/)


Il meccanismo di docker è utile grazie alla stratificazione, poiché ogni strato può essere un immagine assestante
Per esempio:

[[Raccolta UniPi INF/Note/Complementari/Cloud and Green Computing/Untitled 7.png]]

[[Raccolta UniPi INF/Note/Complementari/Cloud and Green Computing/Untitled 8.png]]

# Docker Compose:

[[Raccolta UniPi INF/Note/Complementari/Cloud and Green Computing/Untitled 9.png]]

## RIGUARDARE SWARM MODE DOCKER!

---

# PaaS

PaaS amplia i servizi offerti da parte dello IaaS offrono
