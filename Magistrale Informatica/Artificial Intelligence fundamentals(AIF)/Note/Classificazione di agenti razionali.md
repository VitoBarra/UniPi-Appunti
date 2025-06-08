---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
Course 2: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
tags:
  - AIF
  - IA
Area: 
topic: 
SubTopic: 
---

# Classificazione di agenti
---

Alcuni tipo di [[agenti razionali|agenti razionali]] 
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
![[IMG - agenti basati su modello.png]]
```js
function Agente-Basato-su-Modello (percezione) return azione
//persistent: stato, una descrizione dello stato corrente modello, conoscenza del mondo regole, un insieme di regole condizione-azione azione, l’azione più recente
stato = Aggiorna-Stato(stato, azione, percez., modello) 
regola = Regola-Corrispondente(stato, regole)
azione = regola.Azione
return azione
```
##### Agenti con obiettivo
![[IMG - agenti con obiettivi.png]]
- Sono _guidati_ da un obiettivo nella scelta dell’azione 
	- (è fornito un goal esplicito: e.g. Città da raggiungere) 
-  A volte l’azione migliore dipende da qual è l'obiettivo da raggiungere 
	- (es. da che parte devo girare?). 
-  Devono _pianificare_ una _sequenza di azioni_ per raggiungere l’obiettivo. 
-  Meno efficienti ma più flessibili di un agente reattivo
	-  (obiettivo può cambiare, non è già codificato nelle regole) 
##### Agenti con valutazione di utilità
![[IMG - agenti con valutazione di utilita.png]]
- Obiettivi alternativi (o più modi per raggiungerlo) 
-  l’agente deve decidere verso quali di questi muoversi. 
-  necessaria una _funzione di utilità_ (che associa ad uno stato obiettivo un numero reale). 
-  Obiettivi più facilmente raggiungibili di altri 
- la funzione di utilità tiene conto anche della probabilità di successo (e/o di ciascun risultato): utilità attesa (o in media)

##### Agenti che apprendono
![[IMG - architettura agente che aprende.png]]
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
![[IMG - tipi di rappresentazione degli aggenti.png]]
- Rappresentazione atomica (stati) 
- Rappresentazione fattorizzata (piu variabili e attributi) 
- Rappresentazione strutturata (aggiunge relazioni)