---
type: nota
course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: 
tags:
  - IA
---
# Machine Learning (ML)
---
il _machine learning_ (ML) in italiano Apprendimento automatico e' un sotto campo del [[AI - Concetti generali|inteligenza artificiale]] . questo è uno strumento utile  per l analisi dei dati, crea sistemi adattivi ed è uno strumento [[Statistica (STAT)|statistico]] 

gli obbiettivi sono
- come metodologia per l Ai
	- costruire sistemi adattivi 
- come strumenti statistici 
	- costruire strumenti Predittivi per l analisi dati
-  come metodologia per l informatica
	- trovare modelli sotto forma di strumenti per risolvere problemi interdisciplinari 
		- Biologia
		- medicina 
si utilizza un unico approccio per raggiungere tutti questi obiettivi



### Quando utile
l utilità del machine learning si ha in casi di 
- _nessuna o poca teoria_ del fenomeno che si vuole analizzare
- dati incerti, perturbati o incompleti 
- ambiente dinamico: non conosciuto a priori e necessita di adattamento personalizzato 
ma richiede:
- fonte di dati di training, con dei dati rappresentativi quindi di qualità
- tolleranza sulla precisione dei risultati


### Perché machine learning
- serve a trovare _soluzioni approssimate_ a problemi difficili che spesso sono difficili anche nella formulazione 
- Scrivere sistemi applicabili in più campi detti _sistemi intelligenti_
- è un _approccio rigoroso_ per trovare _[[Funzioni|funzioni approssimate]]_ per risolvere problemi complessi 

![[83EC07C1-95F8-4264-A425-289F6F5AC1E9.jpeg]]

## Learning supervisionato
un tipo di apprendimento che utilizza dei dati _Etichettati_ 
_dati_: dati di training detti _training example_ formalizzati  come $<input,output> = (x,d)$, sono delle associazioni per una funzione sconosciuta $f$ detta _target function_. con i training example se ne definiscono alcuni punti 
- le associazioni sono dati da un _teacher_ e sono prese per vere e utilizzate per stimare le funzione corretta
_Trova_: un approssimazione di $f$ detta _ipotesi_ che verrà poi utilizzata per predirei il valore dei nuovi dati non visti 


ci sono due tipi problemi risolvibili con questo tipo di apprendimento 
- _Clssificazione_: la funzione $f(x)$ restituisce la classe assunta corretta per $x$
	- $f(x)\in \mathbb{F}^k\times \mathbb{N}$. $f$ è quindi una funzione discreta, e ogni numero intero è una diversa classe 
- _Regressione_: la funzione $f(x)$ restituisce output reali approssimando la funzione reale _target_
- $f(x)$ $\in \mathbb{F}\times\mathbb{R}^k$
	 
![[991D6D4A-9F89-4A4E-BE65-509CB69C0C3C.jpeg]]

>[!example]- Alcuni esempi
>![[84563ACF-1E29-4871-81B7-628DCD565D04.jpeg]]


## Apprendimento non supervisionato
Si hanno _dati di training_ di cui non si sa il valore certo ma si vuole comunque aprossimate la funzione si fa quindi 
- _Clustering_
	- portizionare dati in cluster di _dati_ simili 
![[AB7569AC-30D1-4B10-A654-410A5DEDC98A.jpeg]]

_modello_: 
- obiettivo: catturare le relazioni tra dati, basandosi sul compito che si cerca di risolvere
- definisce la classe delle funzioni  che la macchina puo implementare sotto quel modello. detto _Hypotheses space_ (spazio delle ipotesi). 
	
>[!example]- 
> - [[Logica del primo ordine (FOL)|Logica del primo ordine]]
> - Equazioni numeriche
> - [[Definizione di Probabilita|Definizione di Probabilita]]

## Algoritmo di apprendimento 


- basato sui dati, compito da risolvere e modello
- _Learning_  [[AI - Algoritmi di ricerca informati|ricerca con euristiche]] nello spazio delle ipotesi $H$ della _migliore Ipotesi_ 
	- si cerca la migliore approssimazione per la funzione _sconosciuta_ 
	- Tipicamente impostata come la ricerca con il _minimo errore_
	- la _Miglir ipotesi_   si misura con l _Errore di generalizazione_ che misura quanto accurato il modello predice su dati _nuovi_  
- TIpicamente $H$ non coincide con l insieme di tutte le possibili funzioni, e la ricerca non puo essere esaustiva (sarebbe infinita): sono necessarie della assunzioni per ridurre lo spazio di ricerca, ti utlizza il _[[ML - Bias Induttivo|bias induttivo]]_
- ![[43BCF722-8E18-4052-B640-35712D4198B7.jpeg]]


### Generalizzazione 
la generalizzazione è il concetto principale del machine learning e si riferisce alla capacita di predire con basso errore i nuovi dati rispetto a quelli del _training set_
-  _Fase di aprendimento_ (trainin o fitting):  costruzione del modello dai dati conosciuti
- _fase si predizione_ (o stima): si danno nuovi dati al modello, si compara il risultato del modello con il risultato target 
questo ci da informazioni sul ipotesi predittiva e quindi sulle _capacita di generalizzare_

la performance del ML è definita come= _accuratezza predittiva_



