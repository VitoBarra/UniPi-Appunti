---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario Asimmetrico RSA
---
### Definizione
é un [[Cifrari a chiave Asimmetrica|cifrario a chiave asimmetrica]] e utilizza direttamente i risultati del [[Algebra modulare]] per funzionare.


#### Generazione della chiave
per generare la chiave segue i seguenti step
1. [[Generazione di numeri Primi|genera]] due numeri [[Numeri primi|primi]] $p,q$ 
2. Calcola $n = q \times p$ e la [[Teorema di Eulero|funzione di Eulero]] $\Phi(n)=(q-1)(p-1)$ 
3. _sceglie_ un intero $e<\Phi(n)$ e  $e \in \mathcal{Z}^{*}_{n}$ [[Insieme dei coprimi|coprimo]] con $n$ 
4. calcola l intero $d$ [[Inverso di un numero in algebra modulare|inverso]] di $e\mod\Phi(n)$ con il [[Algoritmo di Euclide Esteso|metodo di Euclide esteso]]
5. _assegna_ $k[pub]=\langle e,n\rangle$ e $k[prv]=\langle d\rangle$

#### Cifratura 
la cifratura per inviare un messaggio a _dest_ avviene tramite la chiave pubblica $k[pub]$. abbiamo quindi che 
$$c = \mathcal{C}(m,k[pub])=m^{e}\mod n$$
e risulta che $c <n$
#### Decifrazione
_dest_ Riceve il crittogramma $c$ e lo decifra calcolando 
$$m=\mathcal{D}(c,k[prv])=c^{d} \mod n$$

#### Messaggi
I _messaggi_ sono [[Rappresentazione di oggetti matematici con sequenze|sequenze binarie]] che vengono convertite in un intero $m$. per impiegare il cifrario  è necessario che valga $m<n$ Siccome se avessimo $m \geq n$ succederebbe che il messaggio $m$ e il messaggio $m \mod n$ _generano_ lo stesso crittogramma $c$
 
Questo non è una gran limitazione siccome è sempre possibile dividere un messaggio in piu blocchi lunghi al piu $\ell=\lfloor \log_{2}(n)\rfloor$ _bit_. Questo rende i sotto messaggi $<n$siccome per la [[Rappresentazione di oggetti matematici con sequenze|rappresentare in binario]] di $n$ utilizzo $v=\lceil\log_{2}(n)\rceil$ _bit_ e siccome i messaggi avranno $\ell=\lfloor \log_{2}(n)\rfloor$ _bit_ e essendo che $n=qp$ _non è mai potenza di_ 2 ho che $\ell < v$, ovvero i _sotto messaggi_ $m_{i}$ hanno meno _bit_ di rappresentazione rispetto ad $n$. 
Quindi vale che il _sotto messaggio_ piu grande esprimibile è $2^{\ell}$ e quindi $m_{i}\leq2^{\ell} <n \leq 2^{v}$


#### Correttezza del cifrario 
Per garantire che il cifrario funzioni dobbiamo dimostrare che 
$$\mathcal{D}(\mathcal{C}(m,k[pub]),k[prv])=m$$
##### Teorema 
_Siano_ $n,e,d$ i parametri del cifrario $RSA$ 
_Se_ $m <n$
_Allora_ $(m^{e}\mod n)^{d} \mod n = m$

###### Dimostrazione
Per poter dimostrare questo teorema notiamo che  possiamo [[Algebra modulare|proprieta del algebra modulare]] possiamo riscrivere $(m^{e}\mod n)^{d} \mod n$ _come_ $m^{ed} \mod n =m$.

Per completare la dimostrazione dobbiamo analizzare de casi

_caso_ $p,q$ non [[Divisibilità tra numeri|dividano]] $m$:
	abbiamo che il [[Massimo comun divisore|Massimo comun divisore]] $MCD(m,n)=1$ ovvero sono [[Numeri primi|coprimi]] e quindi per il [[Teorema di Eulero|Teorema di Eulero]] abbiamo che vale $m^{\Phi(n)} \equiv 1 \mod n$ 
	essendo $d$ l inverso di $e \mod \Phi(n)$ ho che vale $e \times d \equiv 1 \mod \Phi(n) \implies e \times d=1+r\Phi(n)$ con $r$ positivo e opportuno.
	otteniamo quindi 
	$$
\begin{array}{}
m^{ed} & \mod n & = & \\
m^{1+r\Phi(x)} & \mod n & = &  \\
m \times (m^{\Phi(n)})^{r}  & \mod n  & = &  \\
m \times 1^{r}  & \mod n  & = & m
\end{array}
$$ 
_caso_ solo uno tra $p$ e $q$ [[Divisibilità tra numeri|divide]] $m$:
	poiché $p$ divide $m$ abbiamo $m\equiv m^{r} \equiv 0 \mod p$ ovvero $m-m^{r} \equiv 0 \mod p$ per qualunque $r$ intero positivo.
	abbiamo che 
	$$
	\begin{array}{}
	m^{ed}  & \mod q  & =  \\
    m^{1+r \Phi(n)}  & \mod q  & = \\
    m \times m^{r(p-1)(q-1)}  & \mod q  & = \\
    m \times (m^{(q-1)})^{r(p-1)}  & \mod q  & =  & m \mod q 
    \end{array}
	$$
	dove l ultima equazione è giustificata è giustificata dal [[Teorema di Eulero|teorema di eulero]] dove $m^{(q-1)}\equiv 1 \mod q$
	dunque  abbiamo che $m^{ed} \equiv m \mod q$ e quindi $m^{ed}-m \equiv 0 \mod q$
	ne consegue che $m^{eq}-m$ è divisibile sia per $p$ che per $q$, quindi è divisibile per il loro prodotto $n=p\times q$. ovvero $(m^{eq}-m)\equiv 0 \mod n$. da qui la tesi

_caso_ sia $p$ che $q$ dividano $m$:
	cosa in contradizione con le ipotesi siccome avremmo che $m \geq n$
	

### Vulnerabilità RSA
la difficoltata nella violazione di RSA sta nel calcolare $n=pq$ _problema difficile_,
si sa sicuramente che calcolare $n \implies$  _violare il cifrario_ ma non si sa se vale l opposto. ovvero non si sa se calcolare $n$ o risolvere un problema di difficolta equivalente è necessario per _violare il cifrario_

alcuni tentativi sono:

il _calcolo della radice_ $e$-esima di $c$:
	questo siccome tutti sanno che $k[pub]=\langle e,n \rangle$ e che $c = m^{e}\mod n$. Il problema del _[[Funzioni One-Way Trapdoor|calcolo della radice in modulo]]_ è difficile almeno quanto il calcolo della _fattorizzazione_ per $n$ _non [[Numeri primi|primi]]_ come in questo caso , di conseguenza tanto vale provare a calare i fattori direttamente

Sulla scoperta della [[Teorema di Eulero|funzione di Eulero]] $\Phi(n)$
	_osservando_ che con sapendo $\Phi(n)$ $\Phi(n)=(p-1)(q-1)=n - (p+q)+1$ possiamo calcolare $x_{1}=(p+q)$
	_osservando_ che vale che                $(p-q)^{2}=(p+q)^{2}-4n$ possiamo calcolare $x_{2}=(p-q)$
	_abbiamo_ in fine che $p=\cfrac{x_{1}+x_{2}}{2}$ e $p=\cfrac{x_{1}x_{2}}{2}$
	il che significa che il calcolo di $\Phi(n)$ e la _fattorizzazione_ di $n$ sono due problemi _computazionalemte equivalenti_ ovvero sono _[[Riducibilita dei problemi|riducibili l uno al altro]]_ in tempo polinomiale

attacco esauriente su $d$:
	anche questa è una strategia che pero puo essere piu costata di _fattorizzare_ $n$ a seconda del parametro $e$. Non è attualmente noto se è possibile calcolare efficientemente $d$ utilizzando la chiave pubblica $\langle e,n\rangle$ ed eventualmente $c$.


Altri tipi di attacchi sono basati su delle _proprietà_ di $q$ e $p$, che in fatti vanno scelti per evitare che queste proprietà siano vere.

la distanza $|q-p|$ deve essere _molto grande_
	cosi non fosse avremmo che $\cfrac{p+q}{2}$ è prossimo a $\sqrt{n}$ e con questo possiamo calcolare velocemente $p$ e $q$. questo vale siccome 
	dal eguaglianza $\cfrac{(p+q)^{2}}{4}-n=\cfrac{(p-q)^{2}}{4}$. si puo dimostrare che $\cfrac{p+q}{2}> \sqrt{ n }$ e si possono scandagliare gli _interi maggiori_ di $\sqrt{n}$ fino a trovare un intero $z$ tale che $z^{2}-n$ sia un _quadrato perfetto_ 
	ponendo $w^{2}=z^{2}-n$
	supponiamo quindi che sia $z=\cfrac{p+q}{2}$ e $w=\cfrac{p-q}{2}$ da cui inferire i valori $p=z+w$ e $q =z-w$ 
	infine si controllano i valori su $c$.
	il fatto di avere $|q-p|$ ci garantisce che non dobbiamo spostarci troppo da $\sqrt{ n}$ per trovare i valori giusti.

Il [[Massimo comun divisore|Massico comun divisore]] $MCD(p-1,q-1)$ deve essere _piccolo_. 
	non fosse cosi potrebbero esserci dei problemi e per evitarli bisogna scegliere $p$ e $q$ in modo che $\cfrac{p-1}{2}$ e $\cfrac{q-1}{2}$ siano _[[Numeri primi|coprimi]]_ 

Anche il valore di $e$ va scelto _attentamente_, infatti abbiamo che 
	_sia_ $k$ un divisore di $\Phi(n)$ in particolare questo è divisibile per 2 e per 4, 
	_se_ $m$ e $n$ sono _coprimi_ 
	_allora_ per $e = 1+\cfrac{\Phi(n)}{k}$ si ha che
	$c =m^{e}\mod n = m \times (m^{\Phi(n)})^{1/k} \mod n=m$
	dove l ultimo passaggio è dato dal [[Teorema di Eulero|Teorema di Eulero]].
	questo significa che tale valore di $e$ non cambia in nessun modo il messaggi.

il valore $e$ per _motivi di efficienza_ si vorremmo sceglier piccolo, ma non si deve andare _sotto un certo limite_. 
	Poniamo che che molti utenti abbiamo lo stesso valore di $e$ e che almeno $e$ di essi ricevano lo stesso messaggi $m$ attraverso i _crittogrammi_ $c_{1}=m^{e} \mod n_{1},\dots c_{e}=m^{e} \mod n_{e}$ 
	dove $m<n_{i}$ e $1 \leq i \leq e$. Per le ipotesi del RSA possiamo assumere che i vari $n_{i}$ siano _coprimi_ tra loro, siccome la _probabilità_ che questo non accada è trascurabile.
	per il [[Teorema cinese del resto|teorema del resto cinese]] esiste ed è unico un numero $m'<n=n_{1}\times n_{2}\times\dots\times n_{e}$ che sodisfa l equazione $m' \equiv m^{e} \mod n$. 
	Poiché $m<n_{i} \ \forall_{i}$ abbiamo che $m^{e}<n$ e possiamo quindi scrivere semplicemente $m^{'}=m^{e}$.
	dunque calcolando $m'$ si può procedere a calcolare il messaggio calcolando $m=\sqrt[e]{m'}$ cosa in questo caso facile non essendoci più il modulo.
nonostante questa vulnerabilità si preferisce prendere $e=3$ o altri primi piccoli cosi da tenere al massimo l efficienza e cancellare il problema aggiungendo un _paddig_ ad ogni messaggi



è importante che due utenti abbiamo $n$ diverso anche se il parametro $e$ è diverso
	Poniamo che due utenti abbiamo $n$ uguale e $e_{1}$ e $e_{2}$ diversi tale che $MCD(e_{1},e_{2})=1$ cosa molto _probabile_
	_Allora_ esistono dune interi $r,s$ tale che vale $$e_{1}r+e_{2}s =1$$ e questo è nella forma del [[Identità di Bezout|Identità di Bezout]] e quindi sono calcolabili con l _[[Algoritmo di Euclide Esteso|algoritmo di Euclide esteso]]_.
	assumiamo che $r<0$ (caso simmetrico per $s<0$)
	dati $c_1,c_2$ due crittogrammi relativi allo stesso messaggio $m$ 
	abbiamo che $m=m^{e_{1}r+e_{2}s}=(c^{r}_{1}\times c_{2}^{s}) \mod  n =((c_{1}^{-1})^{-r}\times c_{2}^{s}) \mod n$
	 si può quindi calcolare $c_{1}^{-1}$ con l [[Algoritmo di Euclide Esteso|algoritmo di Euclide esteso]] e $(c_{1}^{-1})^{-r}$  e $c_{2}^{s}$ per [[Algoritmo delle Quadrature successive o esponenziazione veloce|esponenziazione successive]] siccome $-r,s$ sono numeri positivi.
	 da qui si può ricostruire $m$



per Gestire il problema della possibili periodicità si utilizzano le stesse strategie dei [[Cifrario a Composizione di blocchi|cifrari a blocchi]]
	 
