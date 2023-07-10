---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario a chiave Simmetrica AES
---
è un [[Cifrari a chiave Simmetrica|cifrario simmetrico]] che è stato costruito in sostituzione al [[Cifrario a chiave Simmetrica DES|DES]]
dopa una selezione dal NIST è stato scelto il cifrario *__Rijndael__* che oggi è detto AES

#### Definizione
lo AES è un cifrario che si basa su Fasi

nel algoritmo ogni messaggio viene diviso in blocchi da  128, 192 e 256 bit e puo utilizzare chiavi da 128, 192 e 256 bit queste entrambi estendibili a multipli di 32.
lo Standard si riferisce a blocchi da 128 e chiavi 128, 192 e 256 bit 
anche il numero di fasi _cambia_ a secondo della dimensione della chiave e sono 10,12 e 14 rispettivamente.
ogni fase impiega una _chiave locale_ generata dalla chiave segreta e una _chiave iniziale_ per la prima fase. Tutte queste sotto chiavi sono generate tramite un processo  di selezione ed espansione.

blocchi e _sottochiavi_ sono organizzati in matrici di dimensione variabile a seconda della dimensione del blocco ma lo standard è 128 bit. divisi in $16$ byte $b_{i,j}$
![[Pasted image 20230709180943.png]]


l organizzazione generale segue come
_trasformazione iniziale_: il messaggi $m$ è caricato nella matrice B è ogni bit viene messo in [[Operazioni logiche|XOR]]  con i bit della _chiave iniziale_ vene poi eseguita 10 volte la procedura sotto descritta

_organizazione di una fase_:
1. ogni Byte di $B$ è trasformato mediante una $S$-box
	- usa criteri algebrici che garantiscono la _non linearità_ tra input e output, e ogni byte  di $B$ è trasformato come $b_{i,j} = S(b_{i,j})$
2. viene applicata uno _shift ciclico_ sulle righe della matrice ottenuta.
	- ogni byte viene shiftato a sinistra di $i$ posizioni dove $i$ è il numero di riga partendo da 0
	- quindi la prima riga resta inalterata, la seconda viene shiftata (sui Byte) di 1 la terza di 2 e la quarta di 3 posizioni
3. le colonne vengono trasformate con un operazione algebrica
	- ogni colonna viene moltiplicata per una matrice $M \ \in \mathbb{N}^{4}$ dove la moltiplicazione è fatta in$\mod 2^{8}$ e le adizioni sono fatte come _XOR_ . la matrice è scelta in modo da _influenzare tutti i bit_
4.  ogni bit della matrice risultante è posto in _XOR_ con i bit della chiave locale.
	-  $b_{ij} = b_{ij} \oplus k_{ij}$
![[Pasted image 20230709184159.png]]
#### Vulnerabilità
ad oggi non sono state trovate vulnerabilità teoriche per questo cifrario.


