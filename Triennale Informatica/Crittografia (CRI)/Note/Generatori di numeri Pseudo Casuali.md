---
Course: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Generatori di numeri Pseudo Casuali
---
Generare numeri casuali è un compito difficile ma di grande importanza, siccome questo ha innumerevoli applicazioni in _crittografia_ e in altri campi. Ogni _numero_ puo essere [[Rappresentazione di oggetti matematici con sequenze|espresso in sequenza]] e abbiamo che una [[Sequenza casuali|Sequenza casuale]],in questo caso con _rappresentazione binaria_, per essere tale deve valere che la [[Definizione di Probabilita|probabilità]] di avere uno 0 e quella di avere un 1 è uguale per entrambi e quindi $\mathcal{P}=\frac{1}{2}$, ciò implica che ogni _bit_ deve essere _indipendente_ dal precedente/i.

> [!note]
> in realtà l avere probabilità uguali non è strettamente necessario siccome nella pratica se una delle due probabilità è piu altra si possono raggruppare le coppie $00$ e $11$ e sostituirle in modo da rendere la probabilità di nuovo uguali


#### Test statistici per la casualità
i _generatori_ o le _fonti_ si valutano confrontano le sequenze $S$ che _queste generano_ con una sequenza perfettamente casuale, le sequenze $S$ devono superare certi _test statistici_ per essere definite _casuali_. Questi sono
1. _Test di frequenza_: per sequenza lunghe tutti i caratteri sono equiprobabili, ovvero tutti i caratteri compiano approssimativamente lo stesso numero di volte in $S$
2. _Poker test_: le sotto sequenza di una data lunghezza fissa sono [[Definizione di Probabilita|equiprobabili]], ovvero non esiste una specifica sotto sequenza che compare piu spesso delle altre nella sequenza $S$
3. _Test di autocorrelazione_: verificano che non ci siano valori o sotto sequenze che si ripetono a distanze regolari. 
4. _Ran test_: l frequenza delle sotto sequenze massimali di simboli tutti uguali devono avere una [[Distribuzione di probabilita|Distribuzione di probabilita]] esponenzialmente negativa nella lunghezza della stringa 
questi 4 test bastano per applicazioni normali ma per essere anche _crittografamene sicuri_, e quindi utilizzabili per generare chiavi segrete devono soddisfare l ulteriore 
5. _Test di prossimo bit_:  non deve esiste un algoritmo  di tempo polinomiale in grado di _prevedere_ l $i +1$ bit della sequenza a partire dalla conoscenza degli i bit già generati con [[Definizione di Probabilita|probabilità]] maggiore di $\cfrac{1}{2}$


#### Fonti
per sequenza _brevi_ si possono utilizzare fenomeni fisici di cui si presume l aleatorietà. Queste sono dette fonti e sono ad esempio 
- il rumore in un microfono,
- la posizione di una testina sul disco.
- lettura di un fotone.
questi tipi di fonti andrebbero anche bene per le chiavi brevi ma nella pratica non si usano, sia perché non si puo davvero garantire una perfetta casualità sia perché solitamente servono sequenza casuali piu lunghe.


#### Generatori di numeri Pseudo-casuali
un generatore di numeri _pseudo casuali_ è un [[Algoritmi|algoritmo]] in grado di generare sequenze di numeri _casuali_ ma che si ripetono indefinitamente secondo un certo _periodo_. 

L algoritmo prende in ingresso un numero detto _seme_ che da inizio alla sequenza. 

questo tipi di algoritmi sono solitamente molto corti e dalla teoria delle [[Sequenza casuali|sequenze casuali]] sappiamo che questo vuol dire che le _sequenze generate_ dal programma non sono casuali. Infatti abbiamo che l algoritmo è deterministico e che se dato in input lo stesso _seme_ produrrà la _stessa sequenza_.
questi algoritmi sono pero considerati _amplificatori_ di casualità, infatti generando in modo casuale un _seme_ di lunghezza $m$ si può generare una _sequenza apparentemente casuale_ di lunghezza $n\gg m$, 
Assumendola [[Rappresentazione di oggetti matematici con sequenze|rappresentazione binaria]] abbiamo che il numero di _sequenze **diverse** generabili_ cambia con la lunghezza del _seme_ infatti fissando la lunghezza a $m$ abbiamo che il numero di _semi distinti_ è $2^{m}$ mentre le _sequenze **possibili**_ sono invece  $2^{n}$  e vale $$2^{n}\gg 2^{m}$$ovvero sono in numero _molto maggiori_ rispetto ai _semi_, di conseguenza _molte sequenze_ non sono raggiungibili dal generatore.


##### Generatore lineare
il _generatore lineare_ è un generatore di numeri _pseudo casuali_ che dati $a,b,m$ _interi positivi_ genera una sequenza $x_{1},x_{2},\dots,x_{n}$ a partire dal _seme_ $x_{0}$ secondo la relazione $$x_i = (ax_{i-1} + b)\mod m$$
per garantire una periodo lungo e quindi _indure una permutazione_ dei numeri $1,\dots,m-1$ si deve scegliere 
- $m$ grande
- il [[Massimo comun divisore]] $MCD(b,m)=1$ ovvero devono essere [[Numeri primi|coprimi]] 
- $a-1$ deve essere [[Divisibilità tra numeri|divisibile]] per ogni [[Teorema fondamentale del aritmetica|fattore primo]] di $m$ 
- _se_ $m$ è un multiplo di $4$ anche $a-1$ deve essere un multiplo di $4$ 


##### Generatore polinomiale
un _generatore Polinomiale_ è un generatore di numeri _pseudo casuali_, Questo è un _estensione_ del _generatore lineare_ e dati i numeri $a_{0},\dots a_{n}$ e il _seme_ $x_{0}$  genera una sequenza secondo la relazione  
$$x_{i}=\left( \sum^{n}_{t=0}a_{t}x^{t}_{i-1} \right)\mod m$$


##### Considerazioni
il _generatore lineare_ e il _generatore polinomiale_ possono essere trasformati per generare stringhe binarie, questo si fa calcolando $r=\cfrac{x_{i}}{m}$ se la prima cifra decimale di $r$ è dispari si genera 1 altrimenti 0

il _generatore lineare_ e il _generatore polinomiale_ passano i primi 4 test statistici ma esistono algoritmi polinomiali che data una _sequenza generata_ possono svelare i parametri del generatore, e calcolare facilmente il prossimo valore, non passano quindi il _quinto test_  



##### Generatore BBS  (Blum, Blum, Shub)
il _generatore BBS_ è un generatore di numeri _pseudo casuali_ che 
_sia_ $n =p \cdot q$ il prodotto di due numeri [[Numeri primi|primi]] gradi _tali che_   
- $p \mod 4 =3$  
- $q \mod 4=3$ 
- $MCD(2\cdot\left\lfloor\cfrac{p}{4}\right\rfloor+1,2\cdot\left\lfloor\cfrac{q}{4}\right\rfloor+1)=1$ 
e _sia_
- $f(x)=x^{2}\mod n$  una [[Funzioni One-Way|funzione one way]]  
-  $b(x)= \text{ è dispari}$ un _[[Funzioni One-Way#Predicati Hard-core|predicato hard-hardcore]]_  per $f(x)$
il _generatore BBS_ scelto un _seme_ $x_0= f(x)$ con un $x$  qualsiasi genera una successione di numeri $x_{1},x_{2},\dots,x_{m}$ con $m \leq n$  e genera in corrispondenza dei numeri una sequenza binaria $b_{i}$ secondo la relazione
$$x_{i}=f(x_{i-1})=(x_{i-1})^{2}\mod n$$
e 
$$b_{i}= \begin{cases}
1  &  if & x_{m-i} \text{ dispari} \\
0  & else
\end{cases}$$
Il _generatore_ parte da $x_{0}$ a cui corrisponde $b_{m}$ e procede al calcolo di degli interi $x_{1},\dots x_{m}$ memorizzando i corrispettivi $b_{m-1},\dots b_{0}$ che comunica al sterno in ordine _inverso_ (da destra verso sinistra??).


_questo generatore_  supera il _test di prossimo bit_ e viene direttamente da un  _[[Funzioni One-Way#Proprietà|risultato generale delle funzioni oneway]]_ e dei _predicati Hardcore_ infatti abbiamo che questo è solo un caso specifico di quel _risultato generale_.

> [!note]
> Questo Generatore per quanto perfettamente sicuro tende ad essere molto lento di conseguenza si preferisce utilizzare altri tipi di generatori per l utilizzo crittografico



