---
Course: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# Sistemi informativi
---
 ogni organizzazione per funzionare ha bisogno di informazione. 
 Le informazioni sono considerati risorse
 per gestire le informazioni ha bisogno di un _sistema informativo_ dove
 - _sistema_: si riferisce al fatto che ci sono piu parti che collaborano in coordinazione
 - _informativo_: si riferisce al fatto che ha a che fare con informazioni 
#### Sistema informativo (Definizione)
 Il _sistema informativo_ di un’organizzazione è una combinazione di risorse(umane e materiali), e di procedure organizzate per la _raccolta_, _l’archiviazione_, _l’elaborazione_ e lo _scambio_ delle _informazioni_ necessarie alle attività, queste possono essere di vario tipo 
- _informazioni di servizio_: operative 
- _informazioni di gestione_: di programmazione e controllo
- _informazioni di governo_: di pianificazione strategica 
![[IMG_1029.jpeg]]

#### Sistema Informatico
un sistema informatico è un _sistema informativo automatizzato_ ovvero la il sotto insieme del _sistema informativo_ che è stato automatizzato

Il _sistema informatico_ è composto da:
- Il _software_ e l'_hardware_ di base.
- Una _[[Introduzione ai Data Base|base di dati]]_ che contiene una rappresentazione del patrimonio informativo dell'organizzazione.
- Uno _schema_ che descrive la struttura della _base di dati_, le operazioni per agire su di essa e le restrizioni sui valori memorizzabili (_[[Modellazione della conoscenza|vincoli di integrità]]_).
- I _programmi applicativi_, che forniscono servizi agli utenti eseguendo operazioni sulla _base di dati_.
- La comunicazione, che consente l'accesso ai servizi del sistema informatico da parte di utenti e programmi.

![[IMG_1024.jpeg]]

#### Tipologia di Sistemi informatici 
Ci sono 2 tipologie di _sistemi informatici_ e queste due sono fatti per scopi e usi molto diversi.
##### Sistema Informativo Operazionale: (OLTP)
Sono sistemi orientati al _operatività_, ovvero servono per la _gestione_ delle _operazioni ripetitive_ del azienda tramite le parti _applicative_.

Utilizzano [[Introduzione ai Data Base|database]] di tipo _On-Line transaction Processing_(_OLTP_) ovvero che con il supporto dei [[Database Managment System (DBMS)|DBMS]] si basano su [[DBMS - Gestione affidabilita e concorrenza|transazioni]]![[IMG_1025.jpeg]]
questo tipo di _database_ mantiene dati con struttura _fissa_ e hanno bisogno di essere aggiornati alla versione _corrente_ dei dati per garantire la corretta operabilità 
le operazioni sono semplici e _veloci_ coinvolgono _pochi dati_ e le operazioni 

##### Sistemi informativi direzionali : (OLAP)
sono sistemi _orientati_ al analisi dei dati per guidare le _decisioni_, servono a scoprire pattern o informazioni intrinseche ai dati in modo automatico grazie al utilizzo di tecniche di _[[Data Mining|Data mining]]_. 
Nelle analisi usano dati
- _Aggregati_ raramente interessa il dato singolo, più tosto interessa la [[Statistica descrittiva - Dati Numerici#Media (definizione)|media]], max, min 
- _multidimensionali_ per cogliere informazioni da più punti di vista 
- possono essere analizzati _diversi livelli di dettagli_

usano _[[Introduzione ai Data Base|database]]_ di tipo _On-Line Analysis Processing_(_OLAP_) e sono usati tramite le _WareHouse_. Questo tipo di 
![[IMG_1026.jpeg]]
Questo tipo di _database_  ha una struttura _fissa_ dei dati e utilizza dati _storici_ e _esterni_ e _aggregati_, siccome per scoprire trend non c è bisogno di dati _”attuali”_ 
sono database che _non sono aggiornati_ frequentemente   
le operazioni sono complesse e _lente_ e coinvolgono _molti_ dati _multidimensionali_ 

##### Confronto tra OLTP e OLAP  
![[IMG_1027.jpeg]]


#### Big data
_Big Data_ è un termine ampio, riferito a situazioni in cui l'approccio '_schema-first_' tipico di _DB_ o _DW_ risulta troppo restrittivo o troppo lento. Le tre V:
- Volume
- Varietà
- Velocità

I Big Data sono in genere associati a:
- Sistemi _NoSQL_
- [[Concetti generali del Machine Learning|Machine learning]]
- Approccio _Data Lake_