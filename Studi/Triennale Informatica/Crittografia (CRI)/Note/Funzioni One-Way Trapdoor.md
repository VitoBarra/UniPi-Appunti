---
Subject: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Funzioni One-Way Trapdoor
---
Le _funzioni one-way trapdoor_ Sono [[Funzioni One-Way|funzioni One-Way]] che sono pero _facili da invertire_ se si conosce una _informazione in più_  chiamata _chiave_  
il problema del invertire questa tipologia di funzione senza  la _chiave_ o è  della _[[Complessita|classe]]_  $\mathbf{NP-Hard}$ oppure non si sa ancora un _algoritmo polinomiale_.


### Esempi di funzioni One-way trapdoor 
Alcuni problemi One-Way trap door sono
##### Fattorizazione 
Calcolare il _prodotto_ $n$ di due interi $p$ e $q$ è  facile poiché richiede tempo _quadratico_ nella lunghezza della loro rappresentazione. Invertire la funzione significa ricostruire $p$ e $q$ a partire da $n$, il che è univocamente possibile solo se $p$ e $q$ sono [[Numeri primi|primi]]. Tale inversione richiede _tempo esponenziale_ su _calcolatori normali_ ma è stato dimostrato non essere [[Complessita|NP-hard]] siccome si può risolvere in [[Complessita|tempo polinomiale]] su [[Quantum computing|computer quantistici]] 
- Sono stati sviluppati algoritmi _subesponenziali_ per questo problema come il _[[Algoritmo per la fattorizazione General Number Field Sieve|Algoritmo per la fattorizazione General Number Field Sieve]]_(_GNFS_) che ha complessità $O(2^{\sqrt{ n\log n }})$ dove $n$ sono i bit della rappresentazione. 
- una soluzione _enumerativa_ (_bruteforce_) richeide $O(2^{n})$ operazioni  

conosce uno dei fattori (la chiave segreta) ricostruire l’altro è ovviamente facile

##### Calcolo della radice in modulo
_Calcolo della radice in [[Algebra modulare|modulo]]_. calcolare la potenza $y = x^z \mod s$, con $x, z, s$ interi, richiede tempo polinomiale se si procede per [[Algoritmo delle Quadrature successive o esponenziazione veloce|successive esponenziazioni]]. Il metodo richiede infatti di eseguire $\theta(log_2 z)$ moltiplicazioni, cioè un numero lineare nella lunghezza della rappresentazione di $z$, il che conduce a un algoritmo complessivamente cubico. 

Se $s$ non è [[Numeri primi|primo]] e se ne ignora la [[Teorema fondamentale del aritmetica|fattorizzazione]], invertire la funzione, cioè calcolare $x = \sqrt[z]{y} \mod s$ se sono noti $y, z, s$, richiede _tempo esponenziale_ per quanto noto fino a oggi. Se però $x$ è cooprimo con $s$ e si conosce l [[Inverso di un numero in algebra modulare|inverso]] $v$ di $z$ modullo $\Phi(s)$ ovvero    $z v \equiv 1 \mod \Phi(s)$
si ha che: $$
\begin{array}{}
y^v  & \mod s  & = \\
 x^{zv}  & \mod s  & = \\
 x^{1+k\Phi(s)}  & \mod s  & = \\
 x  & \mod  s & 
\end{array}
$$dove l’ultima eguaglianza è basata sul [[Teorema di Eulero|teorema di Eulero]]. Si ricostruisce quindi in tempo polinomiale $x$ calcolando $y^v \mod s$: in questo caso $v$ è la _chiave segreta_ per invertire la funzione.

##### Calcolo del logaritmo discreto
La funzione potenza del punto precedente si può invertire anche rispetto a $z$: dati  $x, y, s$ interi si richiede di trovare il valore di $z$ tale che $y = x^z \mod s$. Nell’algebra non modulare il problema, di semplice soluzione, è quello del calcolo di $z=\log_{x} y$; ma [[Algebra modulare|operando in modulo]] il problema è _computazionalmente difficile_ e non sempre ha soluzione.
Se $s$ è _[[Numeri primi|primo]]_ esiste una soluzione per ogni $y$ se e solo se $x$ è un [[Generatori di insieme di coprimi|generatore]] di $\mathcal{Z}^{∗}_{s}$ . A parte alcuni particolari primi $s$ per cui il calcolo si semplifica (per esempio se tutti i fattori primi di $s − 1$ sono piccoli)