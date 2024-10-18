---
Course: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario affine e cifrari completo
--- 
è un tipo di [[Cifrari storici|cifrario usato storicamente]] 

e riferendosi alla [[Classificazione di cifrari|classificazione di cifrari]] abbiamo che è un cifrario a _sostituzione monoalfabetico_

#### Formalizzazione 
_sia_ $pos(x)$ la posizione nel alfabeto con $pos(A)=0$ e $pos(Z)=25$ e sia la chiave $k=\langle a,b \rangle$ con $a,b$ parametri del cifrario  e $0<a<26$ e  $0\leq b<26$
Abbiamo che la [[Cifratura e Decifratura|funzione di cifratura/decifratura]] sulle singole lettere sono definite come
$$
\begin{array}
\mathcal{C}_{i}(x) & = & (a \times pos(x)+b)  & \mod 26 \\
\mathcal{D}_{i}(x) & = & (a^{-1} \times (pos(x)-b))  & \mod 26
\end{array}
$$
dove $a^{-1}$ è l [[Inverso di un numero in algebra modulare|inverso]] di $a\mod 26$  
Per far si che questo numero _esista e sia unico_ c è bisogno che $a$ sia comprimo con $26$ ovvero deve valere che il [[Massimo comun divisore|massimo comun divisione]] sia $MCD(a,26)=1$ 
Cosi non fosse avremmo che la funzione di cifratura non è [[Funzioni#Funzione Iniettiva|iniettiva]] e di conseguenza non si potrebbe scrivere una funzione di _decifratura_ che riesce a decifrare unicamente ogni carattere

##### Spazio delle chiavi
vogliamo calcolare la [[Cardinalità di un insieme|cardinalita]] dello spazio delle chiavi $K$
Partiamo notando che dobbiamo avere $MCD(a,26)=1$ ed essendo i _fattori_ di $26 = 2 \cdot 13$ abbiamo che $0<a<26$ puo essere qualsiasi numero _dispari_ diverso da $13$ e quindi abbiamo $12$ scelte e $b$ che può essere qualsiasi numero $0\leq b< 26$   e quindi abbiamo $26$ scelte e quindi
$$|K|=12 \times 26 = 312-1 = 311$$
Togliamo $1$ siccome vogliamo evitare di usare la coppia $\langle 1,0\rangle$ che lascia invariata la _stringa_


#### Cifrario completo
la chiave segreta $k$ è una qualsiasi permutazione del alfabeto e quindi lo spazio delle chiavi è di [[Cardinalità di un insieme|cardinalita]] $|K| = 26!-1$ per esclusione della permutazione nulla.






