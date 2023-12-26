---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario di ElGamal su curve ellittiche
---
il _Cifrario di ElGamal su curve ellittiche_ è [[Cifrari a chiave Asimmetrica|cifrario a chiave assimetrica]] la cui versione che si basa sul algebra modulare è chiamata cifrario a chiave [[Cifrario asimmetrico ElGamal|pubblica ElGamal]].
questo si basa sul idea di scambiare messaggi direttamente sulla [[Curve Ellittiche|curva ellittica]], ovvero 

_Sia_ $m$ un messaggio codificato con in un _numero intero_ questo può essere trasformato in un _punto sulla curva_, questo punto può essere trasformato ulteriormente in un _altro punto sulla curva_ che sarà usato come testo _cifrato_.


per trasformare un messaggi in un punto su una [[Curve Ellittiche|curva ellittica]] non si conoscono algoritmi di [[Complessita|complessita]] polinomiale, ma esistono degli [[Algoritmi Randomizzati|algoritmi randomizati]] che riescono a risolvere questo problema. Uno di questi è l [[Algoritmo di Koblitz]]


### Algoritmo per lo scambio di messaggi
per scambiare _messaggi_ direttamente sulla [[Curve Ellittiche|curva ellittica]] si eseguono i seguenti passi

Si sceglie _pubblicamente_:
- una [[Curve Ellittiche]] _pirma_ $E_{p}(a,b)$ 
-  un punto $B$ della curva con [[Curve Ellittiche#ordine di un punto|ordine del punto]] $n$
- un intero $h$ da usare nel algoritmo di [[Algoritmo di Koblitz|Algoritmo di Koblitz]]

ogni utente $U$ genera la propria coppia chiave _pubblica e privata_ scegliendo un [[Generatori di numeri Pseudo Casuali|numero casuale]] $n_{u}<n$  e  calcola $P_{u}=n_{u}B$ si avrà
$$k[pub]=\langle P_{u}\rangle  \ \ \ \ \ \ k[prv]= \langle n_{U}\rangle$$

#### Cifratura  
1. _mitt_ trasforma $m$ in un punto sula curva $$P_{m} = Kob(m)$$dove $kob(m)$ è l  [[Algoritmo di Koblitz|Algoritmo di Koblitz]]
2. sceglie un intero casuale $r<n$ e calcolare i due punti $$V=rB \ \ \ \ \ \ \ \ \ \ \ W=P_{m}+rP_{D}$$ dove $P_{D}$ è la chiave pubblica di _dest_.
3. _mitt_ manda a _dest_ la coppia di punti $\langle V,W \rangle$

#### Decifratura 
_dest_ riceve la coppia $\langle V,W \rangle$ e ricostruisce il punto $P_{m}$ con la sua _chiave privata_ $u_{D}$, calcolando 
$$W - n_{D}V = P_{m}$$
e poi riconvertirà il punto nel _messaggio_ originale $m$
##### Correttezza
$$
\begin{array}{}
W-n_{D}V & = &  \\
P_{m}+rP_{D}-n_{D}(rB)  & = \\
P_{m}+rn_{D}B-n_{D}rB  &  =   \\
 P_{m}
\end{array}$$



### Sicurezza
Per risalire al _messaggio_ il crittoanalista sapendo $E_{p}(a,b)$ e il punto $B$ e l intero $h$ deve intercettare la coppia $\langle V=rB,W =P_{m}+rP_{D}\rangle$ e riuscire a calcolare $r$ dai valori di $B$ e $rB$ ovvero deve risolvere il problema del [[Problema del logaritmi discreto su curve ellittiche]] che è una [[Funzioni One-Way Trapdoor|funzione one way trap-dor]]
una volta trovato $r$ puo calcolare 
$$
\begin{array}{}
W-rP_{D} & = \\
 P_{m}+rP_{D}-rP_{D} & = &  P_{m}

\end{array}
$$


