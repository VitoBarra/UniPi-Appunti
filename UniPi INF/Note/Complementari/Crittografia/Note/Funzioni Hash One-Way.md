---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Funzioni Hash One-Way
---
Sono particolari tipi di [[Funzioni Hash|funzioni hash]] che hanno le seguenti proprietà
1. ogni elemento $\forall  x \in X$ è [[Complessita|computazionalmente facile]] calcolare $f(x)$
2. (_One-way_) per la _maggior parte_ degli elementi $y \in Y$ è computazionalmente difficile determinare un $x$  tale che $f(x)=y$ 
3. (_Claw-free_) è computazionalmente difficile determinare $x',x''$ tale che $f(x')=f(x'')$

l avere queste proprietà le rende adatta ad applicazioni Crittografiche



### Accenni storici 
_Message digest versione_ 5 (_MD5_) una prima versione di [[Funzioni Hash|funzioni hash]] One way che pero è stata ritirata per problemi di debolezza rispetto alla proprietà _Claw-free_
famiglia _Secure Hash Algorithm_ (_SHA_) sono al momento le più usate. sono nate Piu versioni tra cui SHA0 nata per competere con _Message digest versione_ 5 (_MD5_) che è stata ritirata per un punto di debolezza e SHA1 che è stato uno standard fino al 2010 e poi è stata ritirata per debolezze di interesse più teorico che pratico nonostante questo ù è ancora molto usata.


### SHA1
La funzione SHA è una funzione hash one-way ed è una funzione che utilizza dei blocchi a 160 bit contenuti in un  buffer ed è un funzione a fasi cosi come il [[Cifrario a chiave Simmetrica DES|DES]] e l [[Cifrario a chiave Simmetrica AES|AES]] 

 la funzione SHA1 lavora con 5 registri da 32 bit denominati A,B,C,D,E che alla prima iterazione ha dei valori prefissati.

i _messaggi_ $m$ su cui si sta eseguendo la funzione di ASH se non sono già lunghi un numero di bit multiplo di 512 gli si aggiunge un _padding_.

la struttura di una singola fase $i$ della funzione SHA1 è la seguente
	![[Pasted image 20230813213859.png]]
	dove l $S$ Box realizza una funzione non lineare con $92$ bit di  input  e $32$ d output, $R1,R2$ sono due rotazioni cicliche e $K$ è una quantità costante che dipende dal numero di ciclo $i$, $M$ è un blocco del messaggio da $32$ bit e il segno $+$ indica l addizione $\mod 2^{32}$ 

In Piu per una qualsiasi funzione Hash one-way e in particolare per quelle della famiglia HAS si puo sempre estende la lunghezza della striga generata (chiamata _immagine_). questo è fatto come
_sia_ T la sequenza su cui si vuole eseguire la funzione di hash $h$
Ponendo $D_{0} \leftarrow T$ e calcolando $D_{i}\leftarrow h(D_{i-1})\cdot D_{i-1}$ dove la $\cdot$ è la concatenazione. e deve $h(D_{i-1})$ ha lunghezza $\ell$ e $D_{i-1}$ ha _lunghezza crescente_ con $i$ 
A questo si può ottenere un immagine complessiva di $T$ di lunghezza $\ell \times k$ _concatenando le sequenza_ $h(D_{0})\dots h(D_{k-1})$

in mole applicazioni poter concatenare la funzione HAS aumenta la sicurezza.
