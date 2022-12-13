---
type: nota
course: Ingegneria del software
topic: 
tags: IS
---

Prev: [[Ingegneria Del Software (IS)]]

# Metodi Black Box per generare valori di input per testing
---
metodi per il [[testing]] 
si inizia
1. Separando le funzionalita da testare
2. Derivando un insieme di casi di test per ogni funzionalita.
	- Ad esempio M(_p1_,_p2_,_p3_,_p4_) < <_i1_,_i2_,_i3_,_i4_>, output atteso, ambiente>


## Tecniche di scelta  degli input

### Metodo Statistico
- i casi di testi sono seleziona in base alla distribuzione di [[Probabilità e variabili aleatorie| Probabilita]] dei dati di ingresso del programma
	- Test progettato s i valori più probabili nel momento del utilizzo
		- non sempre rispecchia la realtà
	- nota la distribuzione si può automatizzare la creazione dei test
	- calcavate il valore attore preciso è oneroso (Problema del oracolo)
### partizione dei dati in cassi di equivalenza (categorie)
- Metodo in cui il dominio dei dati di ingresso è _ripartito_ in classi di _equivalenza_.  
	- due valori  d ingresso appartengono alla stessa classe di equivalenza se, in base ai requisiti, dovrebbero produrre lo stesso comportate del programma (non necessariamente stesso output)
- economicamente valido se il numero di possibili comportamenti è di molto inferiore alle possibili configurazioni di ingresso
	- i risultati dei test sono noti per a classe  
- questo criterio si basa sul assunzione non sempre vera che se un comportamento vale per certi input allora funziona per tutta la classe di equivalenza 
	- la correttezza di questa assunzione dipende dalla realizzazione del programma
##### Esempio
	![[9FBFD18C-F776-4C44-B8F4-AD45C5494241.jpeg]]
### Criterio dei valori limite (DI frontiera) 
- Metodo Basato sul individuare di valori estremi 
	-  Estremi delle classi di equivalenti definite in base alle uguaglianza del comportamento del programma
	- Estremi in base a considerare inerenti il tipo dei valori d ingresso 
	- molto utilizzato siccome i difetti spesso si celano nel intorno dei valori limite 
### Casi non validi 
- per ogni input si definiscono anche i casi non validi che devono generare un errore
### Metodo Random
- si generano input random e si testa con quelli
- difficile girare valori attesi
- non ripetibile 
- praticamente gratis 
- non testa i valori limiti

### Test su catalogo
- una lista di cose da testare basate sul esperienza di chi ha già fatto design dei test


## Test combinatorio
nei casi in cui vi valori di input sono più di uno si dovrebbe prevedere il [[Prodotto Cartesiano]] Dei valori di input e dalla [[Combinatoria]] sappiamo che i numeri di casi da testare diventano velocemente troppi per essere gestiti.
si ragiona sulle classi di equivalenza per calcolare il numero di casi da testare. 
#### Esempio
<i1,i2,i3>:
i1: 7 classi di cui 1 di errore
i2: 5 classi di cui 2 di errore 
i3: 6 classi di cui 3 di errore   
il numero delle combinazioni da testare sarebbe
$n:7*5*6$

si possono applicare tecniche per ridurre questo numero 
### Vincoli
##### Di errore
si sceglie un solo elemento per classe d errore
$n: 3 + 6*3*3$
> [!question] 
> si prende 1 per posizione o uno per classe di equivalenza???? chiedere prof
##### Di proprieta
si possono definire dei vincoli di proprietà che possono ridurre il numero di casi introducendo dipendenze tra i dati
i1:
	classe 1, classe 2, classe 4,classe 5 \[property 1\]
	classe 3, classe 6  \[property 2\]
	classe 7 \[errore\]
i2:
	classe 1,classe 2 \[Property 1\]
	classe 3	\[Property 1\]
	classe 4,classe 5 \[error\]

$n:3+(4*2+2*1) *3$

##### Singoletti
fissando alcuni parametri in questo caso i3  
$n:3+(4*2+2*1) *1$

#### VAnraggi della tecnicha dei vincoli
questa tecnica funziona bene se i vincoli sono veri vincoli del dominio. non funziona bene se li aggiungiamo al solo scopo di ridurre le combinazioni 

### PairWise testing 
si utilizza quando il dominio non fornisce vincoli interessanti per ridurre le combinazioni. si generano e testano solo le combinazioni di un numero $k$ di variabili tale che $k<n$ se $k=2$ si parla di PairWise.

##### Esempio
Prendendo i caso di prima invece di $n:7*4*5$ si ottiene
$n:7*4+7*5+4*5$ queste coppie si possono generare in modo piu efficiente 
![[6E10A608-67C7-43F8-924B-8E39D70B5E50.jpeg]]
la generazione delle copie non puo essere fatta a mano ma si possono usare delle euristiche. 


> [!question]
> non capita troppo la logica del perche questa tecnica funziona e la generazione efficente