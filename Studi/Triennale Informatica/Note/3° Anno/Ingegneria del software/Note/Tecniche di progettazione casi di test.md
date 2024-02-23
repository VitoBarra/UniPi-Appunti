---
Subject: Ingegneria del software
topic: nota
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Tecniche di progettazione casi di test
---
progettazione dei casi di test per tecniche di [[Testing]]

i casi di test sono triple (input, output (_atteso_), ambiente)

### Adeguatezza dei casi di test
- un medo per definire l adeguatezza di un insieme di casi di test ( test suit)
- E’ impossibile: 
	- se il sistema supera un adeguato insieme di test allora deve essere corretto
	- l adeguatezza come è definita sopra è indecidibile

l adeguatezza si decide con certi criteri di adeguatezza.
1. nella specifica ho due casi, i casi di test non testano che i due casi siano trattati differentemente. 
2. nel codice ci sono n istruzioni 

_Test Obligation_: specifica descrizione di casi di test delle proprietà ritenute importanti per il testing 

i criteri di adeguatezza sono un insieme di test obligation.
un insieme di test soddisfa un criterio di adeguatezza se: 
1. tutti i test hanno successo
2. Ogni test obligation è soddisfatta da almeno un caso di test (nell’ insieme di casi di test scelto)

## Definizione test Obligations
1. dalla funzionalità (a scatola chiusa, _black box_), guardando la specifica del software
	- mirati a evidenziare malfunzionamento relativi a funzionalità.
	- [[Metodi Black Box per generare valori di input per testing]]
2. dalla struttura (a scatola aperta, _white box_) guardando il codice
	- Basati sulla conoscenza del codice
	- mirati a esercitare il codice indipendentemente dalla funzionalità  
	- [[Metodi white box per il testing]]
3. dal modello del programma
	- Modelli utilizzati nella specifica o nella progettazione o derivati del codice
4. da fault ipotetici
	- Cercano difetti ipotizzato (bug comuni)


## Fasi del testing 
1. Batterie di prove (Test suite)
## Procedure di prova 
- Procedure (automatiche e non ) per eseguire, registrare analizzare e valutare i risultati di una batteria di prova 
1. definizione del obiettivo della prova
2. Progettazione della prova
	- Scelta e definizione dei casi di prova (batterie di prove)
3. esecuzione della prova
	- l esecuzione può richiedere tempo
4. Analisi dei risultati
	- L esame dei risultati alla ricerca di d’evidenza di malfunzionamenti
5. Valutazione della prova


## Test Scaffolding (Impalcatura)
Codice che server per gestire i test e contengono 
1. _Driver di test_: sostituiscono il programma principale che richiama la funzionalità che vogliamo testare
2. _Stub_ : Sostituiscono le funzionalità chiamate dal test o utilizzate dal software in prova (_mock_)
3. _Test Harness_: sostituiscono parte del ambiente di distribuzione 
	- Tool per gestire l esecuzione del test
	- Tool per registrare i risultati 


	

	





