---
Course: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario simmetrico DES
---
il _Data Encryption Standard_ (DES) è un [[Cifrari a chiave Simmetrica|cifrario a chiave simmetrica]] pensato per comunicazione di massa quindi per lo scambio di messaggi _non classificati_


#### Definizione
il DES ha la seguente struttura. 

- il messaggi $m$ è suddiviso in blocchi tutti lunghi $64$ bit
- la cifratura e la decifratura avviene attraverso $r$ fasi consecutive dette _rounds_.
	-  nel implementazione classica $r=16$
- la chiave $k$  e composta da $b$ _byte_ di cui per ogni byte 7 sono scelti arbitrariamente e l ottavo è un [[Algoritmo di parita per il controllo degli errori|bit di parità]]
- Dalla chiave vengono create $r$ sottochiavi $k[0],k[1],\dots,k[r-1]$
- Indicando con $i$ il _round_ corrente e con  $i+1$ la fase successiva con $i = 1, \dots,r$ nel cifrario un _round_ $i$ vengono eseguiti i passi 
	1. per $i=1$  il messaggio viene diviso in due meta sinistra $S$ e destra $D$  
	2. per $i=2,\dots,r$ $S_{i+1} =D_{i} \ \ \ \ D_{i+1}=f(k[i-1],D_{i},S_{i})$
		-  con $f$ una funzione non lineare.
	3. finiti gli $r$ round i le due meta vengono scambiate di nuovo e concatenate, producendo il crittogramma $c$
- La decrittazione funziona invertendo il processo appena descritto.

con questo schema abbiamo che tutti i bit del _crittogramma_ dipenda da tutti i bit del messaggio e da tutti i bit della chiave.


#### Breakdown ad alto livello
Ad alto livello abbiamo che la crittazione è divisa piu parti
_Permutazioni iniziali_ :
	$PI$ permuta i 64 bit del messaggi in chiaro. 
	$T$ cancella i _bit di parità_ e permuta i restanti 56 bit per generare la prima sotto chiave $k[0]$
_Trasformazione centrale_: 
	La sequenza permutata da $PI$  viene divisa in un blocco sinistro $S[0]$ e un blocco destro $D[0]$ di $32$ bit ciascuno. 
	Su questi due blocchi si eseguono, nelle successive fasi del DES, sedici trasformazioni strutturalmente uguali, ciascuna con una diversa sottochiave $k[i]$ di $56$ bit derivata dalla chiave iniziale k. 
	L _i-esima_ fase riceve in ingresso tre blocchi $S[i − 1], D[i − 1], k[i − 1]$ rispettivamente di $32, 32$ e $56$bit, e produce in uscita tre nuovi blocchi $S[i], D[i], k[i]$ che costituiscono l’ingresso alla fase successiva. Dopo l’ultima fase i due blocchi $S[16]$ e $D[16]$ vengono scambiati e concatenati tra loro in un unico blocco di $64$ bit da cui si costruirà il crittogramma finale.
_permutazione finale_: 
	PF genera la permutaizone finale del è l inversa di _PI_
 ovvero riporta i bit nella l’ora posizione originale.
le permutazioni sono specificate in questa tabella.
![[Pasted image 20230707214636.png]]

Il processo complessivo segue come nel immagine
![[Pasted image 20230707195205.png]]
andando ad analizzare cosa succede nella i-esima fase abbiamo che i componenti sono

_Schift ciflico_: 
	$SC[i]$. La sottochiave $k[i − 1]$ di 56 bit, ricevuta dalla fase precedente, viene suddivisa in due meta di $28$ bit ciascuna. Su ognuna di queste la funzione $SC[i]$ esegue uno _shift ciclico_ verso sinistra di un _numero di posizioni_ definito come segue: $$\begin{cases}
		SC[i] = 1 &if &i = 1, 2, 9, 16 \\ SC[i] = 2 & else
     \end{cases}$$Le due parti cosi traslate vengono concatenate in un unico blocco di $56$ bit che costituisce la sottochiave $k[i]$ per la fase successiva.
		
_Compressione e trasposizione_ (_CT_):
	Il blocco di $56$ bit prodotto dall’operazione precedente viene ulteriormente elaborato per produrre un nuovo blocco da $48$  utilizzato poi in operazione di XOR con il risultato di $EP$
	La funzione $CT$ esegue una permutazione del blocco e una selezione di $48$ bit da esso. la _combinazione delle funzioni_ $SC[i]$ e $CT$ garantisce che in ogni fase venga estratto dalla sottochiave un diverso sottoinsieme di bit per la cifratura. 
	Si calcola che nella cifratura ogni bit della chiave originale $k$ partecipi in media a quattordici fasi

_Espansione e permutazione_ (_EP_):
	Il blocco $D[i − 1]$ di $32$ bit generato nella fase precedente viene espanso a $48$ bit _duplicando_ $16$ bit in ingresso e spostandone altri per ottenere un blocco della stessa dimensione di quello estratto dalla _sottochiave_ e poter eseguire lo _XOR_ tra i due. Si incrementa cosi la dipendenza tra ingresso e uscita della fase, poiché i bit duplicati influenzano due delle sostituzioni operate dalla funzione $S$ del blocco seguente.
![[Pasted image 20230707223730.png]]


_Sostituzione S (o S-box)_:
	Questa funzione costituisce la parte cruciale e “magica” su cui si basa la sicurezza del cifrario. Essa composta di _otto sotto funzioni_ combinatorie $S_1, S_2,\dots,S_8$  L’ingresso di $48$ bit viene decomposto in otto blocchi $B_1, B_2,\dots,B_8$ di $6$ bit ciascuno che costituiscono l’ingresso alle _sotto funzioni_ di pari indice. 
	Sia $B_{j} = b_1b_2b_3b_4b_5b_6$. Questi bit vengono divisi in due gruppi $b_1b_6$ e $b_2b_3b_4b_5$ che definiscono due numeri $x, y$, con $0 \leq x \leq 3$ e $0 \leq y \leq 15$, utilizzati per accedere alla cella di riga $x$ e colonna $y$ in una tabella che definisce la sottofunzione $S_j$ . Il _numero contenuto_ al incrocio di _riga e colonna_ contenuto è compreso tra $0$ e $15$, ed è quindi [[Rappresentazione di oggetti matematici con sequenze|rappresentato]] con 4 bit, questa è l _output_ di $S_j$ realizzando cosi una compressione da 6 a 4 bit. Complessivamente gli otto blocchi generano una sequenza di $32$ bit.
	I blocchi $EP$ e $S$ sono studiati in modo che tutti i bit di $D[i−1]$ influenzino l’uscita di $S$, senza la quale non sarebbe poi possibile decifrare il messaggio.

![[Pasted image 20230707222422.png]]

_Permutazione_ (_P_). è una permutazione di 32 bit che genera il blocco finale $D[i]$
![[Pasted image 20230707222509.png]]

e mettendo insieme i vari pezzi per ogni fase ho lo schema seguiente. dove $\oplus$ è lo [[Operazioni logiche|XOR]]
![[Pasted image 20230707221817.png]]

tutte le funzione nel cifrario, tranne che per la $S$-box sono lineari e quindi vale che $f(x) \oplus f(y) =f(x \oplus y)$ 
il grande della  _sicurezza_ del cifrario viene dalla $S$-box proprio perche non è lineare.

#### Attacchi e vulnerabilità
per analizzare le vulnerabili del cifrario DES si parte dal valutare l attacco esauriente. 
i bit della chiave sono $56$ quindi ci sono $|K|=2^{56}$ numero molto alto di [[Combinatoria|permutazioni con ripetizioni]] ma analizzando la struttura del cifrario si _puo ridurre_ lo spazio delle chiavi da testare.

Possiamo togliere $64$ _chiavi "deboli"_ tra queste figurano le chiavi con tutti 1 o con tutti 0 , o con 28 uni e 28 zeri di seguito.

definite $\mathcal{C}_{DES}, \mathcal{D}_{DES}$ le funzione di [[Cifratura e Decifratura|cifratura e decifratura]] complessive del DES

si ha che  ulteriore riduzione viene dal fatto che $$\mathcal{C}_{DES}(m,k)=c \implies \mathcal{C}_{DES}(\bar{m},\bar{k} ) =\bar{c}$$dove l operazione $\bar{\cdot}$ è l operazione di [[Operazioni logiche|complemento]]. L operazione di complementazione nel cifrario influenza solo l output di _XOR_ e della S-box ma 
- lo _XOR_ ha la stessa uscita se entrambi gli ingressi sono complimentati   
- per la prima proprietà lo $S$-box riceve lo _stesso input_ di non fare il complemento e di conseguenza dara lo _stesso output_.
da queste proprietà notiamo che nella _successiva fase_ $i$ avremo  il blocco il valore di  $S[i-1]$  complimentato mentre $D[i-1]$ sara diretto e quindi il valore dello _XOR_ finale sarà _complementato_

su questa proprietà il _crittoanalista_ puo fare un attacco di tipo [[Tipologia di attacchi ai cifrari|Chosen plain text]].
	si procura due coppie _messaggio crittogramma_ $\langle m,c_1\rangle,\langle \bar{m},c_2\rangle$ e si prova a eseguire le funzione di crittazione $\mathcal{C}_{DES}(m,k)$ se abbiamo che 
- $\mathcal{C}_{DES}(m,k) =c_{1}$ allora _probabilmente_ $k$ è la chiave perché general la coppia $\langle m,c_1\rangle$
- $\mathcal{C}_{DES}(m,k) =\bar{c_2}$ allora _probabilmente_ $\bar{k}$ è la chiave perché genera la coppia $,\langle \bar{m},c_2\rangle$.
il probabilmente è dovuto al fatto piu chiavi possono generare un dato $c$ partendo da $m$.
se entrambi i casi falliscono allora significa che ne $k$ ne $\bar{k}$ sono la chiave e di fatto ci basta controllare una delle due chiavi.
cosi facendo stiamo dimezzando le chiavi che dobbiamo controllare portando lo spazio delle chiavi _da esplorare_ a $2^{55}$

altre due tipi di attacchi al DES sono 
- _Critto analisi differenziale_:  è un attacco di tipo _chose plain text_ dove il critto analista ha bisogno di $2^{47}$ coppie $\langle m,c \rangle$ con delle particolare differenze per poter assegnare delle probabilità a un insieme di chiavi.
	- L impiego di questa tecnica ha mostrato che se le fasi fossero meno di 16 il cifrario sarebbe stato facilmente attaccabile.
- _Critto analisi Lineare_: è un attacco di tipo _chose plain text_ dove si usa una approssimazione lineare della funzione per calcolare alcuni bit e gli altri si fanno attraverso un attacco esauriente. Questa metodologia porta le coppie da analizzare a  $2^{43}$

#### Varianti DES
i vari attacchi possibili al DES son costosi da implementare e quindi poco pratici, sono _puramente accademici_. . 
il DES è anche stato violato in meno di 24h da un calcolatore costruito a hoc e molto costoso chiamato _RIVYERA_ .
questo ha  fatto sorgere abbastanza dubbio per far nascere varianti piu sicure del DES.

##### Scelta indipendente
ogni _sotto chiave_ viene scelta indipendentemente portando i bit della chiave a $48 \times 16 = 768$ in questo modo l _attacco differenziale_ richiede $2^{61}$ coppie $\langle m,c \rangle$ 
questa variante è poco pratica per la lunghezza della chiave che deve essere generata dal utente

##### Cifratura multipla
Si Concatenano piu copie di DES con chiavi diverse dando cosi origine ad un _cifrario composito_. 
questo non implica necessariamente che la sicurezza aumenti ma a differenza del [[Cifrario di Cesare|Cifrario di Cesare]] nel caso del DES questo è vero.
matematicamente abbiamo che
_Siano_ $k_1, k_2$ due chiavi arbitrarie 
_vale_ che
$$\mathcal{C}_{DES}(\mathcal{C}_{DES}(m,k_{1}),k_{2}) \not =\mathcal{C}_{DES}(m,k_{3}) \ \ \ \forall m,k_{3}$$

Pero due chiavi da $56$ bit non ne fanno una da $112$ siccome si puo utilizzare una semplice strategia per ridurre il numero di chiavi da controllare.  l attacco è chiamato _meet in the middle_ ed si parte dalla osservazione che data una coppia $\langle m,c\rangle$
$$c=\mathcal{C}_{DES}(\mathcal{C}_{DES}(m,k_{1}),k_{2}) \ \ \  \ \ \ \ \mathcal{D}_{DES}(c,k_{2})=\mathcal{C}_{DES}(m,k_{1}) $$
e quindi posso fare 
1. per ogni $k_{1}$ si calcola $\mathcal{C}_{DES}(m,k_{1})$ e la salvo in una tabella
2. per ogni $k_{2}$ si calcola $\mathcal{D}_{DES}(c,k_{2})$ e si cerca nella tabella.
il costo complessivo è $O(2^{n}+2^{n})=O(2^{n+1})$ dove $n$ è il numero di bit della chiave.  Quindi con questa strategia devo provare solo _il doppio_ delle chiavi invece che $2^{112}$  


Da queste osservazioni si sono sviluppate delle varianti che soffrono comunque per questo attacco ma aumentano comunque la sicurezza ottenuta

le varianti _triple DEA_ (_triple data encryption algorithm_)
- 2TDEA: dove si utilizzano 2 chiavi 
- 3TDEA: dove si utilizzano 3 chiavi 
in queste varianti date $k_1, k_2,k_3$ con eventualmente $k_3=k_{1}$ _chiavi indipendenti_ le funzioni di [[Cifratura e Decifratura|Cifratura e Decifratura]] sono 
$$
\begin{array}{}
\mathcal{C}_{DES}(\mathcal{D}_{DES}(\mathcal{C}_{DES}(m,k_{1}),k_{2}),k_{3})  &  =  & c \\
\mathcal{D}_{DES}(\mathcal{C}_{DES}(\mathcal{D}_{DES}(c,k_{1}),k_{2}),k_{3})  & = & m 
\end{array}
$$
anche qui il gain di sicurezza non è pari alla somma delle chiavi si arriva solo alla sicurezza di una chiave a $112$
si puo strutturare un attacco _meet in the midle_ osservando che $$\begin{array}{}
\mathcal{D}(c,k_{3})=\mathcal{D}_{DES}(\mathcal{C}_{DES}(m,k_{1}),k_{2}) \\
\mathcal{C}_{DES}(\mathcal{D}_{DES}(c,k_{3}),k_{2})=\mathcal{C}_{DES}(m,k_{1})
\end{array}
$$e data una coppia $\langle m,c\rangle$ procedendo
1. per ogni $k_{1}$ si calcola e si scalda $\mathcal{C}_{DES}(m,k_{1})$ in una tabella
2. per ogni coppia di chiavi $k_{2},k_{3}$ si calcola $\mathcal{C}_{DES}(\mathcal{D}_{DES}(c,k_{3}),k_{2})$ e si cerca nella tabella
il costo complessivo è $O(2^{n}+2^{n}\cdot2^{n})=O(2^{2n})$ dove $n$ è il numero di bit della chiave e  _quindi_ $2^{112}$ e questo risultato vale anche se $k_{3}=k_{1}$


queste varianti preservano la _compatibilità_ con il DES originale siccome con $k_{1}=k_{2}= k_{3}$ abbiamo che queste varianti si comportano in modo identico al _DES_ ma più costoso


