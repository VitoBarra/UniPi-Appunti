---
Course: "[[Ingegneria Del Software (IS)]]"
topic: nota
tags:
  - IS
---
# Principi di progettazione e qualità di un progetto
---
## Principi e pattern di programmazione 


### Principi generali
1. Information Hiding:
	1. Controllo delle interfacce
2. Astrazione 
	1. Dati e controllo
3. Coesione 
4. Disaccoppiamento

Sommati in [[Principi SOLID|SOLID]] e [[Principi GRASP|GRASP]]


## Information Hiding
consiste nel nascondere ad utilizzatore di un oggetto le strutture  dati e gli algoritmi usati dal oggetti lasciando pubblica solo un interfaccia che rappresenta i metodi invocabili su quel oggetto.


>[!warning]  Incapsulamento VS information Hiding
>differisce dal incapsulamento  (che è una proprietà del linguaggio ) siccome questo racchiude le proprietà in un singolo oggetto ma non necessariamente le nascondo, ad esempio le variabili possono essere publiche  
### Realizzazione del Principio 
la realizzazione è spesso facile, basta rendere gli attributi che si vogliono nascondere privati. e eventualmente rendere accessibili dei dati passando per metodi _accessors_ e _mutators_ detti: 
- _get()_: non deve cambiare lo stato del oggetto e restituire se possibile un clone dei dati non un riferimento 
- _set()_: permette una modifica controllata delle proprietà di un oggetto.


#### Pro
1. _Comprensibilità_ : non serve conoscere l implementazione specifica di un unita per usarla 2
2. _Manutenibilità_: si può cambiare l implementazione di una unita senza dover modificare le altre
3. _Lavoro in team_ : le separazione corpo-interfaccia facilita lo sviluppo da parte di persone che lavorano in modo indipendente, il riuso, le riparazione e le riconfigurazioni
4. _Sicurezza_: I dati di un unita possono essere modificato solo da funzioni interne alla stessa e non dall’ esterno.

## Coesione
- Proprietà di una unità di realizzazione (o sottosistema)
	- grado in cui una unità realizza “_uno e un solo concetto_”
	- funzionalità “vicine” devono stare nella stessa unità 
		- vicinanza per tipo, algoritmi, dati in ingresso e in uscita


### Tipi di Coesione 
####  Funzionale:
raggruppa parti che collaborano per realizzare una funzionalità 
- È la situazione ideale.
#### Comunicativa: 
tra elementi che operano sugli stessi dati di input o contribuiscono agli stessi dati di output. 
- Esempio: aggiornare il record nel database e inviarlo alla stampante. 
- Non è un buon modo di raggruppare, non supporta il riuso
#### Procedurale:
tra elementi che realizzano i passi di una procedura. 
- Esempio: calcolala media di uno studente, stampa la media di uno studente 
- Le azioni sono debolmente connesse e difficilmente riutilizzabili.
#### Temporale
tra azioni che devono essere fatte in uno stesso arco di tempo 
- Esempio: azioni da fare all’apertura dell’anno accademico
- Le azioni sono debolmente connesse e difficilmente riutilizzabili. 
- Soluzione preferibile: dividere le azioni in diverse unità, avere una routine che manda a tutte loro un evento di avvio 
#### Logica
tra elementi che sono logicamente correlati e non funzionalmente. 
- Esempio: un componente legge input da nastro, disco e rete. Le operazioni sono correlate, ma le funzioni sono significativamente diverse. 
- Le operazioni sono debolmente connesse e difficilmente riutilizzabili. 
#### Accidentale:
- tra elementi non correlati ma piazzati assieme 
- È la peggiore forma di coesione.

## Disaccoppiamento 
Proprietà di un insieme di unità di progettazione(in generale di una architettura) 
- grado in cui un'unità di progettazione è  “legata” ad altre unità di progettazione
- Dipendenze, scambio di messaggi…
![[531571FC-7869-4540-BF31-1A0E0345C8C8.jpeg]]
un buon sistema ha basso accoppiamento. 


#### Vantaggi:
un sistema con altro grado di coesione e basso grado di accoppiamento permette
- maggiore riuso e migliore manutenibilità 
- ridotta interazione fra (sotto) sistemi
- garantire un altro grado di coesione normalmente riduce il grado di accoppiamento. 
