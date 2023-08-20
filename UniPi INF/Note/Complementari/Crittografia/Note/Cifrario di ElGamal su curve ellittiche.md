---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario di ElGamal su curve ellittiche
---
 il _Cifrario di ElGamal su curve ellittiche_ è [[Cifrari a chiave Asimmetrica|cifrario a chiave assimetrica]] la cui versione base è chiamata cifrario a chiave [[Cifrario ElGamal|pubblica ElGamal]].
questo si basa sul idea di scambiare messaggi direttamente sulla [[Curve Ellittiche|curva ellittica]], ovvero 
_Sia_ $m$ un messaggio codificato con in un _numero intero_ questo può essere trasformato in un _punto sulla curva_, questo punto può essere trasformato ulteriormente in un _altro punto sulla curva_ che sarà usato come testo _cifrato_.


per trasformare un messaggi in un punto su una [[Curve Ellittiche|curva ellittica]] non si conoscono algoritmi di [[Complessita|complessita]] polinomiale, ma esistono degli [[Algoritmi Randomizzati|algoritmi randomizati]] che riescono a risolvere questo problema. Uno di questi è l [[Algoritmo di Koblitz]]


### Algoritmo per lo scambio di messaggi
per scambiare _messaggi_ direttamente sulla [[Curve Ellittiche|curva ellittica]] si eseguono i seguneti passi

Si sceglie pubblicamente una curva ellittica $E_{p}(a,b)$ e un punto $B$ della curva con [[Curve Ellittiche#ordine di un punto|ordine del punto]] $n$ elevato e un intero $h$ da utilizzare nel [[Algoritmo di Koblitz|algoritmo di koblitz]] $Kob(m)$ per la trasformazione dei messaggi in punti sulla curva.

ogni utente $U$ genera la propria coppia chiave pubblica e privata scegliendo un numero casuale $n_{u}<n$  e $P_{u}=n_{u}B$

a questo punto supponendo che _mitt_ voglia mandare un messaggi a _dest_ il processi di cifratura e decifratura avviene come 

_cifratura_:  _mitt_ trasforma $m$ in un punto sula curva $P_{m}$ sceglie un intero casuale $r$ e calcolare i due punti $V=rB$ e $W=P_{m}+rP_{D}$ dove $P_{D}$ è la chiave pubblica di _dest_. _mitt_ manda a _dest_ la coppia di punti $\langle V,W \rangle$

_decifratura_: _dest_ riceve la coppia $\langle V,W \rangle$ e ricostruisce il punto $P_{m}$ con la sua _chiave privata_ $u_{D}$, calcolando $$
\begin{array}{}
W-n_{D}V & = &  \\
P_{m}+rP_{D}-n_{D}(rB)  & = \\
P_{m}+r(n_{D}B )-n_{D}(rB)  &  =   \\
 P_{m}
\end{array}$$e ritrasforma il punto $P_{m}$ nel messaggio $m$


### Sicurezza
Per risalire al _messaggio_ il crittoanalista sapendo $E_{p}(a,b)$ e il punto $B$ e l intero $h$ deve intercettare la coppia $\langle V=rB,W =P_{m}+rP_{D}\rangle$ e riuscire a calcolare $r$ dai valori di $B$ e $rB$ ovvero deve risolvere il problema del [[Problema del logaritmi discreto su curve ellittiche]] che è una [[Funzioni One-Way Trapdoor|funzione one way trap-dor]]


