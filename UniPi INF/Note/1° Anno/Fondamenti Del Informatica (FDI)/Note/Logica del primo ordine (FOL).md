---
type: nota
course: Fondamenti Di Informatica
topic: 
tags: FDI
---

Prev: [[Fondamenti Del Informatica (FDI)]]

# Logica del primo Ordine
---
è una logica che estende la [[Logica proposizionale|Logica proposizionale]] permettendo di lavorare con oggetti piu complessi dei semplici valori di verità  

## Sintassi

### Quantificatori
- _Per ogni_ denotato con $\forall x$
- _Esiste_ denotato con $\exists x$ 


### Scope e Ferme legate

Definizione:
- Formula _Chiusa_: se tutte le occorrenze sono legate
- Formula  _Aperta_: se anche una solo occorrenza _NON_ è legata
- formula _ground_: se non contiene variabili 







## Semantica
ci interessa definire il significato delle formule _chiuse_ e _ground_ siccome nel caso delle formule aperte va specificato il valore delle variabili prima di poter dare una valutazione sensata, specificare il valore di una variabile porta la formula ad essere _chiusa_ o _ground_

### Concettualizzazione
una concettualizzazione una descrizione del mondo con ciò che è rilevante per la risoluzione del problema che ci interessa. per definirla ci servono 3 elementi 
- _Dominio_:  dove si descrivono gli oggetti 
- _Funzioni_: dove si descrivono delle proprieta degli oggetti
- _Relazioni_: dove si descrivono le relazioni tra oggetti

Le _Concettualizzazioni_ possibili sono infinite: sta a chi fa il design del agente di scegliere il giusto livello di astrazione 

### Interpretazione
un Interpretazione $I$ stabilisce una corrispondenza precisa tra elementi atomici del linguaggio ed elementi della [[#Concettualizzazione|concettualizzazione]].
$I$ interpreta:
- I simboli di costante come elementi del dominio $D$
- I simboli di funzione come funzioni da $n-$uple di $D$ in $D$
- i simboli di predicato come insieme di $n-$uple ([[Relazioni]])

#### Semantica ($\forall$)
- $\forall x.A(x)$ è _vera_ se lo è per ciascun elemento del dominio $A$
	- Se il dominio  è finito equivale ad una concatenazione di $\land$ (AND)
- Tipicamente usata con $\implies$
	- $\forall x P_1(x) \implies P_2(x)$
	- usato quindi per restringere il campo del dominio ai soli oggetti che soddisfano il primo predicato
	
#### Semantica ($\exists$)
- $\exists x.A(x)$ è _vera_ se lo è per almeno un elemento del domino $A$
	- Se il dominio è finito equivale ad una concatenazione di $\lor$ (OR)
- Tipicamente usato con $\land$ (and)
	- $\exists x . P_1(x) \land P_2(x)$
		- Esiste un oggetto che soddisfa entrambi le proprieta
	- $\exists x . P_1(x) \implies P_2(x)$
		- forma molto debole potrebbe è una formula _vera_ anche se non esiste nessun elemento che soddisfi $P_1$ 

##### Relazione tra $\forall$ e $\exists$
- $\forall x. \lnot P(x) \equiv \lnot \exists x . P(x)$
- $\lnot \forall x. P(x) \equiv \exists x . \lnot P(x)$
- $\forall x. P(x) \equiv \lnot \exists x . \lnot P(x)$
- $\lnot \forall x. \lnot P(x) \equiv \exists x . P(x)$


#### Semantica composizionale
la semantica del intera formula dipende direttamente dalla semantica dei sui componenti 