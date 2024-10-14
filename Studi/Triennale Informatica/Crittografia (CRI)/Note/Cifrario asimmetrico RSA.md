---
Subject: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario asimmetrico RSA
---
il _cifrario RSA_ (dagli autori Rivest, Shamir, Adleman) é un [[Cifrari a chiave Asimmetrica|cifrario a chiave asimmetrica]] e utilizza direttamente i risultati del [[Algebra modulare]] per funzionare.


#### Generazione della chiave
per generare la chiave segue i seguenti step
1. [[Generazione di numeri Primi|genera]] due numeri [[Numeri primi|primi]] $p,q$ 
2. Calcola $n = q \times p$ e la [[Teorema di Eulero|funzione di Eulero]] $\Phi(n)=(q-1)(p-1)$ 
3. _sceglie_ un intero $e<\Phi(n)$ e  $e \in \mathcal{Z}^{*}_{n}$ [[Insieme dei coprimi|coprimo]] con $n$ 
4. calcola l intero $d$ [[Inverso di un numero in algebra modulare|inverso]] di $e\mod\Phi(n)$ con il [[Calcolare l inverso di un numero in algebra modulare#Usare la funzione estesa di Euclide|metodo di Euclide esteso]]
5. _assegna_ $k[pub]=\langle e,n\rangle$ e $k[prv]=\langle d\rangle$

#### Cifratura 
il mittente _mit_ per inviare un messaggio a _dest_  deve primo cifrarlo tramite la _chiave pubblica_ $k[pub]$ di _dest_.
abbiamo quindi che 
$$c = \mathcal{C}(m,k[pub])=m^{e}\mod n$$
e risulta che $c <n$
#### Decifrazione
_dest_ Riceve il crittogramma $c$ e lo decifra utilizzando la sua _chiave privata_ $k[prv]$ 
$$m=\mathcal{D}(c,k[prv])=c^{d} \mod n$$
#### Messaggi
I _messaggi_ sono [[Rappresentazione di oggetti matematici con sequenze|sequenze binarie]] che vengono convertite in un intero $m$. per impiegare il cifrario  è necessario che valga $m<n$ Siccome se avessimo $m \geq n$ succederebbe che il messaggio $m$ e il messaggio $m \mod n$ _generano_ lo stesso crittogramma $c$
 
Questo non è una gran limitazione siccome è sempre possibile dividere un messaggio in piu blocchi lunghi al piu $\ell=\lfloor \log_{2}(n)\rfloor$ _bit_. 
Questo assicura che i sotto messaggi $m_{i}<n$ 
	ciò avviene siccome  la [[Rappresentazione di oggetti matematici con sequenze|rappresentare in binario]] di $n$ utilizza $v=\lceil\log_{2}(n)\rceil$ _bit_ e siccome i messaggi avranno $\ell=\lfloor \log_{2}(n)\rfloor$ _bit_ e essendo che $n=qp$ _non è mai potenza di_ 2  non succede mai che $\ell=v$ e ho quindi che che $\ell < v$, ovvero i _sotto messaggi_ $m_{i}$ hanno meno _bit_ di rappresentazione rispetto ad $n$. 
	Quindi vale che il _sotto messaggio_ piu grande esprimibile è $2^{\ell}$ e quindi $m_{i}\leq2^{\ell} <n \leq 2^{v}$


#### Correttezza del cifrario 
Per garantire che il cifrario funzioni dobbiamo dimostrare che 
$$\mathcal{D}(\mathcal{C}(m,k[pub]),k[prv])=m$$
##### Teorema 
_Siano_ $n,e,d$ i parametri del cifrario $RSA$ 
_Se_ $m <n$
_Allora_ $(m^{e}\mod n)^{d} \mod n = m$

###### Dimostrazione

Per poter dimostrare questo teorema notiamo che  possiamo [[Algebra modulare|proprieta del algebra modulare]] abbiamo che $$(m^{e}\mod n)^{d} \mod n=m^{ed} \mod n =m$$
partiamo da alcune osservazioni generali:
essendo $d$ l [[Inverso di un numero in algebra modulare|inverso]] di $e \mod \Phi(n)$ ho che vale $$e \times d \equiv 1 \mod \Phi(n) \implies e \times d=1+r\Phi(n)$$ con $r$ _positivo e opportuno_.

e dimostriamo per casi
_caso_ $p,q$ non [[Divisibilità tra numeri|dividano]] $m$:
	abbiamo che il [[Massimo comun divisore|Massimo comun divisore]] $MCD(m,n)=1$ ovvero sono [[Numeri primi|coprimi]] e quindi per il [[Teorema di Eulero|Teorema di Eulero]] abbiamo che vale $m^{\Phi(n)} \equiv 1 \mod n$ 
	otteniamo quindi  $$
\begin{array}{}
m^{ed} & \mod n & = & \\
m^{1+r\Phi(x)} & \mod n & = &  \\
m \times (m^{\Phi(n)})^{r}  & \mod n  & = &  \\
m \times 1^{r}  & \mod n  & = & m
\end{array}
$$ 
_caso_ solo uno tra $p$ e $q$ [[Divisibilità tra numeri|divide]] $m$:
	poiché $p$ divide $m$ abbiamo $$m\equiv m^{r} \equiv 0 \mod p\implies (m^{r}-m) \equiv 0 \mod p$$per qualunque $r$ intero positivo.
	ora _osserviamo che_ $MCD(q,m)=1$ e usando un ragionamento simile al punto precedente abbiamo $$
	\begin{array}{}
	m^{ed}  & \mod q  & =  \\
    m^{1+r \Phi(n)}  & \mod q  & = \\
    m \times m^{r(p-1)(q-1)}  & \mod q  & = \\
    m \times (m^{(q-1)})^{r(p-1)}  & \mod q  & = \\  
	m \times (m^{\Phi(q)})^{r(p-1)}  & \mod q  & = \\
  m \times 1^{r(p-1)}  & \mod   q& =& m \mod q 
    \end{array}
	$$dove vale:
- $\Phi(q)=(q-1)$ perchè $q$ è [[Numeri primi|primo]] .
 - sto usando il  [[Teorema di Eulero|teorema di eulero]] per $m^{\Phi(q)}\equiv 1 \mod q$ 
	1. _dunque_ abbiamo che $$m^{ed} \equiv m \mod q\implies (m^{ed}-m) \equiv 0 \mod q$$ne consegue che $m^{ed}-m$ è [[Divisibilità tra numeri|divisibile]] sia per $p$ che per $q$, quindi è _[[Divisibilità tra numeri|divisibile]]_ per il loro prodotto $n=p\times q$ e _vale_ quindi  $$(m^{ed}-m)\equiv 0 \mod n \implies m^{e
	d}\equiv m \mod n$$ ovvero la tesi

_caso_ sia $p$ che $q$ dividano $m$:
	cosa in contradizione con le ipotesi siccome avremmo che $m \geq n$
	

### Vulnerabilità RSA
la difficoltata nella violazione di _RSA_ sta nel calcolare i fattori di  $n=pq$, la fattorizazione è un _problema difficile_,
Si sa sicuramente che calcolare [[Funzioni One-Way Trapdoor#Fattorizazione|la fattorizazione]] di $n \implies$  _violare il cifrario_ ma non si sa se vale l opposto. ovvero non si sa se calcolare la fattorizazione di  $n$ o risolvere un problema di [[Riducibilita dei problemi|difficolta equivalente]] è necessario per _violare il cifrario_ o se si può fare in altri modi
	Esistono delle versione di RSA per cui invece vale il $\iff$ ma sono piu complesse e non adottate 

#### Attacchi generali
il _calcolo della radice_ $e$-esima di $c$:
	tutti conoscono $k[pub]=\langle e,n \rangle$ e che $c = m^{e}\mod n$. 
	quindi per decrittografare il cifrario basterebbe calcolare $$m=\sqrt[e]{c} \mod   n$$ma Il problema del _[[Funzioni One-Way Trapdoor|calcolo della radice in modulo]]_ è difficile almeno quanto il calcolo della _fattorizzazione_ per $n$ _non [[Numeri primi|primo]]_ come in questo caso , di conseguenza tanto vale provare a calare i fattori direttamente
	

Sulla scoperta della [[Teorema di Eulero|funzione di Eulero]] $\Phi(n)$
	_osservando_ che sapendo $\Phi(n)$$$\Phi(n)=(p-1)(q-1)=n - (p+q)+1$$da cui possiamo calcolare $x_{1}=(p+q)=n +1-\Phi(n)$
	_osservando_ che vale   $$
	\begin{array}{}
	(p-q)^{2}  &  = & p^{2}+q^{2}-2n \\
     p^{2}+q^{2}+2n-2n-2n & = &(p+q)^{2}-4n
    \end{array}
	$$ da cui possiamo calcolare $x_{2}=(p-q)=\sqrt{ x_{1}^{2}-4n }$
	risolvendo il sistema tra i due _abbiamo_ in che $$p=\cfrac{x_{1}+x_{2}}{2} \ \ \ \ \ \ \ \ \ q=\cfrac{x_{1}-x_{2}}{2}$$il che significa che il calcolo di $\Phi(n)$ e la _fattorizzazione_ di $n$ sono due problemi _computazionalemte equivalenti_ ovvero sono _[[Riducibilita dei problemi|riducibili l uno al altro]]_ in tempo polinomiale

attacco esauriente su $d$:
	anche questa è una strategia che pero puo essere piu costata di _fattorizzare_ $n$ a seconda del parametro $e$. Non è attualmente noto se è possibile calcolare efficientemente $d$ utilizzando la chiave pubblica $\langle e,n\rangle$ ed eventualmente $c$.


#### Vincoli su p e q
Altri tipi di attacchi sono basati su delle _proprietà_ di $q$ e $p$, che in fatti vanno scelti per evitare che queste proprietà siano vere.

la distanza $|p-q|$ deve essere _molto grande_
	cosi non fosse avremmo che $\cfrac{p+q}{2}$ è prossimo a $\sqrt{n}$ e questa informazione ci permette di calcolare velocemente $p$ e $q$. per capire perche si parte dal eguaglianza vera $$
	\begin{array}{}
	\cfrac{(p+q)^{2}}{4}-n=\cfrac{(p-q)^{2}}{4} \\
	\left(\cfrac{p+q}{2}\right)^{2}-n=\left(\cfrac{p-q}{2}\right)^{2}
	
    \end{array}
	$$che mostra come $\left(\cfrac{p+q}{2}\right)^{2}-n$ si  un _quadrato perfetto_  e da qui si dimostra che $\cfrac{p+q}{2}>n$ tramite i seguenti passaggi
$$ \begin{array}{}
\cfrac{(p+q)^{2}}{2^{2}}-n & = & \cfrac{(p-q)^{2}}{4}  &  & & \implies\\  
\left(\cfrac{p+q}{2}\right)^{2} & = & \cfrac{(p-q)^{2}}{4} +n    & > &  n  &\implies \\
\left(\cfrac{p+q}{2}\right)^{2} & > & n  &  & & \implies \\
	\cfrac{p+q}{2} & > &  \sqrt{ n }
\end{array}
	$$ sapendo questi si possono  scandagliare gli _interi maggiori_ di $\sqrt{n}$ fino a trovare un intero $z$ tale che $z^{2}-n$ sia un _quadrato perfetto_ 
	ponendo $w^{2}=z^{2}-n$
	supponiamo quindi che sia $z=\cfrac{p+q}{2}$ e $w=\cfrac{p-q}{2}$ da cui inferire i valori $$p=z+w\ \ \ \ \ \ \ \ \ q =z-w$$ (viene dal attacco visto prima sulla funzione di eulero)
	infine si controlla la significatività provando a decrittare $c$.
	il fatto di avere $|q-p|$ ci garantisce che non dobbiamo spostarci troppo da $\sqrt{ n}$ per trovare i valori giusti.

Il [[Massimo comun divisore|Massimo comun divisore]] $MCD(p-1,q-1)$ deve essere _piccolo_. 
	non fosse cosi potrebbero esserci dei problemi siccome $p-1$ e $q-1$ sono entrambi pari al meglio possiamo scegliere $p$ e $q$ in modo che $\cfrac{p-1}{2}$ e $\cfrac{q-1}{2}$ siano _[[Numeri primi|coprimi]]_ 


_NON_ va riusato uno dei fattori per altro numero $n$
	_sia_  $n_{1}=pq$ e $n=pq’$ 
	_allora_ $MCD(n_{1},n_{2})=p$ 
	e sapendo $p$ scoprire $q$ è facile.

#### Vincoli su e
Anche il valore di $e$ va scelto _attentamente_, infatti abbiamo che 
	_sia_ $k$ un divisore di $p-1$ e $q-1$  (entrambi sono divisibili per 2)
	_sia_ $m$ il messaggio che si vuole cifrare
	_se_ $m$ e $n$ sono _coprimi_ 
	_allora_ per $e = 1+\cfrac{n}{k}$ si ha che$$c =m^{e}\mod n = m$$
	questo significa che tale valore di $e$ non cambia in nessun modo il messaggi.


il valore $e$ per _motivi di efficienza_ si vorremmo sceglier piccolo, ma non si deve andare _sotto un certo limite_. 
	Poniamo che che molti utenti abbiamo lo stesso valore di $e$ e che almeno $e$ di essi ricevano lo stesso messaggi $m$ attraverso i _crittogrammi_ $$c_{1}=m^{e} \mod n_{1},\dots c_{e}=m^{e} \mod n_{e}$$ dove $m<n_{i} \forall i. 1 \leq i \leq e$. Per le ipotesi del RSA possiamo assumere che valga $MCD(n_{i},n_{j}) \forall ij$ ovvero i vari $n_{i}$ siano _coprimi_ tra loro, siccome la _probabilità_ che questo non accada è [[Probabilità e variabili aleatorie|trascurabile]]. allora posso impostare il sistema come segue $$
	\begin{cases}
	m’ & \equiv & m^{e} \mod n_{1} \\
     & \vdots &   \\
    m’ & \equiv & m^{e} \mod n_{e}
    \end{cases}
	$$dove $m’$ è l incognita che rende vere tutte le _congruenze_. per il [[Teorema cinese del resto|teorema del resto cinese]] la soluzione _esiste_ $$m'<N=n_{1}\times\dots\times n_{e}\mid m' \equiv m^{e} \mod N$$Poiché $m<n_{i} \ \forall_{i}$ abbiamo che $m^{e}<N$ e possiamo quindi _scrivere semplicemente_ $m'=m^{e}$.
	dunque una volta calcolato $m'$ si può procedere a calcolare il messaggio _calcolando_ $$m=\sqrt[e]{m'}$$ cosa _facile_ non essendoci più il modulo.
nonostante questa vulnerabilità si preferisce prendere $e=3$ o altri primi piccoli cosi da tenere al massimo l efficienza e cancellare il problema aggiungendo un _paddig_ ad ogni messaggi



#### Vincoli su n
è importante che due utenti abbiamo $n$ diverso anche se il parametro $e$ è _diverso_
	Poniamo che due utenti abbiamo $n$ uguale e $e_{1}$ e $e_{2}$ diversi tale che $MCD(e_{1},e_{2})=1$ cosa molto _probabile_
	_Allora_ esistono due interi $r,s$ tale che vale $$e_{1}r+e_{2}s =1$$e questo è nella forma del [[Identità di Bezout|Identità di Bezout]] e quindi sono calcolabili con l _[[Algoritmo di Euclide Esteso|algoritmo di Euclide esteso]]_.
	assumiamo che $r<0$ (caso simmetrico per $s<0$)
	dati 
	- $c_1 = m^{e_{1}}\mod n$
	- $c_2= m^{e_{2}}\mod n$ 
	due crittogrammi relativi allo stesso messaggio $m$ 
	abbiamo che $$
	\begin{array}{}
	m & =  & m^{e_{1}r}\times m^{e_{2}s} & = 
 &   \\
 (c^{r}_{1}\times c_{2}^{s}) \mod  n  & = & ((c_{1}^{-1})^{-r}\times c_{2}^{s}) \mod n\end{array}
	$$dove $c_{1}$ e $n$ sono _coprimi_ e quindi l [[Inverso di un numero in algebra modulare|inverso]]  $c_{1}^{-1}$ esiste e si può calcolare con l [[Calcolare l inverso di un numero in algebra modulare#Usare la funzione estesa di Euclide|algoritmo di Euclide esteso]].
		questa inversione si fa per poter usare $-r$ che essendo negativo diventa positivo.
	$(c_{1}^{-1})^{-r}$  e $c_{2}^{s}$ si calcolano per [[Algoritmo delle Quadrature successive o esponenziazione veloce|esponenziazione successive]] siccome $-r,s$ sono numeri positivi.
	 da qui si può ricostruire in _[[Complessita|tempo polinomiale]]_  $m$


### Periodicità
per Gestire il problema della possibili periodicità si utilizzano le stesse strategie dei [[Cifrario a Composizione di blocchi|cifrari a blocchi]]
	 
