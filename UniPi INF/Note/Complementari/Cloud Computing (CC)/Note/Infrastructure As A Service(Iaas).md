---
type: nota
course: Cloud Computing
topic: [[]]
tags: CC
---

Prev: [[Cloud Computing (CC)]]

# Infrastructure As A Service(Iaas)
---

## Server Virtualization & hypervisors

- _Definition of virtualization_
	- è un layer di astrazione 
	- OS non è più legato al server/pc su cui gira
	- l [[Sistemi Operativi|OS]] è astratto dal hardwere e non è installato direttamente sulla macchina
- _Server Virtualization_ 
	- Layer di virtualizzazione tra il server fisico e l OS che normalmente sarebbe installato
	- Virtual machine: dove installi effettivamente l OS e le App
- _Definiton of Hypervisor_:
	- Crea il layer di virtualizzazione 
	- Contiene il _Virtual machine manager_
- _Tipi di Hypervisor_
	- _type 1_: carica direttamente sul hardware
		- meno overhead
		- Usato nei _Data center_
		- alto _rapporto di consolidamento_
			- ovvero numero di machine virtuali che riusciamo a gestire nello stesso server
	- _type 2_: carica in un sistema operativo installato sul hardware
		- più overhead
		- usato per macchine desktop 
		- più basso  _rapporto di consolidamento_
			- il sistema operativo originale gia occupa una parte dello spazio limitando la capacita utilizzabile dal _Hypervisor_
		- utile quando l Hypervisor non è l unica applicazione su una macchina 
 ![[IMG_0516.jpeg]]

### Amazon Elastic Computer Cloud (EC2)


### Amazon Simple Storage Service (S3)


### Amazon Elastic Block Store (EBS)



### AWS identity and access Management IAM
per la gestione dei ruoli e dei permessi 
- _identity_: si intende la capacita di capire se l utente che sta facendo l accesso è quello specifico utente
- _access_: si riferisce ai permessi che ha quel utente. (es accesso di scrittura lettura ec)  
