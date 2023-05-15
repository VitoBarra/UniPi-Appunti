---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Rappresentazione in base di un numero
---


## Virgola fissa
 registro da $N$ bit che rappresenta una parte di numero $N$ in 3 part 
 - 1 bit per il segno 
 -  $I$ bit per la parte intera
 - $N-I-1$ per la parte frazionaria

Questa rappresentazione ha molti problemi 



### Teorema di rappresentazione in base
comunque io scelga un $x \in \mathbb{R}, x \not= 0$ allora scelta una base $\beta$ di rappresentazione allora _esistono e sono uniche_ le sequenze quantità
1. $p \in \mathbb{Z}$ detto _esponente_ della rappresentazione
2. una successione di  $d_i \in \mathbb{N}$ con
	1. $i >  0$
	3. $0 \leq d_i \leq \beta -1$
	2. $d_1 \not=0$
	4. $d_i$ non definitivamente uguali a $\beta -1$
tale che:  
$$x= segno(X).\beta^p \sum _{i=1}^\infty d_i\beta^{-i}$$
la parte della sommatoria è chiamata _mantissa_

##### Vincoli per garantire l univocità
i vincoli servono per assicurarsi che la rappresentazione sia unica

1. $d_i$ non definitivamente uguali a $\beta -1$
	- questo evita situazioni di doppia rappresentazione del $1$ siccome  $0.\overline{(\beta-1)} = 1$ questo si dimostra con la [[Serie giometrica]] 
2. $d_1 \not=0$
	- evita la possibilità di rappresentare più volte lo stesso numero nelle occasioni m in ciò tutti  i $d_i =0$ tranne per il caso $i=p$ che ha $d_i =1$, questa è uno standard i si sarebbe potuta scegliere anche una altra cifra diversa da 0 (probabilmente meno efficiente)    
	- esempio: $$1=10^1(1 \cdot 10^{-1}) = 10^2(0\cdot10^{-1}+1\cdot10^{-2})$$
in questa forma i numeri sono detti  _numeri normalizzati in virgola mobile_, 
- l unico numero che non ammette una forma normalizzata è lo $0$ che è trattato in modo speciale
- si può estendere per la rappresentazione dei numeri complessi $z=a+ib$ rappresentandoli come coppie di numeri reali


