---
type: nota
course: Intelligenza Artificiale
topic: 
tags: IA
---

Prev: [[Introduzione Intelligenza Artificiale (IIA)]]

# Agenti Intelligenti
---
a gente come ricerca della soluzione in una spazio di stati 

un agente percepisce l ambiente tramite _sensori_ e agisce su esso con degli _attuatori_
##### Agenti secondo AIMA
![[F69349A9-C2E7-4B42-8EFA-AB4AD09D99D0.jpeg]]
#### Caratteristiche  degli agenti 

- Gli agenti sono _situati_
	-  Ricevono percezioni da un ambiente
	- agiscono sull’ ambiente mediante azioni (attuatori)
- gli agenti hanno _abilita sociali_
	- Sono capacita di comunicare, collaborare , difendersi da altri agenti.
- Gli agenti hanno credenze, obiettivi, intenzioni 
- Gli agenti sogno _Embodied_: hanno un corpo, fino a considerare i meccanismi delle emozioni.


- Percezione: input da sensori 
- _Sequenza percettiva_: storia completa delle percezioni 
- la scelta delle azioni è funzioni unicamente della sequenza percettiva (ma non da qualcosa che non abbiamo percepito)
- _Funzione agente_: definisce l azione da compiere per ogni sequenza percettiva (descrive completamente l agente)
$$\text{sequenza percettiva}  \xrightarrow{f}   {\text{Azione}}$$
- Implementato da un _programma agente_
 il compito dello studio del IA sta nel progettare il programma agente
 

## Agenti Razionali 
Un agente razionale interagisce con il suo ambiente in maniera “efficace” ovvero fa la cosa “giusta”
-  Serve un criterio di valutazione oggettivo dell’effetto delle azioni dell’agente (della sequenza di stati dell’ambiente)

L architettura astratta di un agente è del tipo
![[Pasted image 20230211161120.png]]



- La razionalità è relativa a (dipende da): 
	-  la misura di prestazioni
	-  le conoscenze pregressa dell’ambiente 
	-  le percezioni presenti e passate (seq. percettiva) 
	-  le capacità dell’agente (azioni possibili) 
- _Agente razionale_: per ogni sequenza di percezioni compie l’azione che massimizza il valore atteso della misura delle prestazioni, considerando le sue percezioni passate e la sua conoscenza pregressa.
	- Riformulato massimizza il risultato con le informazione che possiede
	- Essere razionali significa non essere onnisciente e onnipotente. le azioni del  agente dipendono quindi solo da ciò che conosce e dalle sue capacita.
		- Per aumentare le conoscenze si possono fare azioni esplorative
	- L’agente razionale deve essere in grado di modificare il proprio comportamento con l’esperienza (le percezioni passate).
- _Agenti Autonomi_: un agente è autonomo nella misura in cui il suo comportamento dipende dalla sua capacità di ottenere esperienza (e non dall’aiuto del progettista)
	- Un agente il cui comportamento fosse determinato solo dalla sua conoscenza built-in (pregressa), sarebbe non autonomo e poco flessibile

## Struttura degli agenti
ogni agente si interafaccia con l [[Definizione di problemi per AI - Ambienti|Ambiente]] in cui vive e opera
è formato come
$$Agente = Architettura + Programma$$
![[F69349A9-C2E7-4B42-8EFA-AB4AD09D99D0.jpeg]]
$$Ag: P \rightarrow Az$$
dove $P$ sono le percezioni e $Az$ sono le azioni. il Programma del agente implementa la funzione $Ag$

##### Schema generale
```js
function Skeleton-Agent (percept) return action
//static: memory, the agent’s memory of the world 
memory = UpdateMemory(memory, percept)
action = Choose-Best-Action(memory) 
memory = UpdateMemory(memory, action) 
return action
```

##### Agenti reattivi semplici
![[Pasted image 20230211164922.png]]
```js
function Agente-Reattivo-Semplice (percezione)
returns azione
//persistent: regole, un insieme di regole 
condizione-azione (if-then) 
stato = Interpreta-Input(percezione) 
regola = Regola-Corrispondente(stato, regole) 
azione = regola.Azione 
return azione
```
##### Agenti basati su modello (con stato)
![[Pasted image 20230211165128.png]]
```js
function Agente-Basato-su-Modello (percezione) return azione
//persistent: stato, una descrizione dello stato corrente modello, conoscenza del mondo regole, un insieme di regole condizione-azione azione, l’azione più recente
stato = Aggiorna-Stato(stato, azione, percez., modello) 
regola = Regola-Corrispondente(stato, regole)
azione = regola.Azione
return azione
```
##### Agenti con obiettivo
![[Pasted image 20230211165212.png]]
- Sono _guidati_ da un obiettivo nella scelta dell’azione 
	- (è fornito un goal esplicito: e.g. Città da raggiungere) 
-  A volte l’azione migliore dipende da qual è l'obiettivo da raggiungere 
	- (es. da che parte devo girare?). 
-  Devono _pianificare_ una _sequenza di azioni_ per raggiungere l’obiettivo. 
-  Meno efficienti ma più flessibili di un agente reattivo
	-  (obiettivo può cambiare, non è già codificato nelle regole) 
##### Agenti con valutazione di utilità
![[Pasted image 20230211165311.png]]
- Obiettivi alternativi (o più modi per raggiungerlo) 
-  l’agente deve decidere verso quali di questi muoversi. 
-  necessaria una _funzione di utilità_ (che associa ad uno stato obiettivo un numero reale). 
-  Obiettivi più facilmente raggiungibili di altri 
- la funzione di utilità tiene conto anche della probabilità di successo (e/o di ciascun risultato): utilità attesa (o in media)

##### Agenti che apprendono
![[Pasted image 20230211165623.png]]
1. _Componente di apprendimento_ 
	- Produce cambiamenti al programma agente 
	- Migliora prestazioni , adattando i suoi componenti, apprendendo dall’ambiente
2.  _Elemento esecutivo_ (“Performance element”) 
	- Il programma agente (visto sinora per decider le azioni) 
3.  _Elemento critico_ 
	- Osserva e dà feedback sul comportamento basandosii su performance standard
4.  _Generatore di problemi_ 
	- Suggerisce nuove situazioni da esplorare


### Tipi di rappresentazioni
![[Pasted image 20230211165709.png]]
- Rappresentazione atomica (stati) 
- Rappresentazione fattorizzata (piu variabili e attributi) 
- Rappresentazione strutturata (aggiunge relazioni)