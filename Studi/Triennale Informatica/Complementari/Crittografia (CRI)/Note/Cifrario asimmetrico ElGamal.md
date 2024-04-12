---
Subject: Crittografia
topic: nota
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario asimmetrico ElGamal
---
è un [[Cifrari a chiave Asimmetrica|cifrario a chiave asimetrica]] 

### Generazione delle chiavi
_sia_
1. $p$ un numero primo
2. $g$ un [[Generatori di insieme di coprimi|generatore]] di $\mathcal{Z}^{*}_{p}$ 
3.  un _intero_ a caso $x\in [2,p-2]$
4. posto  $y=g^{x}\mod p$
_allora_ $$k[pub]=\langle p,g,y\rangle \ ,\  k[prv]=\langle x\rangle$$
#### Cifratura
_sia_ $m$ il messaggio trattato come un _numero intero_
1. il messaggio deve essere $m<p$ altrimenti si fa una cifratura a blocchi di $\log_{2}p$ _bit_ ciascuno
2. si calcola a caso un intero $r \in [2,p-2]$
3. si calcola la coppia di crittogrammi $$c= g^{r}\mod  p \ \ \\ \ \ \ \ \ \ \ \ \  \ d=my^{r}\mod  p$$
#### Decifratura
per $m<p$ si ha che 
$$\mathcal{D}(d,c)=m=dc^{-x}\mod   p$$

#### Correttezza
Dobbiamo mostrare che $m=dc^{-x} \mod  p$
$$\begin{array}{}
 dc^{-x}  & \mod   p  & = \\
my^{r}c^{-x}  & \mod  p  & = \\
my^{r}(g^{r})^{-x} & \mod  p  & = \\
m(g^{x})^{r}g^{-rx} & \mod   p & = \\
mg^{0}  & \mod  p  & = & m
\end{array}$$
quindi la decifrazione è corretta

### Sicurezza
La difficoltà di calcolare il [[Funzioni One-Way Trapdoor|logaritmo discreto]] rende la chiave privata $x$ sicura, anche se $y$ e $g$ sono pubblici 
se $r$ è un _[[Generatori di numeri Pseudo Casuali|intero casuale]]_ 
- $y^{r} \mod p$ è un _intero casuale_ 
- $d = m·y^{r} \mod p$ è casuale e non fornisce alcuna informazione su $m$ al crittoanalista 
 per _calcolare_ $r$ da $c$ occorre risolvere il problema del _[[Funzioni One-Way Trapdoor#Calcolo del logaritmo discreto|logaritmo discreto]]_ 
- se $r$ è noto si può decifrare: $$\begin{array}{}
 d y^{-r}  & \mod p \\
 m(y^{r} y^{-r})  & \mod p    & =m \\

\end{array}
$$occorre un _nuovo numero casuale_ $r$ per ogni nuovo messaggio




### Attacchi al cifrario
questo cifrario è sensibile a tipi di attacchi [[Tipologia di attacchi ai cifrari|man in the midle]]
cosi come per il cifrario [[Cifrario Diffie-Hellman (DH)]]