---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Algoritmo di Koblitz
---
L _algoritmo di Koblitz_ è un [[Algoritmi|algoritmo]] della casse degli [[Algoritmi Randomizzati|Algoritmi Randomizzati]] e serve a trasformare un intero $m$ in un punto su una [[Curve Ellittiche|curva ellittica]] $E_{p}(a,b)$ prima o binaria,
questo algoritmo ha una probabilità di fallire _arbitrariamente abbassabile_

 
### Algoritmo di Koblitz
_Sia_ $m$ un numero intero $m < p$ e $E_{p}(a,b)$ una _[[Curve Ellittiche|curva ellittica]] prima_ sul campo finito $\mathcal{Z}_{p}$ 
usando $m$ come ascissa  la probabilità che $(m^{3}+am+b)\mod p$ sia un [[Residui quadratici|residuo quadratico]] è di circa $\cfrac{1}{2}$
detto ciò si può fissare un intero $h$ tale che $(m+1)h<p$ (questo serve ad evitare che il messaggio venga corrotto dalle _operazioni di modulo_) e si considerano potenziali ascisse di un punto della curva i valori $mh+i$ dove $0 \leq i < h$. 
Siccome per essere un punto della curva ellittica deve valore $$y^{2}\equiv x^{3}+ax+b \mod   p$$abbiamo che per ogni diverso $x$ se l equazione è verificata _allora esiste_ la radice quadrata 
$$y = \sqrt{ x^{3}+ax+b } \mod   p$$
calcolare questa radice ha [[Complessita|costo polinomiale]] visto che  $p$ è [[Numeri primi|primo]].

Si scansionano sequenzialmente le vari possibili $x_{i} = mh+i$ e si cerca di calcolare la radice $y_{i}$ se _questa esiste_ allora il punto  sulla curva sarà $P_{m} = (x_{i},y_{i})$ _altrimenti_ si incrementa $i$ e si prova con la prossima $x$ _candidata_. L algoritmo si ferma al primo punto trovato, o in caso di fallimento quando $i$ avrà raggiunto $h$ e in questo caso non è stato possibile trasformare $m$ in un punto sulla curva.


Siccome la probabilità che la radice non esista, e che quindi $x^{3}+ax+b$ non sia uno [[Residui quadratici|scarto quadratico]] e che quindi il punto non è sulla curva è $\cfrac{1}{2}$ abbiamo che provando per $h$ valori la [[Probabilità e variabili aleatorie|probabilità]] che il _metodo fallisca_ è  $2^{-h}$ e che quindi può essere arbitrariamente abbassata cambiando il valore di $h$

per tornare indietro e trasformare un punto in un intero si deve calcolare$$m = \left\lfloor\cfrac{x_{i}}{h} \right\rfloor$$


 

 
