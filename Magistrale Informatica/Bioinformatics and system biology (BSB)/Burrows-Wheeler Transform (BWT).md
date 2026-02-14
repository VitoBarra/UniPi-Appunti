---
Course: "[[Teoria del informazione (TDI)]]"
tags:
  - TDI
Area:
topic:
SubTopic:
---

# Burrows-Wheeler Transform (BWT)
La **trasformazione di Burrows–Wheeler** è una **permutazione** reversibile dei caratteri di una [[Stringhe|stringa]] $T$ terminata da simbolo $\$$ con $\$$ minimo unico nell’[[alfabeto|alfabeto]]. Questa trasformazione è usata come pre-processing per permettere buone condizioni per gli [[Algoritmi di compressione|algoritmi di compressione]]
la procedura di trasformazione segue come: 
1. si costruisce una matrice tutte le rotazioni distinte di $T$ ottenute spostando ciclicamente il primo carattere in fondo
2. si [[Ordinamenti|ordinano]] le righe lessograficametne che coincide con l’ordinamento dei suffissi grazie alla presenza di $\$$ che interrompe i confronti.
3. si prende l ultima colonna dal alto verso il basso ottenendo la  **Burrows–Wheeler matrix** (BWT)
La **BWT** ottenuta è quindi una permutazione dei caratteri di $T$.
![[IMG - Burrows-Wheeler Transform (BWT).png]]
L’effetto principale è l’aggregazione di caratteri uguali in run contigue. Ordinando per rotazioni si ordinano i caratteri in base al contesto destro, cioè al testo che li segue in $T$. Caratteri con contesti simili tendono a essere vicini, generando run compressibili. La compressione sfrutta codifiche come [[run–length encoding|run–length encoding]]: una sequenza di $k$ caratteri identici è rappresentata da coppia (carattere, conteggio). La BWT non comprime di per sé ma riorganizza $T$ in forma più comprimibile.

La **Burrows–Wheeler matrix** ha struttura analoga al [[Suffix array|suffix array]] ![[IMG - BWT e SA.png]]
possiamo usare questo fatto per costruire direttamente la **BWT**, ovvero l ultima colonna 
Se $SA$ è il suffix array di $T$, la **BWT** si ottiene come$$\begin{cases}
BWT[i]=T[SA[i]-1]  & if &  SA[i]> 0 \\
BWT[i]=\$  &  if &  SA[i]= 0
\end{cases}
$$Questa costruzione evita di materializzare tutte le rotazioni.


Per permettere l inversione si introduce un **ranking dei caratteri**: per ogni carattere $c$ e posizione $i$ si definisce un rank che li annota
- **T-ranking**: ogni carattere $c$ in $T$ è annotato con il numero di occorrenze precedenti di $c$. ![[IMG - T-ranking in BWT.png]]
- **B-ranking** i rank di uno stesso carattere sono in ordine crescente scorrendo $L$ e $F$ ![[IMG - B-ranking.png]]
 
la **BW matrix** soddisfa la l **LF mapping** che afferma che tra ultima colonna $L$ e prima colonna $F$ si ha che l’$i$-esima occorrenza di $c$ in $L$ corrisponde all’$i$-esima in $F$; ovvero condividono il **rank** qualunque esso sia.![[IMG - LF mapping.png]]

Questa proprietà viene dal fatto che sono entrambi ordinate dal suo contesto destro. Nella seconda matrice il contesto sembra a sinistra ma la stringa va considerata come array circolare quindi è come se fosse a destra, infatti l ordinamento va da sinistra verso destra![[IMG - right-context sort perche funziona il FL-mapping.png]]


Usando il **B-ranking**, $F$ è partizionata in blocchi contigui [[Ordinamenti|ordinati]] lessicograficamente per carattere per l’[[alfabeto|alfabeto]] ordinato $\Sigma$ con $\$$ minimo, $F$ è $\$$ seguito dal blocco di tutti gli $c\in\Sigma\setminus\{\$\}$ in ordine crescente; nel blocco di $c$ i ranks crescono di $1$ scorrendo verso il basso.

Sia $occ(c)$ il numero di occorrenze di $c$ in $T$ (quindi anche in $F$). Definisco la funzione cumulativa $$C(c)=\sum_{d\in\Sigma,\ d<c} occ(d)$$cioè il numero totale di caratteri in $T$ strettamente minori di $c$ (incluso $\$$). Allora il blocco di $c$ in $F$ occupa esattamente le righe con indici $[C(c),\ C(c)+occ(c)-1]$, e la riga che inizia con il **carattere** $c$ avente **B-rank** $i$ è $$row_F(c,i)=C(c)+i  \ \ \ \ \ \ 0\le i<occ(c)$$In particolare, la ricerca dell’indice della riga che inizia con $(c,i)$ si riduce a un accesso a $C(c)$ e a una somma, senza dover materializzare $F$ il che lo rende un algoritmo di [[Complessita|complessità]] $O(1)$



L’inversione della BWT usa la **LF-mapping** per ricostruire $T$ da destra verso sinistra sfruttando solo $L$ e le informazioni cumulative $C$. Si assume l’uso del **B-ranking**, quindi ogni carattere in $L$ ha implicitamente un rank crescente all’interno del proprio blocco.

Si inizializza dalla riga $0$ di $F$, che contiene sempre $\$$. Poiché ogni riga della matrice è una rotazione di $T$, il carattere in $L[0]$ è quello che precede $\$$ in $T$, cioè l’ultimo carattere di $T$ prima del terminatore. Questo carattere viene scritto come ultimo carattere ricostruito.

Dato l’indice corrente di riga $i$, si considera il carattere $c=L[i]$ e il suo rank in $L$, indicato come $rank_L(i,c)$ (numero di occorrenze di $c$ in $L[0..i]$ meno uno). La riga successiva da visitare è determinata dalla funzione
$$LF(i)=C(c)+rank_L(i,c)$$
che fornisce l’indice della riga in $F$ che inizia con l’occorrenza di $c$ con quel rank. Il carattere in $L[LF(i)]$ è il carattere che precede $c$ in $T$. Iterando questa procedura si attraversano tutte le posizioni della rotazione che contiene $\$$, ricostruendo i caratteri di $T$ in ordine inverso.

L’algoritmo termina quando si ritorna alla riga contenente $\$$ in $L$, oppure dopo $|T|$ iterazioni. Se i caratteri raccolti lungo il percorso sono $c_{|T|-1},c_{|T|-2},\dots,c_0$, la stringa originale è $T=c_0c_1\dots c_{|T|-1}$.

Per l’inversione non è necessario memorizzare esplicitamente $F$: la sua struttura è implicita nei valori cumulativi $C(c)$. È sufficiente mantenere $L$ e una struttura che consenta di calcolare $rank_L(i,c)$; una realizzazione ingenua usa un array di rank di lunghezza $|T|$, mentre strutture compatte permettono di ottenere $rank$ e $C$ con spazio sublineare mantenendo tempo di accesso $O(1)$ per iterazione.
![[IMG - processo di inversione BWT.gif]]
un altro modo per visualizarlo è il seguente ![[IMG - inversion Burrows-Wheeler Transform (BWT) rolldout.png]]



![vidoe](https://www.youtube.com/watch?v=4n7NPk5lwbI))


