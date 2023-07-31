---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Generazione di numeri Pseudo Casuali
---
Generare numeri casuali è un compito difficile ma di grande importanza, siccome questo ha innumerevoli applicazioni in _crittografia_ e in altri campi. Ogni _numero_ puo essere [[Rappresentazione di oggetti matematici con sequenze|espresso in sequenza]] e abbiamo che una [[Sequenza casuali|Sequenza casuale]],in questo caso con _rappresentazione binaria_, per essere tale deve valere che la [[Probabilità e variabili aleatorie|Probabilita]] di avere uno 0 e quella di avere un 1 è uguale per entrambi e quindi $\mathcal{P}=\frac{1}{2}$, ciò implica che ogni _bit_ deve essere _indipendente_ dal precedente/i.

> [!note]
> in realtà l avere probabilità uguali non è strettamente necessario siccome nella pratica se una delle due probabilità è piu altra si possono raggruppare le coppie $00$ e $11$ e sostituirle in modo da rendere la probabilità di nuovo uguali


#### Test per accertassi della casualità
i _generatori_ o le _fonti_ si valutano confrontano le sequenze $S$ che _queste generano_ con una sequenza perfettamente casuale, le sequenze $S$ devono superare certi _test statistici_ per essere definite _casuali_. Questi sono
1. _Test di frequenza_: per sequenza lunghe tutti i caratteri sono equiprobabili, ovvero tutti i caratteri compiano approssimativamente lo stesso numero di volte in $S$
2. _Pokert test_: le sotto sequenza di una data lunghezza fissa sono equiprobabili, ovvero non esiste una specifica sotto sequenza che compare piu spesso delle altre nella sequenza $S$
3. _Test di autocorrelazione_: verificano che non ci siano valori o sotto sequenze che si ripetono a distanze regolari. 
4. _Ran test_: l frequenza delle sotto sequenze massimali di simboli tutti uguali devono avere una distribuzione esponenzialmente negativa nella lunghezza della stringa 
questi 4 test bastano per applicazioni normali ma per essere anche _crittografamene sicuri_, e quindi utilizzabili per generare chiavi segrete devono soddisfare l ulteriore 
5. _Test di prossimo bit_:  non deve esiste un algoritmo  di tempo polinomiale in grado di _prevedere_ l $i +1$ bit della sequenza a partire dalla conoscenza degli i bit già generati con probabilità maggiore di $\frac{1}{2}$


#### Fonti
per sequenza _brevi_ si possono utilizzare fenomeni fisici di cui si presume l aleatorietà. Queste sono dette fonti e sono ad esempio 
- il rumore in un microfono,
- la posizione di una testina sul disco.
- lettura di un fotone.
questi tipi di fonti andrebbero anche bene per le chiavi brevi ma nella pratica non si usano, sia perché non si puo davvero garantire una perfetta casualità sia perché solitamente servono sequenza casuali piu lunghe.


#### Generatori di numeri Pseudo-casuali
i numeri _pseudo casuali_ è un [[Algoritmi|algoritmo]] in grado di generare sequenze di numeri _casuali_ ma che si ripetono indefinitamente secondo un certo _periodo_. L algoritmo prende in ingresso un numero detto _seme_ che da inizio alla sequenza. 

questo tipi di algoritmi sono solitamente molto corti e dalla teoria delle [[Sequenza casuali|sequenze casuali]] sappiamo che questo vuol dire che le _sequenze generate_ dal programma non sono casuali. Infatti abbiamo che l algoritmo è deterministico e che se dato in input lo stesso _seme_ produrrà la _stessa sequenza_.
questi algoritmi Sono pero considerati _amplificatori_ di casualità, siccome generando in modo casuale un _seme_ di lunghezza $m$ si puo generare una _sequenza apparentemente casuale_ di lunghezza $n\gg m$, ma il numero di _sequenze generabili_ cambia con la lunghezza del _seme_ e al massimo abbiamo $2^{m}$ _semi possibili_ nel caso di [[Rappresentazione di oggetti matematici con sequenze|rappresentazione binaria]], le _sequenze possibili_ sono invece  $2^{n}$  quindi in numero molto maggiori rispetto ai _semi_, di conseguenza molte sequenze non sono raggiungibili dal generatore 


##### Generatore lineare
il _generatore lineare_ è un generatore di numeri _pseudo casuali_ che dati $a,b,m$ _interi positivi_ genera una sequenza $x_{1},x_{2},\dots,x_{n}$ a partire dal _seme_ $x_{0}$ secondo la relazione $$x_i = (ax_{i-1} + b)\mod m$$
per garantire una periodo lungo e quindi _indure una permutazione_ dei numeri $1,\dots,m-1$ si deve scegliere 
- $m$ grande
- $MCD(b,m)=1$ ovvero devono essere [[Numeri primi|coprimi]] 
- $a-1$ deve essere [[Divisibilità dei numeri|divisibile]] per ogni [[Teorema fondamentale del aritmetica|fattore primo]] di $m$ 
- _se_ $m$ è un multiplo di $4$ anche $a-1$ deve essere un multiplo di $4$ 



##### Generatore polinomiale
un _generatore Polinomiale_ è un generatore di numeri _pseudo casuali_, Questo è un _estensione_ del generatore lineare e dati i numeri $a_{1},\dots a_{n}$ genera una sequenza $x_{1},x_{2},\dots,x_{n}$ a partire dal _seme_ $x_{0}$ secondo la relazione 
$$x_{i}=(a_{1}x^{t}_{i-1}+a_{2}x^{t-1}_{i-1}+\cdots + a_{t}x_{i-1}+a_{t+1})\mod n$$


##### Considerazioni
il _generatore lineare_ e il _generatore polinomiale_ possono essere trasformati per generare stringhe binarie, questo si fa calcolando $r=\cfrac{x_{i}}{m}$ se la prima cifra decimale di $r$ è dispari si genera 1 altrimenti 0

il _generatore lineare_ e il _generatore polinomiale_ passano i primi 4 test statistici ma esistono algoritmi polinomiali che data una _sequenza generata_ possono svelare i parametri del generatore, non passano quindi il quinto test  


### Funzioni One-Way
le _Funzioni one-way_ sono funzioni facili da calcolare ma difficili da invertire, ovvero richiede _tempo polinomiale_ calcolare $y =f(x)$ ma _tempo esponenziale_ calcolare $x=f^{-1}(y)$, le complessità sono calcolare nelle lunghezza della rappresentazione.

Di solito queste tipologia di funzioni fanno impiego della teoria del _algebra modulare_ per essere _One-Way_

un esempio è la funzione 
$$f(x)=x^{2}\mod n$$
con $n$ non primo.

#### Predicati Hard-core
Un _predicato_ $b(x)$  per una funzione _One-way_ $f(x)$
è detto _Hard-Core_ se è facile da calcolare conoscendo $x$ ma difficile da prevedere con [[Probabilità e variabili aleatorie|probabilita]] $>\cfrac{1}{2}$ conoscendo solo il valore di $f(x)$

per la funzione $f(x)=x^{2}\mod n$ un predicato _hardcore_ è
$$b(x)= x \text{ è dispari}$$


#### Prodiera
_sia_ $f(x)$ funzione _one way_ e $b(x)$ un _predicato hardcore_ per $f(x)$ e indicando con $f^{(i)}(x)$ l _applicazione_ di $i$  volte di $f(x)$ avremo che la _sequenza binaria_
$$S = b(f^{(i)}(x)) \ \ \ b(f^{(i-1)}(x)) \ \ \ \cdots \ \ \ b(f^{(1)}(x))  \ \ \ b(x) $$
supera il _test di prossimo bit_ 
questo discendo direttamente dalle proprietà delle funzioni _one way_ e dei predicati _hardcore_  


##### Generatore Blum, Blum, Shub (BBS)
il _generatore BBS_ è un generatore di numeri _pseudo casuali_ che 
_sia_ $n =p \cdot q$ il prodotto di due numeri [[Numeri primi|primi]] gradi _tali che_   
- $p \mod 4 =3$  
- $q \mod 4=3$ 
- $2\cdot\left\lfloor\cfrac{p}{4}\right\rfloor+1$ è primo 
- $2\cdot\left\lfloor\cfrac{q}{4}\right\rfloor+1$ è  primo
e che  $x_{0}=y^{2}\mod n$ per un qualunque $y$ genera una sequenza di numeri $x_{1},x_{2},\dots,x_{m}$ con $m \leq n$ a partire dal _seme_ $x_{0}$, e genera in corrispondenza dei numeri una sequenza binaria $b_{i}$ secondo la relazione
$$x_{i}=(x_{i-1})^{2}\mod n$$
e 
$$b_{i}= \begin{cases}
1  &  if & x_{m-i} \text{ dispari} \\
0  & else
\end{cases}$$

_questo generatore_  supera il _test di prossimo bit_ e viene direttamente dal _risultato generale_ delle funzioni oneway e dei predicati Hardcore infatti abbiamo che questo è solo un caso specifico di quel risultato generale.

> [!note]
> Questo Generatore per quanto perfettamente sicuro tende ad essere molto lento di conseguenza si preferisce utilizzare altri tipi di generatori per l utilizzo crittografico

