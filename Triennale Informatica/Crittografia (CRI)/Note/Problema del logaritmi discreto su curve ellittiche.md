---
Course: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Problema del logaritmi discreto su curve ellittiche
---
il problema del _logaritmo discreto su curve ellittiche_  è un _problema_ che si basa sulle definizione di _somma_ delle [[Curve Ellittiche|curve Ellittiche]]  

Il problema è _analogo_ a quella del [[Funzioni One-Way Trapdoor|logaritmo discreto del algebra modulare]] e consiste Invertire la _moltiplicazione_ per $k$ di un punto $P$ una una _curva ellittica_, Ovvero dato $P$ e dato $Q =kP$ voglio sapere il valore di $k$ 
il numero $k$ è detto _logaritmo in base $P$ di $Q$_ 

calcolare $Q$ conoscendo $P$ e $k$ è un problema computazionale _facile_, mentre calcolare $k$ conoscendo solo $P$ e $Q$ è un problema intrattabile siamo quindi davanti ad una [[Funzioni One-Way|funzione One-Way]] e quindi questo problema è utilizzabile a scopi crittografici.

### Calcolare velocemente $Q$
Possiamo fare il calcolo di $Q =kP = P+\dots+P$ ($k$ volte)  _velocemente_ utilizzando un metodo analogo al [[Algoritmo delle Quadrature successive o esponenziazione veloce|metodo di esponenziazione veloce]].
Possiamo quindi calcolare $Q$  con $\Theta(\log k)$ _raddoppi_ e $O(\log k)$ _somme_.

per fare ciò si riscrive $k$ [[Rappresentazione di oggetti matematici con sequenze|rappresentandolo in binario]] come $$k = \sum^{t}_{i=0}k_{i}2^{i}$$ottenendo cosi la _stringa_ $k_{t}\dots k_{1}k_{0}$ con $t = \lfloor \log_{2} k\rfloor$

si calcolano in _sequenza_ $2P,4P,\dots{2}^{t}P$ ognuno [[Curve Ellittiche#Definizione di somma|raddoppiando]] sempre il precedere e partendo da $P$, Questo procedimento ha [[Complessita|complessità]] $\Theta(\log k)$

e in fine si calcola $Q$ come 
$$Q =\sum_{i=0}^{t} k_{i}2^{i}P$$
ovvero vado a sommare soltanto dove $k_{i}=1$ mentre il resto si ignora siccome $k_{i}=0$ e non viene sommato, abbiamo quindi che le somme da fare sono $O(\log k)$

la [[Complessita|complessità]] totale e quindi $\Theta(\log k)+O(\log k)$



### Difficoltata nel calcolo
tutti gli algoritmo noti fin ad ora hanno complessità almeno esponenziale
>[!question]-
>dimostrazione che il calcolo di $k$ è un problema intrattabile, non fa parte del corso da aggiungere per curiosità