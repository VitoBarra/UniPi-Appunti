---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Funzioni Hash One-Way
---
Sono _particolari_ tipi di [[Funzioni Hash|funzioni hash]] $h:X\rightarrow Y$ che hanno in piu le  seguenti proprietà

1. ogni elemento $\forall  x \in X$ è [[Complessita|computazionalmente facile]] calcolare $y=h(x)$
2. (_One-way_) per la _maggior parte_ degli elementi $y \in Y$ è computazionalmente difficile determinare un $x$  tale che $h(x)=y$ 
3. (_string Collision-resistant_) è _computazionalmente difficile_ determinare $x',x''$ tale che $$h(x')=g(x'')$$
l avere queste proprietà le rende adatta ad applicazioni Crittografiche. Queste applicazione dovranno gestire il _problema delle collisioni_. Un modo è con la struttura dati [[Hash Table|Hash Table]] altre proprietà che devono soddisfare per essere buone _funzione hash one way_ per applicazioni crittografiche sono
1. prendono in input una valore di _qualsiasi grandezza_
2. danno in output un valore di una _grandezza fissa_
3. (_Weak collision resistent_) dato un blocco $x’$ deve essere difficile trovare un $x’’$ tale che  $x’’ \not =x’ . h(x’) = h(x’’)$
4. deve superare i test di [[Generatori di numeri Pseudo Casuali#Test statistici per la casualità|pseudo-randomicita]]





### Accenni storici 
_Message digest versione_ 5 (_MD5_) una delle prime _funzioni hash One way_ che prende in input blocchi da 512 bit e restituisce valori a 128 _bit_
	MD5 questa è stata ritirata  nel 2004 per problemi di debolezza rispetto alla proprietà _Collision-resistenz_
la famiglia _Secure Hash Algorithm_ (_SHA_) sono al momento le più usate. sono nate Piu versioni tra cui SHA0 nata per competere con _Message digest versione_ 5 (_MD5_) che è stata ritirata per un punto di debolezza e SHA1 che è stato uno standard fino al 2010 e poi è stata ritirata per debolezze di interesse più teorico che pratico nonostante questo è ancora molto usata.


### SHA1
La funzione _SHA_ è una _funzione hash one-way_ ed è una funzione che opera su sequenze fino a $2^{64}-1$ bit e produce _immagini_ a  160 bit

 la funzione SHA1 lavora con blocchi da 160 _bit_ messi in 5 registri da 32 _bit_ denominati A,B,C,D,E che alla prima iterazione ha dei valori _prefissati e publici_

i _messaggi_ $m$ su cui si sta eseguendo la funzione di _SHA_ se non sono già lunghi un numero di bit multiplo di 512 gli si aggiunge un _padding_.

la struttura di una singola fase $i$ della funzione SHA1 è la seguente
	![[Pasted image 20230813213859.png]]
dove:
- $S$ Box realizza una _funzione non lineare_ con $92$ bit di  input  e $32$ d output
- $R1,R2$ sono due _shift ciclici_ di $n$ posizioni dove $n$ vari ad ogni iterazione $i$
- $K$ è una _quantità costante_ che cambia ad ogni interazione $i$
- $M$ è un blocco del messaggio da $32$ bit  ottenuto tagliando e rimescolando il messaggio
- il segno $+$ indica l addizione $\mod 2^{32}$ 
il _numero di iterazioni_ dipende dalla lunghezza del messaggi, ad ogni ciclo si leggono $32$ _bit_ del messaggio e le iterazioni finiscono quando il _messaggio viene letto tutto_.


In Piu per una qualsiasi _funzione Hash one-way_ e in particolare per quelle della famiglia _SHA_ si puo sempre estende la lunghezza della striga generata (chiamata _immagine_). questo è fatto come
_sia_ T la sequenza su cui si vuole eseguire la funzione di hash $h$
Ponendo $D_{0} \leftarrow T$ e calcolando $D_{i}\leftarrow h(D_{i-1})\cdot D_{i-1}$ dove la $\cdot$ è la concatenazione. e deve $h(D_{i-1})$ ha lunghezza $\ell$ e $D_{i-1}$ ha _lunghezza crescente_ con $i$ 
si ottiene cosi un immagine complessiva di lunghezza $\ell \times k$ _concatenando le sequenza_ $h(D_{0})\dots h(D_{k-1})$

in mole applicazioni poter concatenare la funzione SHA aumenta la sicurezza.
