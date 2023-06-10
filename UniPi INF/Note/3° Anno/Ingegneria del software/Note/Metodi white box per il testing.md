---
type: nota
course: Ingegneria del software
topic: 
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Metodi white box per il testing
---
Criteri per la generazione dei casi di test del [[Testing]].

questi metodi si basano sulla struttura del codice e vanno usati come supplemento ai [[Metodi Black Box per generare valori di input per testing|Metodi funzionali]] 

## Flusso di controllo
il test devono eseguire tutto il codice presente nel programma altrimenti non sono test adeguati.

per fare questa fase del testing s utilizzano i frati di flusso  che  definiscono la struttura del codice e come le varie parti sono collegate tra loro 
##### esempio
![[4BA97FD2-B6BB-49C4-883E-A265AA11766C.jpeg]]
per misurare l adeguante a dei controlli si utilizza la misura di copertura definita come
_Comandi_
$$\text{misura di copertura COMANDI} =\frac{\text{numero di comandi esercitati }}{\text{numero di comandi totali}}$$
si cerca l insieme minimale che compre il magistrale numero di comandi ma non sempre vale la pena cercare il _minimale_ per grafi molto complessi.
_Decision_ :
$$\text{misura di copertura DECISIONI} =\frac{\text{numero di archi esercitati }}{\text{numero di archi totali}}$$

_basic logic codition_:   
$$\text{misura di copertura Basic Condition}  =  \frac{\text{n.  valori assunti  basic condition }}{\text{2n. basic condition }}$$
_Multiple codition coverage_:
questo richiede di controllare $2^n$ condizioni ma sono riducibili con la [[Linguaggio formale| semantica del linguaggio]] 
- con lazy operation su i booleani
_Copertura dei cammini_:
copertura del numero di cammini.
questi in presenza di cicli potrebbero essere infiniti


## Fault based Testing 
basata sul ipotizzare difetti

### Test Mutazionale
data una batteria di test su cui abbiamo risultati corretti modifichiamo di poco il codice che stiamo testando generando cosi un codice _mutante_ e rilanciando il test possiamo fare delle osservazioni 
- se nessun test fallisce allora la nostra batteria di test non era abbastanza solida
- se solo il mutante viene ucciso ovvero almeno un test fallisce allora possiamo avere più fiducia che quella batteria di test sia corretta.

si possono classificare i mutanti: 
- _invalido_ : se non sintatticamente corretto _valido_ altrimenti
- _Utile_:  se _valido_ se ucciso da un sotto insieme di test
- _inutile_ : se ucciso sempre da tutti i test

I mutanti non vengono ucciso solo se: 
- il mutante rende il programma equivalente es. condizioni logiche equivalenti 
- la batteria di test è inadeguata


#### Obbiettivi 
- Favorire scoperta di malfunzionamenti ipotizzati
- valutare l efficacia dei casi di test
- cercare indicazioni sulla locazione dei difetti 