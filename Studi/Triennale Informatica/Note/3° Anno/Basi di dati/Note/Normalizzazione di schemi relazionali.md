---
type: nota
course: Data Base
topic: 
tags:
  - FDI
Parent MOC: "[[Data Base (DB)]]"
---

# Normalizzazione di schemi relazionali
---
lo [[Progettazione DB - Modello Relazionale|schema relazionale]] è semplice siccome si basa al concetto semplice di [[Relazioni tra insiemi|relazione tra insiemi]] ma per ogni relazione ci sono diverse rappresentazioni valide e quindi uno dei problemi e la _scelta_ di questa rappresentazione.
Per fare la corretta scelta si ricorre al processo di _normalizzazione degli schemi relazionali_ ovvero si trasforma una _rappresentazione esistente_ in una rappresentazione _equivalente_ ma in una forma detta _forma normale_.
una _forma normale_ è una forma che assicura le buone qualità di un [[Introduzione ai Data Base|Database]], dove la qualità è misurata con l assenze di _anomalie_


#### Anomalie
Le anomalie per un database sono definite come

_Ripetizione dell’informazione_: Ripetere piu volte la stessa informazione e problematico sia per spreco di  memoria e per l aggiornamento delle informazioni 
_Impossibilità di rappresentare certi fatti_
	Informazioni relative agli utenti della biblioteca possono essere memorizzate solo quando questi hanno un libro in prestito, non potendo lasciare l’attributo chiave NumeroLibro non specificata.

