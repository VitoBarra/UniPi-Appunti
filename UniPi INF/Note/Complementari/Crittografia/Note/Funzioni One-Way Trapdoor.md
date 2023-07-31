---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Funzioni One-Way Trapdoor
---
sono [[Funzioni|funzioni]] che sono semplici da calcolare in modo incondizionato ma difficili da invertire ameno che non si abbai un informazioni in piu.
il problema del invertire questa tipologia di funzione senza avere la _chiave_ è solfitate [[Calcolabilità\|NP-Hard]] o non si sa ancora un algoritmo polinomiale.

alcuni esempi sono

_Fattorizzazione_: Calcolare il prodotto $n$ di due interi $p$ e $q$ è  facile poiché richiede tempo _quadratico_ nella lunghezza della loro rappresentazione. Invertire la funzione significa ricostruire $p$ e $q$ a partire da $n$, il che è univocamente possibile solo se $p$ e $q$ sono primi. Tale inversione richiede tempo esponenziale per quanto è noto fino a oggi, anche se non vi è dimostrazione che il problema sia [[Calcolabilità|NP-hard]]. Se pero si conosce uno dei fattori (la chiave segreta) ricostruire l’altro è ovviamente facile

_Calcolo della radice in modulo_. calcolare la potenza $y = x^z \mod s$, con $x, z, s$ interi, richiede tempo polinomiale se si procede per [[Algoritmo delle Quadrature successive o esponenziazione veloce|successive esponenziazioni]]. Il metodo richiede infatti di eseguire $\theta(log_2 z)$ moltiplicazioni, cioè un numero lineare nella lunghezza della rappresentazione di $z$, il che conduce a un algoritmo complessivamente cubico. 
Se $s$ non è [[Numeri primi|primo]] e se ne ignora la [[Teorema fondamentale del aritmetica|fattorizzazione]], invertire la funzione, cioè calcolare $x = \sqrt[z]{y} \mod s$ se sono noti $y, z, s$, richiede _tempo esponenziale_ per quanto noto fino a oggi. Se però $x$ è coprimo con $s$ e si conosce  $z v \equiv 1 \mod \Phi(s)$, si ha: $y^v \mod s = x^{zv} \mod s = x^{1+k\Phi(s)} \mod s = x \mod s$, in cui l’ultima eguaglianza è basata sul [[Teorema di Eulero|teorema di Eulero]]. Si ricostruisce quindi in tempo polinomiale $x$ calcolando $y^v \mod s$: in questo caso $v$ è la _chiave segreta_ per invertire la funzione.


_Calcolo del logaritmo discreto_. La funzione potenza del punto precedente si può invertire anche rispetto a $z$: dati  $x, y, s$ interi si richiede di trovare il valore di $z$ tale che $y = x^z \mod s$. Nell’algebra non modulare il problema, di semplice soluzione, è quello del calcolo di $z=\log_{x} y$; ma [[Algebra modulare|operando in modulo]] il problema è _computazionalmente difficile_ e non sempre ha soluzione. Se $s$ è primo esiste una soluzione per ogni $y$ se e solo se $x$ è un [[Generatori di insieme di coprimi|generatore]] di $Z^{∗}_{s}$ . A parte alcuni particolari primi $s$ per cui il calcolo si semplifica (per esempio se tutti i fattori primi di s − 1 sono piccoli)