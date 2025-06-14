---
Course: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# DBMS - Macchina Fisica
---
La _Machina Fisica_ di un [[Architettura di un DBMS|architettura di un DBMS]] gestisce


### Macchina Fisica

#### Gestore della memoria permanente
Il _gestore della memoria permanente_ offre una visione di una basi di dati come un insieme di file di blocchi di caratteri (_[[Memoria Paginata|pagine fisiche]]_) di grandezza prefissata, compresa generalmente fra 1 e 8 Kbyte, che sono l’unita minima di trasferimento fra la _[[Architettura Von-Neumann|memoria permanente]]_ e quella _[[Architettura Von-Neumann|temporanea]]_.


è un _astrazione_ sulla _memoria permanente_ e fornisce a gli altri moduli un _servizio di accesso alla memoria_ che si occupa dalle diverse modalità di gestione dei [[File System|file]] dei [[Sistemi Operativi|sistemi operativi]].

I dati memorizzati nella memoria permanente sono 
- Quelli descritti nello _[[Progettazione DB - Progettazione Logica Relazionale|schema logico]]_
- Le [[Strutture Dati|strutture]] ausiliarie per agevolare gli accessi alla base di dati (_indici_)
- I dati di servizio necessari per il funzionamento del sistema.
 

#### Gestore buffer
Il _gestore del buffer_ gestisce uno _spazio della memoria temporanea_ destinato a contenere un insieme di _pagine fisiche_ trasferite dalla _memoria permanente_.

è un _astrazione_ sul _trasferimento_ dalla _memoria temporanea_ a quella _permanente_
Offre agli altri _moduli_ un servizio per l interazione con la _memoria permanente_ 
chi utilizza questo servizio vede la memoria come un _insieme di pagine_ in _memoria temporanea_
	una _pagina_ è una _struttura logica_ che rappresenta in _memoria temporanea_ una _pagina fisica_  


le operazioni vengono eseguite sui record nel _buffer_, quindi lo _stesso record_ può subire _piu operazioni_ prima che questo venga salvato in _memoria permanente_, Infatti il trasferimento da _buffer_ a _memoria permanente_ viene fatto solo quando è necessario _liberare il buffer_ o quando il protocollo per la [[DBMS - Gestione affidabilita e concorrenza|gestione dell’affidabilita]] lo richiede.
Per questo Il Buffer è una [[Cache|cache]] per i dati e quindi una delle problematiche è scegliere la _politica di rimpiazzamento_, Siccome conoscere la [[SQL - Data Manipulation Lenguage|Query]] significa conoscere anche il _pattern di accesso ai dati_ si possono fare scelte _più informate_ su quale politica applicare dipendenti dal l’operazione da eseguire. il che aumenta _molto l efficienza del operazione_.

Molto spesso si utilizza la politica __most recently used__ (MRU) siccome le pagine appena usate e' difficile che serviranno di nuovo subito

![[IMG_1069.jpeg]]



I _record_ all’interno delle _pagine_ sono memorizzati come _stringhe di caratteri_ con un prefisso contenente informazioni di servizio seguito dai valori dei campi.
Il _prefisso_ può contenere, ad esempio, 
- _marca_ per la cancellazione logica
- _lunghezza del record_
- _numero_ degli attributi 
- l’_identificatore_ interno del record,

Un record con una dimensione inferiore a quella di una pagina si memorizza tutto in una pagina.

Al inserimento di un _record_ in una _[[Modello dati - Modello Relazionale|relazione]]_ nel [[Introduzione ai Data Base|DB]], il sistema gli assegna un _identificatore_ detto _TID_ (Tuple Identifier), o _RID_ (Row Identifier),
Dalla creazione del _record_ alla sua eliminazione Il _TID_ associato al record __non cambia mai__ 
il _TID_ è il riferimento da usare nelle _strutture dati_ per indicare il _record_

il _TID_ ha varie implementazioni e cambia si cosa si memorizza sia la conseguente gestione di qui dati.

un implementazione del  _TID_ comune che garantisce che questo _non cambi_ è la seguente  

il _TID_ è una coppia  $(P, j)$, dove 
- $P$ è il _numero di pagina_ 
- $j$ è l _indice_ di un vettore memorizzato nella pagina detto _slot array_
	- lo _slot array_ contiene i riferimenti agli inizi dei vari record 
![[IMG_1067.jpeg]]

In caso di modifica della lunghezza del _record_ se questo  non entra piu nello _spazio assegnatogli_ _va sposto_ e quindi si opera a seconda di due casi dipendenza dallo spazio libero _sulla pagina_ 
- _c è abbastanza spazio_: viene _spostato_ al interno della _stessa pagina_ in cui era originariamente e si aggiorna il valore dello _slot array_ nella cella $j$  con il nuovo indirizzo del inizio del record e non si cambia _TID_
- _NON c è abbastanza spazio_: si sposta il _record_ in un’altra pagina _senza_ cambiare il _TID_ che lo identifica. Al posto del _record_  viene scritta la coppia $(P’, j’)$ (ovvero un altro _TID_), dove 
	- $P’$ è l’indirizzo della _nuova pagina_ dove è stato scritto il record 
	- $j’$ è l _indice_ nello _slot array_  in $P’$
nel caso in cui un record venga spostato in un _altra pagina_ se successivamente all accesso del _record_ ci si accorge che in $P$ c è sufficiente _spazio libero_ per contenerlo, _allora_ viene spostato nella pagina originaria 


#### Gestore delle strutture di memorizzazione
Il _gestore delle strutture di memorizzazione_  _astrae_ dalle _strutture fisiche_ usate per la loro memorizzazione in _memoria permanente_.
Offre _agli altri moduli_ del sistema una visione dei dati permanenti organizzati in _collezioni di record e indici_

questo livello si occupa di
- come _individuare la pagina_ in cui inserire un nuovo record quando questo viene aggiunto alla collezione;
- come gestire le situazioni in cui una sequenza di cancellazioni o di inserimenti rendono una pagina _troppo vuota_ o _troppo piena_;
- quali _strutture ausiliarie_ prevedere per facilitare l’esecuzione delle ricerche. 

per fare ciò si usano particolari _organizzazione dei dati_ e un insieme di _algoritmi_ per gestire le operazioni su una _collezione di record_ 

###### Organizzazione seriale 
nel _organizzazione seriale_ (_heap_) i record di una collazione vengono memorizzati consecutivamente nell’_ordine_ in cui vengono _inseriti_.

Le _prestazioni_ delle _operazioni_ su record sono  
- _Inserzioni_:  __Veloce__ non ci sono strutture da mantenere 
- _Ricerca_ (valore di una chiave o di piccoli sottoinsiemi di record):  __Lente__ se i dati in cui cercare sono molti.
è adatto per _piccole collezioni_ o quando si opera su _grandi sottoinsiemi di record_.

è un organizzazione molto semplice di solita scelta di default se non se ne specificano altre


###### Organizzazione Sequenziale 
Nel _organizzazione seriale_  i record di una collezione sono memorizzati _consecutivamente_ nell’_ordine dei valori_ di un sotto insieme degli attributi $A_1, \dots , A_n$, 


Le _prestazioni_ delle _operazioni_ su record sono  
- _Inserzioni_: __Veloce__ ma si perdo l ordinamento
	- l ordinamento puo essere ripristinato ma solitamente non si usa quando si fa spesso l operazione di inserzione
- _Ricerca_: __Veloce__ se la ricerca e sugli attributi $A_1,\dots A_n$
	- _Numero di accessi_: gli elementi sono ordinati quindi si può fare la [[Ricerca Binaria|ricerca binaria]] e in più si deve leggere il _record_ trovato quindi:  $\log_2 b+1$ con $b$ il numero di blocchi

i _[[Database Managment System (DBMS)|DBMS]]_ che la prevedono richiedono di usarla per _collezioni statiche_ e dopo _aver caricato tutti i dati_, cosi da poter gestire l ordinamento. 


###### Organizzazione procedurale statico
L’_organizzazione procedurale_, o [[Hash Table|hash]], si utilizza un funzione hash per _trasformare la [[Modello Relazionale - Chiavi|chiave]]_ e ottenere l’indirizzo della _pagina in cui memorizzare_, Le collisioni sono gestite con delle [[Lista linkata|Liste linkate]] e c è un area del file designato a contenere i _record_ che traboccano 

![[IMG_1070.jpeg]]


Le _prestazioni_ delle _operazioni_ su record sono  
- _Inserzioni_: __Veloce__ con gestione di _collisioni_
- _Ricerca_: 
	- __Veloce__ per uguaglianza su chiave (ricerca puntuale) 
	- __Lenta__ su _intervalli_ di valori
	- __Lenta__ per ricerche su attributi non [[Modello Relazionale - Chiavi|chiave]]


>[!warning] gibberish della prof 
>
>
>il file (Collezione di pagine fisiche)  può prevedere un numero di blocchi(pagine fisiche) $B=\lceil d\rceil$ con  $d=\frac{N}{Mc}$
$d$ è la Frazione dello spazio fisico disponibile mediamente utilizzata, dove 
>- $N$ è il numero di record previsto per il file 
>- $M$ il fattore di pagine 
>- $c$ il _fattore di caricamento_

è un organizzazione _statica_ quindi funziona solo con _pagine_ che non cambiano

Trade-off da considerare:
 - Se il _numero di blocchi_ è troppo piccolo rispetto al Database si hanno frequenti collisioni (con catene di overflow, etc). 
 - Se il _numero di blocchi_ è troppo grande rispetto al Database si ha un fattore di riempimento dei blocchi molto basso.

###### Organizzazione ad albero
L’_organizzazione ad albero_ di una collezione $C$ sulla chiave $A$ prevede l’utilizzo di una [[Strutture Dati|struttura dati]] in _memoria permanente_ 

si usa un [[Bplus-Tree|B+-albero]] che ha le seguenti caratteristiche:
1. Permette di trovare il record con un valore della chiave $A$, se esiste, con pochi accessi alla memoria permanente.
2. Mantiene la collezione $C$ ordinata sulla chiave $A$.


Le _prestazioni_ delle _operazioni_ su record sono  
- _Inserzioni_: __Lenta__ va mantenuta la struttura del _B+-albero_
- _Ricerca_: 
	- __Veloce__: per ricerche del tipo $A \leq k, A \geq k,  k_1 \leq A \leq k_2$.
	- __più lenta__, rispetto la _procedurale_ per ricerche del tipo $A=k$ 
Questa organizzazione è la più __complessa__ 

###### Indici
l _organizzazione dei dati con indici_ Un indice su un attributo $A$ di una relazione $R$ e una [[Strutture Dati|struttura dati]] con le seguenti proprietà


_Definizione indice_:
Un indice $I$ su un attributo $A$ di una relazione $R$,  è una _[[Relazioni tra insiemi|relazione]] ordinata_ con due attributi $I(A, TID)$, con gli elementi ordinati su $A$ e valori $(A := a_i , TID := r_j)$, dove 
- $a_i$ è un _valore_ di $A$ presente in un _record_ di $R$
- $r_j$ è un _riferimento_ (_TID_) al record di $R$ in cui $A$ vale $a_i$  
Se $A$ non è una [[Modello Relazionale - Chiavi|chiave]], nell’indice sono presenti tanti record con lo stesso valore $a_i$ di $A$ quanti sono i record di $R$ in cui $A$ vale $a_i$


Un _indice_ è _organizzato_ a [[Bplus-Tree|B+- albero]] per permettere di trovare con _pochi accessi_, a partire da un valore $v$, i record di $R$ in cui il valore di $A$ e in una relazione specificata con $v$.


Un _indice_ può anche essere definito su di un insieme $A_1,\dots , A_n$ di attributi. In questo caso, l’indice contiene un record per ogni _combinazione_ di valori assunti dagli attributi $A_1,\dots, A_n$ nella relazione, e può essere utilizzato per rispondere in modo efficiente ad interrogazioni che specifichino un valore per ciascuno di questi attributi.


Possiamo distinguere: 
- __INDICE PRIMARIO__: in questo caso la _chiave di ordinamento_ del file sequenziale coincide con la chiave di _ricerca dell’indice_.  
	- Il _primo campo_ è dello stesso tipo del campo chiave di ordinamento (_Chiave primaria_) 
	- Il _secondo campo_ è un puntatore a un blocco del disco 
	- Esiste un record nel file dell’indice per ogni blocco nel file di dati
- __INDICE SECONDARIO__: in questo caso invece la chiave di ordinamento del file e la chiave di ricerca sono diverse.
	- Il primo campo è dello stesso tipo del campo che non viene usato per ordinare il file ed è chiamato campo di indicizzazione 
	- Il secondo campo è un puntatore al blocco oppure un puntatore al record (RID)



Le _prestazioni_ delle _operazioni_ su record sono  
- _Inserzioni_: __Lenta__ va mantenuta la struttura del _B+-albero_
- _Ricerca_: 
	- __Veloce__: per ricerche del tipo $A \leq k, A \geq k,  k_1 \leq A \leq k_2$ (dal fatto di usare un B+-tree)
	- __Veloce__: in caso di indice su insiemi di attributi e ricerca su quei specifici insiemi 
Questa organizzazione è __complessa__ 



##### Organizzazioni statiche e dinamiche
la _gestione_ delle situazioni in cui una pagina diventa _troppo vuota_ o _troppo piena_ si classifica in due categorie
- __statica__: una volta _dimensionata_ per una certa _quantità di dati_, non si riconfigura automaticamente se i dati memorizzati aumentano
	- _Degrado_ delle prestazioni se i dati sono più del programmato, questo si risolve con __riorganizzazione__.  
- __Dinamica__: è in grado di _adeguarsi_ alla quantità di dati _memorizzati_, preservando le prestazioni senza bisogno di __riorganizzazioni__.



#### Gestione dei metodi di accesso
Il _gestore dei metodi di accesso_  _astrae_  l organizazione fisica dei _record_ 
_Offre_
- operatori per _costruire/eliminare_, collezioni di record o indici 
- operatori per recuperare i record uno dopo l’altro nell’ordine in cui sono memorizzati, oppure attraverso indici.
