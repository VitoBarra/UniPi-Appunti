---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Schema relazionali - Ricerca delle chiavi
---
#### Algoritmo di ricerca per tutte le chiavi
_Sia_ $R \langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]] 
Un [[Algoritmi|algoritmo]] per cercare tutte le [[Modello Relazionale - Chiavi|chiavi]] di $R$  si basa sulle seguenti osservazioni
1. _Se_ un attributo $A\in T$ non appare __MAI__ a _destra_ nelle _[[Schemi relazionali - Dipendenze funzionali|dipendenze]]_ in $F$
	- _allora_ appartiene a _tutte le chiave_ di $R$
2. _Se_ un attributo $A \in T$ _Appare_ a _destra_ ma __MAI__ a _sinistra_ nelle dipendenze in $F$
	- _allora_ non appartiene ad _nessuna chiave_ di $R$

da questi possiamo dire che 
_sia_ $X$ gli attributi che non appaiono a destra
_se_  $X^+=T$ dove $X^+$ è la [[Schema relazionali - Chiusura rispetto gli attributi|chiusura rispetto agli attributi]]
_allora_ (per osservazione 1) $X^+$ è _[[Modello Relazionale - Chiavi|chiave]]_ ed è l _unica possibile_ 
 
 _se_ $X^+ \not=T$ dove $X^+$ è la [[Schema relazionali - Chiusura rispetto gli attributi|chiusura rispetto agli attributi]] 
 _allora_ (per osservazione 2 ) per _trovare le chiavi_ bisogna aggiunge _uno alla volta_ a $X$ degli elementi di $W \in T$ che compaiono sia a _destra che a sinistra_ delle dipendenze, evitando 
 - Elemento già in $X^+$ che sarebbero ridondanti
 - Gli elementi che producono un insieme  $X'$ che contengono una chiave _precedentemente trovata_, perché  $X'$  diventata una _[[Modello Relazionale - Chiavi#Superchiave (Definizione)|superchiave]]_ ma non una _[[Modello Relazionale - Chiavi#Chiave (Definizione)|chiave]]_

E allora un _algoritmo_ che cerca tutte le possibili chiavi segue come
![[photo1703945663.jpeg]]
Funzioni
- _First_($list$) : restituisce il primo elemento della lista
- _rest_($list$): restituisce il resto della [[Matematica - liste |lista]] escludendo il primo
- $list_{1}$ _append_ $list_2$: mette in coda a $list_1$ gli elementi di $List_{2}$  

Questo algoritmo Memorizza in
- _chiavi_ : le chiavi trovate durante l iterazione
- _Candidati_: i possibili candidati da analizzare.
- _NoDes_: sono gli attributi che non appaino a destra
- _SinDes_: sono gli attributi che appaiono sia a sinistra che a destra

un _candidato_ è un _sottoinsieme_ di $T$ ed è definito con la forma $X::(Y)$ che rappresenta compattamente tutti gli insiemi formati dal unione di  $X$ e Tutte le _combinazioni_ degli elementi di $Y$   $$X::(Y)=\{X \cup_{i \in  I} Y_{i}\} \ \ \forall I\in  2^{n}$$
Inizialmente i _candidati_$=NoDes::(SinDes)$  

E i candidati $X::(Y)$ sono analizzati in ordine 
_Se_ $X^+=T$ 
_allora_ $X$ è _chiave_ e gli altri insiemi $X::(Y)$ sono _scartati_

_altrimenti_  essendo gli elemento di $X^+$ quelli raggiungibili da $X$ sappiamo che non potranno partecipare alle _[[Modello Relazionale - Chiavi#Chiave (Definizione)|chiavi]]_ che contengono $X$ altrimenti sarebbero _[[Modello Relazionale - Chiavi#Superchiave (Definizione)|superchiavi]]_  
_quindi_  _sia_ $Y-X^+=\{ A_{1},\dots,A_{n}\}$ 
si aggiungono a _candidati_ le liste $XA_{1}::(A_{2,\dots,A_{n}}),XA_{2}::(A_{3,\dots,A_{n}}),\dots ,XA_{n}::()$ e queste _coprono_ completamente $(X::(A_{1},\dots A_{n}))-\{ X \}$
 

Il _test_ $X^+=T$ assicura che $X$ è un _superchiave_ e per assicurarci che sia anche _chiave_ dobbiamo controllare che non siano presenti in $X$ altre chiavi.

Mentre le _chiavi gia trovate_ non potranno mai contenere le chiavi trovate successive e quindi non c è bisogno di ricontrollarle. Questo è vero siccome si estrae sempre il primo elemento di _candidati_ è candidati è una lista ordinata in modo _crescente_ sulla _lunghezza_ del elemento, e gli elementi avranno _sempre lunghezza maggiore o uguale_ a quella del ultima _chiave trovata_.
Questo _invariante_ è assicurata siccome si aggiungono sempre i nuovi elementi infondo alla lista con _append_ e gli elementi generati hanno sempre lunghezza uguale o meggiore. 



##### Algoritmo Lineare nelle chiusure
Sfruttando le due osservazioni viste si puo trovare __una__ sola chiave in modo lineare

si parte dalla [[Modello Relazionale - Chiavi#Superchiave (Definizione)|superchiave]] banale, ovvero quella composta da tutti gli attributi e si escludono mano gli elementi finche quello che resta e’ una chiave 

per saltare dei passaggi si possono escludere direttamente gli attributi che non appaiono mai a sx
