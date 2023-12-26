---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario simmetrico AES
---
è un [[Cifrari a chiave Simmetrica|cifrario simmetrico]] che è stato costruito in sostituzione al [[Cifrario simmetrico DES|DES]]
dopa una selezione dal NIST è stato scelto il cifrario *__Rijndael__* che oggi è chiama _AES_

#### Definizione
lo _AES_ è un cifrario a _blocchi_ che si _basa su fasi_

nel algoritmo ogni _messaggio_ viene diviso in blocchi da  128, 192 e 256 bit e puo utilizzare chiavi da 128, 192 e 256 bit queste entrambi estendibili a multipli di 32.
lo Standard si riferisce a blocchi da 128 e chiavi 128, 192 e 256 bit 
anche il numero di fasi _cambia_ a secondo della dimensione della chiave e sono 10,12 e 14 rispettivamente.
![[IMG_0615.jpeg]]
ogni fase impiega una _chiave locale_ generata dalla chiave segreta e una _chiave iniziale_ per la prima fase. Tutte queste sotto chiavi sono generate tramite un processo  di selezione ed espansione.

_blocchi_ e _sottochiavi_ sono organizzati in matrici di dimensione variabile a seconda della dimensione del blocco ma lo standard è $128$ bit. divisi in $16$ byte $b_{i,j}$
![[Pasted image 20230709180943.png]]


l organizzazione generale segue come
_trasformazione iniziale_: 
	si generano le _chiavi locali_ a partire dalla chiave del cifrario. questo viene fatto ricorsiva mente aggiungendo 40 colonne alla matrice delle chiavi
	- $40$ perchè se ne usano $4$ ad ogni fase e queste sono 10	![[IMG_0617.jpeg]]
	  ogni colonna viene calcolata come $$
	\begin{cases}
	 W[i]= W[i-4] \oplus W[i-1] &   \\
	 W[i]= W[i-4] \oplus T(W[i-1]) & if & i \text{ multiplo di 4} 
	\end{cases}
	  $$
	  dove $T(W[i])$ è una trasformazione non lineare che segue come:
   1. _Shift ciclico_ di una posizione verso l alto 
   2. ad ogni byte viene sostituito con $b_{i}’=S(b_{i})$ dove $S$ è $S$-box 
   3. al byte $b’_{1}$ si aggiunge in _XOR_ un numero _RC_ che cambia per ogni fase secondo la regola $$\begin{array}{}RC_1 & = & 1 \\RC_{i}& = & 2RC_{i-1}\end{array}$$
	  e la _chiave locale_ risultate è$$
	  k(i)=W[4i],W[4i+1],W[4i+2],W[4i+3]
	  $$
	il messaggi $m$ è caricato nella matrice $B$ è ogni bit viene messo in [[Operazioni logiche|XOR]]  con i bit della _chiave iniziale_ $k(0)$

vene poi eseguita 10 volte la procedura sotto descritta
_organizazione di una fase_:
1. ogni Byte di $B$ è trasformato mediante una $S$-box
	- usa criteri algebrici che garantiscono la _non linearità_ tra input e output, e ogni _byte_  di $B$ è trasformato come $a_{i,j} = S(b_{i,j})$, 
	- l $S$ box è una matrice $16 \times 16$ ed è a 8 bit di ingresso e 8 di uscita. contiene una permutazione degli  [[Rappresentazione di oggetti matematici con sequenze|interi rappresentabili]] con 8 bit, ovvero quelli da $0\leq v < 256$ 
	- l Input della $S$-box è usato per selezionare _riga e colonna_ e l output e la rappresentazione del numero l incrocio delle due
	- ![[IMG_0618.jpeg]]
2. viene applicata uno _shift ciclico_ sulle righe della matrice ottenuta.
	- ogni byte viene shiftato a sinistra di $i$ posizioni dove $i$ è il numero di riga partendo da 0
	- quindi la prima riga resta inalterata, la seconda viene shiftata (sui Byte) di 1 la terza di 2 e la quarta di 3 posizioni
3. le colonne vengono trasformate con un operazione algebrica
	- ogni colonna vista come vettore _viene moltiplicata_ per una matrice $M$ $4 \times 4$ di _byte_ dove la moltiplicazione è fatta in$\mod 2^{8}$ e le addizioni in $\mod  2$
		- la matrice è scelta in modo da _influenzare tutti i bit_
		- questa parte insieme allo _shift delle righe_ garantisce [[Criteri di Shannon per i cifrari|diffusione]] totale dopo sole due fasi.
4.  ogni bit della matrice risultante è posto in _XOR_ con i bit della _chiave locale_ corrispettiva alla fase
	-  $b_{ij} = b_{ij} \oplus k_{ij}$

![[IMG_0616.jpeg]]
![[Pasted image 20230709184159.png]]
#### Vulnerabilità
esisono attacchi più volevi di quello esauriente se le fasi sono 6 o meno ma con 7  questo attacco non funziona più

Ad oggi non sono state trovate vulnerabilità teoriche per questo cifrario.

#### Problematiche
essendo un _cifrario a blocchi_ soffre del problema generare dei cifrari a blocchi risolto con il [[Cifrario a Composizione di blocchi|CBC]]

