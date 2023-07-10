---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario affine e cifrari completo
--- 
è un tipo di [[Cifrari storici|cifrario usato storicamente]] 

e riferendosi alla [[Classificazione di cifrari|classificazione di cifrari]] abbiamo che è un cifrario a _sostituzione monoalfabetico_

[[Cifrario di Cesare]]

#### formalizzazione 
_sia_ $pos(x)$ la posizione nel alfabeto con $pos(A)=0$ e $pos(Z)=25$ e sia la chiave $k=\langle a,b \rangle$ con $a,b$ parametri del cifrario
abbiamo che la [[Cifratura e Decifratura|funzione di cifratura/decifratura]] sulle singole lettere sono definite come
$$
\begin{array}
\mathcal{C}_{i}(x)=(a \times pos(x)+b) \mod 26 \\
\mathcal{D}_{i}(x)=(a^{-1} \times (pos(x)-b)) \mod 26
\end{array}
$$
dove $a^{-1}$ è l [[Inverso di un numero in algebra modulare|inverso]] di $a\mod 26$  
per far si che questo numero _esista e sia unico_ c è bisogno che sia primo con 26 ovvero deve valere che il [[Massimo comun divisore|massimo comun divisione]] sia $mcd(a,26)=1$ ovvero $a$ deve essere coprimo con $26$.
cosi non fosse avremmo che la funzione di cifratura non è [[Funzioni|iniettiva]].

##### Spazio delle chiavi
per calcolare lo spazio delle chiavi $K$ notiamo che dobbiamo avere $a$ coprimo con $26$ ed essendo i fattori di $26 = 2 \cdot 13$ abbiamo che $0<a<26$ puo essere qualsiasi numero dispari diverso da $13$ e quindi abbiamo $12$ scelte e $b$ che puo essere qualsiasi numero $0<b<26$   e quindi abbiamo $26$ scelte e quindi
$$|K|=12 \times 26 = 312-1 = 311$$
togliamo 1 siccome vogliamo evitare di usare la coppia $\langle 1,0\rangle$ che lascia invariata la [[Rappresentazione di oggetti matematici con sequenze|sequenza]]


#### Cifrario completo
la chiave segreta $k$ è una qualsiasi permutazione del alfabeto e quindi lo spazio delle chiavi è di [[Cardinalità di un insieme|cardinalita]] $|K| = 26!-1$ per esclusione della permutazione nulla.






