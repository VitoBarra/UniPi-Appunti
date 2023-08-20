---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario ElGamal
---
è un [[Cifrari a chiave Asimmetrica|cifrario a chiave asimetrica]] 

### Generazione delle chiavi
_sia_ $p$ un numero primo e un [[Generatori di insieme di coprimi]] di $\mathcal{Z}^{*}_{p}$ 
si calcola un intero a caso $x\in [2,p-2]$
si calcola $y=g^{x}\mod p$
_allora_ $k[pub]=\langle p,g,y\rangle \ ,\  k[prv]=\langle x\rangle$ 

il processo segue come:

[[Cifrario Asimmetrico RSA]]

#### cifratura
_sia_ $m$ il messaggio trattato come un _numero intero_
1. il messaggio deve essere $m<p$ altrimenti si fa una cifratura a blocchi di $\log_{2}p$ bit ciascuno
2. si calcola a caso un intero $r \in [2,p-2]$
3. si calcola la coppia di crittogrammi $$c= g^{r}\mod  p \ \ \ \ d=my^{r}\mod  p$$
#### Decifratura
per $m<p$ si ha che 
$$\begin{array}{}
 dc^{-x}  & \mod   p  & = \\
my^{r}c^{-x}  & \mod  p  & = \\
my^{r}(g^{r})^{-x} & \mod  p  & = \\
m(g^{x})^{r}g^{-rx} & \mod   p & = \\
m  & \mod  p  & = & m
\end{array}$$
quindi abbiamo che 
$$m=dc^{-x}\mod   p$$

### Sicurezza
La difficoltà di calcolare il [[Funzioni One-Way Trapdoor|logaritmo discreto]] rende la chiave privata $x$ sicura, anche se $y$ e $g$ sono pubblici 
se $r$ è un _[[Generazione di numeri Pseudo Casuali|intero casuale]]_ 
- $y^{r} \mod p$ è un _intero casuale_ 
- $d = m·y^{r} \mod p$ è casuale e non fornisce alcuna informazione su $m$ al crittoanalista 
 per _calcolare_ $r$ da $c$ occorre risolvere il problema del _logaritmo discreto_ 
- se $r$ è noto si può decifrare: $m = d y^{-r} \mod p$ 
 occorre un _nuovo numero casuale_ $r$ per ogni nuovo messaggio



### Attacchi al cifrario
questo cifrario è sensibile a tipi di attacchi [[Tipologia di attacchi per scoprire il messaggio criptato|man in the midle]]
cosi come per il cifrario [[Cifrario Diffie-Hellman (DH)]]