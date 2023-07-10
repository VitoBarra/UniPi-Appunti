---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario a chiave Simmetrica DES
---
il _Data Encryption Standard_ (DES) è un [[Cifrari a chiave Simmetrica|cifrario a chiave simmetrica]] pensato per comunicazione di massa quindi di messaggi _non classificati_


#### Definizione
il DES ha la seguente struttura. 

- il messaggi $m$ è suddiviso in blocchi tutti lunghi $64$ bit
- la cifratura e la decifratura avviene attraverso $r$ fasi successive dette _round_ . nel implementazione classica $r=16$
- la chiave $k$  e composta da $b$ _byte_ di cui per ogni byte 7 sono scelti arbitrariamente e l ottavo è un [[Algoritmo di partia per il controllo degli errori|bit di parità]]
- Dalla chiave vengono create $r$ sottochiavi $k[0],k[1],\dots,k[r-1]$
- nel cifrario _sia_ $i$ la fase corrente e $i+1$ la fase successiva con $i = 1, \dots,r$
	- per $i=1$  il messaggio viene diviso in due meta sinistra $S$ e destra $D$  
	- per $i=2,\dots,r$$S_{i+1} =D_{i} \ \ \ \ D_{i+1}=f(k[i-1],D_{i},S_{i})$ 
		-  con $f$ una funzione non lineare.
	- finiti gli $r$ round i le due meta vengono scambiate di nuovo e concatenate, producendo il crittogramma $c$
- La decrittazione funziona invertendo il processo prima descritto.

con questo schema abbiamo che tutti i bit del _crittogramma_ dipenda da tutti i bit del messaggio e da tutti i bit della chiave.


#### breakdown ad alto livello
ad alto livello abbiamo che questa è divisa piu parti
_permutazioni iniziali_ : $PI$ permuta i 64 bit del messaggi in chiaro. mentre $T$ cancella i _bit di parità_ e permuta i restanti 56 bit per generare la prima sotto chiave $k[0]$
le permutazioni sono specificate in questa tabella.
![[Pasted image 20230707214636.png]]
_trasformazione centrale_: 
La sequenza permutata da $PI$  viene divisa in un blocco sinistro $S[0]$ e un blocco destro $D[0]$ di $32$ bit ciascuno. 
Su questi due blocchi si eseguono, nelle successive fasi del DES, sedici trasformazioni strutturalmente uguali, ciascuna con una diversa sottochiave $k[i]$ di $56$ bit derivata dalla chiave iniziale k. La i-esima fase riceve in ingresso tre blocchi $S[i − 1], D[i − 1], k[i − 1]$ rispettivamente di 32, 32 e 56 bit, e produce in uscita tre nuovi blocchi $S[i], D[i], k[i]$ che costituiscono l’ingresso alla fase successiva. Dopo l’ultima fase i due blocchi $S[16]$ e $D[16]$ vengono scambiati e concatenati tra loro in un unico blocco di 64 bit da cui si costruirà il crittogramma finale.
_permutazione finale_: PF genera la permutaizone finale
![[Pasted image 20230707195205.png]]
andando ad analizzare cosa succede nella singola fase abbiamo che i componenti sono

_Schift ciflico_: $SC[i]$. La sottochiave $k[i − 1]$ di 56 bit, ricevuta dalla fase precedente, viene suddivisa in due meta di $28$ bit ciascuna. Su ognuna di queste la funzione $SC[i]$ esegue uno _shift ciclico_ verso sinistra di un numero di posizioni definito come segue: $SC[i] = 1$ per $i = 1, 2, 9, 16,$ $SC[i] = 2$ altrimenti. Le due parti cosi traslate vengono concatenate in un unico blocco di 56 bit che costituisce la sottochiave $k[i]$ per la fase successiva.
_Compressione e trasposizione_ CT. Il blocco di 56 bit prodotto dall’operazione precedente viene ulteriormente elaborato per produrre un nuovo blocco di 48 bit utilizzato nel processo di cifratura dei blocchi $S[i−1]$ e $D[i−1]$. La funzione $CT$ esegue una permutazione del blocco e una selezione di 48 bit da esso. la combinazione delle funzioni $SC[i]$ e $CT$ garantisce che in ogni fase venga estratto dalla sottochiave un diverso sottoinsieme di bit per la cifratura. Si calcola che nella cifratura ogni bit della chiave originale $k$ partecipi in media a quattordici fasi

_Espansione e permutazione_ EP. Il blocco $D[i − 1]$ di 32 bit generato nella fase precedente viene espanso a $48$ bit _duplicando_ 16 bit in ingresso e spostandone altri per ottenere un blocco della stessa dimensione di quello estratto dalla sottochiave e poter eseguire lo _XOR_ tra i due. Si incrementa cosi la dipendenza tra ingresso e uscita della fase, poiché i bit duplicati influenzano due delle sostituzioni operate dalla funzione $S$ del blocco seguente.
![[Pasted image 20230707223730.png]]


_Sostituzione S (o S-box)_. Questa funzione costituisce la parte cruciale e “magica” su cui si basa la sicurezza del cifrario. Essa consta di otto sotto funzioni combinatorie $S1, S2,...,S8$  L’ingresso di 48 bit viene decomposto in otto blocchi $B1, B2,\dots,B8$ di 6 bit ciascuno che costituiscono l’ingresso alle sottofunzioni di pari indice. 
Sia $B_{j} = b_1b_2b_3b_4b_5b_6$. Questi bit vengono divisi in due gruppi $b_1b_6$ e $b_2b_3b_4b_5$ che definiscono due numeri $x, y$, con $0 \leq x \leq 3$ e $0 \leq y \leq 15$, utilizzati per accedere alla cella di riga $x$ e colonna $y$ in una tabella che definisce la sottofunzione $S_j$ . Il numero ivi contenuto è compreso tra 0 e 15, ed è quindi rappresentato con 4 bit che costituiscono l’uscita di $S_j$ realizzando una compressione da 6 a 4 bit. Complessivamente gli otto blocchi generano una sequenza di 32 bit. I blocchi $EP$ e $S$ sono studiati in modo che tutti i bit di $D[i−1]$ influenzino l’uscita di $S$, senza di che non sarebbe poi possibile decifrare il messaggio.

![[Pasted image 20230707222422.png]]

_Permutazione_ P. E una permutazione di 32 bit che genera il blocco finale $D[i]$
![[Pasted image 20230707222509.png]]


e mettendo insieme i vari pezzi per ogni fase ho lo schema seguiente. dove $\oplus$ è lo [[Operazioni logiche|XOR]]
![[Pasted image 20230707221817.png]]

tutte le funzione tranne la $S$-box e quindi vale che $f(x) \oplus f(y) =f(x \oplus y)$ infatti tutta la _sicurezza_ del cifrario viene dalla $S$-box

#### Attacchi e vulnerabilità
per analizzare le vulnerabili del cifrario DES si pare dal valutare l attacco esauriente. 
i bit della chiave sono 56 quindi ci sono $|K|=2^{56}$ [[Combinatoria|combinazioni]] ma analizzando la struttura del cifrario si _puo ridurre_ lo spazio delle chiavi da testare.

Possiamo togliere $64$ _chiavi "deboli"_ tra queste figurano le chiavi con tutti 1 o con tutti 0 , o con 28 uni e 28 zeri di seguito.

definite $\mathcal{C}_{DES}, \mathcal{D}_{DES}$ le funzione di [[Cifratura e Decifratura|cifratura e decifratura]] complessive del DES

si ha che  ulteriore riduzione viene dal fatto che $\mathcal{C}_{DES}(m,k)=c \implies \mathcal{C}_{DES}(\bar{m},\bar{k} ) =\bar{c}$ dove l operazione $\bar{\cdot}$ è l operazione di [[Operazioni logiche|complemento]]. L operazione di complementazione nel cifrario influenza solo l output di XOR e della S-box e lo _XOR_ ha la stessa uscita se entrambi gli ingressi sono complimentati, di conseguenza l $S$-box riceve lo stesso input e di conseguenza da lo stesso output.
da queste proprietà notiamo che nel successivo passaggio il blocco XOR riceverà l ingresso $S[i-1]$ complementato e uno diretto permutato da P di conseguenza dara un _output complementato_.

su questa proprietà il _crittoanalista_ puo fare un attacco di tipo [[Tipologia di attacchi per scoprire il messaggio criptato|Chosen plain text]].
si procura due coppie _messaggio crittogramma_ $\langle m,c_1\rangle,\langle \bar{m},c_2\rangle$ e si prova a eseguire le funzione di crittazione $\mathcal{C}_{DES}(m,k)$ se abbiamo che 
- $\mathcal{C}_{DES}(m,k) =c_{1}$ allora _probabilmente_ $k$ è la chiave perché general la coppia $\langle m,c_1\rangle$
- $\mathcal{C}_{DES}(m,k) =\bar{c_2}$ allora _probabilmente_ $\bar{k}$ è la chiave perché genera la coppia $,\langle \bar{m},c_2\rangle$.
il probabilmente è dovuto al fatto piu chiavi possono generare $c$ partendo da $m$.
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
$$\mathcal{C}_{DES}(\mathcal{C}_{DES}(m,k_{1}),k_{2}) \not =\mathcal{C}_{DES}(m,k_{3}) \ \ \ \forall m,k$$
da questa proprietà sono stati sviluppato le varianti _triple DES_ con 2 o 3 chiavi chiamate 2TDEA e 3TDEA (triple data encryption algorithm). 

in queste varianti date $k_1, k_2$ e eventualmente $k_3$ _chiavi indipendenti_ le funzioni di [[Cifratura e Decifratura|Cifratura e Decifratura]] sono 
$$
\begin{array}
\mathcal{C}_{DES}(\mathcal{D}_{DES}(\mathcal{C}_{DES}(m,k_{1}),k_{2}),k_{1})  &  =  & c \\
\mathcal{D}_{DES}(\mathcal{C}_{DES}(\mathcal{D}_{DES}(c,k_{1}),k_{2}),k_{1})  & = & m 
\end{array}
$$
queste varianti preservano la compatibilità con il DES originale siccome con $k_{1}=k_{2}$ abbiamo che queste varianti si comportano in modo identico al DES.





