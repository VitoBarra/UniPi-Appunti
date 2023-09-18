---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Algoritmi di firma digitale su curve ellittiche (ECDSA)
---
è un _algoritmo_ per la [[Protocolli di firma digitale|firma digitale]] basata su [[Curve Ellittiche|Curve Ellittiche]] 

si vuole quindi mandare un messaggio $m$ _firmato_   
Scelta una _curva ellittica prima_ $E_{p}(a,b)$ con $p$ primo e un punto sulla curva $B$ con un ordine $n$ _grande_ e [[Numeri primi|primo]].

sulla curva ogni utente $U$ genera la copia di chiave _pubblica_ e _privata_ come 
1. Seleziona un intero casuale $d \in [1,n-1]$
2. Calcola $Q=dB$
3. $k[pub]= Q,k[prv]=d$

e il protocollo di firma segue come:
_Firma_: l utente _Bob_
1. Seleziona un intero casuale $k \in [1, n-1]$ 
2. Calcola il punto $P = (x_{P}, y_{P}) = k B$ e pone $r = x_{P} \mod n$
	- _Se_ $r = 0$, riparte dal punto 1 
3. Calcola $s = k^{-1} (e + d r) \mod n$, dove
	1.  $d$ è la  chiave privata di _bob_ 
	2.  $k^{-1} \mod n$ è l [[Inverso di un numero in algebra modulare|inverso in modulo]] $n$ del valore $k$
	3. Calcola $e = h(m)$, dove $h$ è una funzione [[Funzioni Hash One-Way|hash crittografica]] 
	- _Se_ $s = 0$, riparte dal punto 1 
4. La firma del messaggio è la coppia $f=\langle r, s\rangle$
_Verifica della firma_:
_alice_ riceve il messaggio formato come $\langle m,f=\langle r, s\rangle\rangle$
1. Verifica che $r,s \in [1, n-1]$ 
2.  Calcola $e = h(m)$ e  $w = s^{-1} \mod n$ 
4. Calcola $u_{1} = e w$ e $u_{2} = r w$
5. Calcola il punto $E = (x_{E} , y_{E}) = u_{1} B + u_{2} Q$
6. _Se_ $E = O$, rifiuta la firma, _altrimenti_ calcola $v = x_{E} \mod n$
7. Accetta la firma se e solo se $v = r$


### Correttezza
Se il messaggio ricevuto da Alice è proprio quello firmato da Bob, allora abbiamo che 
$$s = k^{-1}(e+dr)\mod n$$
quindi  $\implies$
$$
\begin{array}{}
k  & = &  s^{-1}(e+dr)  & \mod n  & = \\
   & = & (s^{-1}e +s^{-1}dr)  & \mod  n  & = \\
 &  =  & (we+wdr) & \mod  n  & =  \\
 & = & (u_{1}+u_{2}d) & \mod  n 
\end{array}$$
osserviamo che 
$$E=u_{1}B+u_{2}Q = u_{1}B+u_{2}dB= (u_{1}+u_{2}d)B = kB$$
quindi risulta
$$kB=u_{1}B+u_{2}Q=E$$
al passo $6$ della _verifica_ si pone 
$$v=x_{E} \mod   n$$
dove $x_{E}$ è l _ascissa_ nel punto $E=(x_{E},y_{E})=u_{1}B+u_{2}Q$
al passo $2$ della _generazione della firma_ si pone invece $$r= x_{P} \mod n$$dove $x_{P}$ è l _ascisse_ del punto  $P=kB$

e siccome  $E=P=kB$ _abbiamo_ che $r=v$ solo se la firma è _corretta_

### Discussione
La verifica della firma è fatta sul valore $r$ (ascissa del punto $kB$), che non dipende dal messaggio firmato 

l valore $s$ della firma dipende invece da $k$, dall’_hash del messaggio_ e dalla _chiave privata_ dell’utente che firma 

$s$ è utilizzato per ricostruire $r$ durante la verifica della firma 

Data la difficoltà del problema del [[Problema del logaritmi discreto su curve ellittiche|logaritmo discreto]] su curve ellittiche, è computazionalmente improponibile recuperare $k$ da $r$, o $d$ da $Q$


### Possibili attacchi
L’intero $k$ deve essere generato casualmente ed essere unico per ciascuna firma; 
In caso contrario, è possibile recuperare la chiave privata $d$

_siano_ $m$ e $m’$ messaggi noti, firmati usando lo stesso $k$ (non noto). Dato che il primo valore della firma, $r$, dipende solo da $k$, risulta:
- firma su $m : (r,s)$
- firma su $m':(r,s')$
_siano_ $e=h(m)e'=h(m')$ si ha che 
- $s= k^{-1}(e+dr)$
- $s'=k^{-1}(e'+dr)$
da cui 
$$
\begin{array}{}
(s-s') & = &  k^{-1}(e+dr)-k^{-1}(e’+dr) \\
	   & = &  k^{-1}e \cancel{ + k^{-1}dr } -k^{-1}e’ \cancel{ - k^{-1}dr } \\
(s-s') & = & k^{-1}(e-e')
\end{array}
$$
da cui il critto analista può trovare 
$$k=\cfrac{e-e'}{s-s'}$$
dato che $s= k^{-1}(e+dr)$ il crittoanalista può infine trovare la chiave privata 
$$d=\cfrac{sk-e}{r}$$
_tutte le operazioni sono in modulo $n$_
