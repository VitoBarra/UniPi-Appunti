---
type: nota
course: Calcolo Numerico
topic: 
tags:
  - CN
Parent MOC: "[[Calcolo Numerico(CN)]]"
---

# Rappresentazione in base di numeri reali
---

## Teorema di rappresentazione in base
_sia_ $x \in \mathbb{R}, x \not= 0$ e scelta una base $\beta$ di rappresentazione 
_allora_ _esistono e sono uniche_ le seguenti quantità
1. $p \in \mathbb{Z}$ detto _esponente_ della rappresentazione
2. una successione di  $d_i \in \mathbb{N}$ con
	1. $i >  0$
	3. $0 \leq d_i \leq \beta -1$
	2. $d_1 \not=0$
	4. $d_i$ non definitivamente uguali a $\beta -1$
tale che:  
$$x= segno(x)*\beta^p \sum _{i=1}^\infty d_i\beta^{-i}$$
la parte della sommatoria è chiamata _mantissa_

#### Vincoli per garantire l univocità
i vincoli ci assicurano che la rappresentazione sia unica

1. $d_i$ non definitivamente uguali a $\beta -1$
	- questo evita situazioni di doppia rappresentazione del $1$ siccome  $0.\overline{(\beta-1)} = 1$ questo si dimostra con la [[Serie geometrica|Serie geometrica]] 
2. $d_1 \not=0$
	- evita la possibilità di rappresentare più volte lo stesso numero nelle occasioni in cui ho tutti i $d_i =0$ tranne per il caso $i=p$ che ha $d_i =1$.
	- esempio: $$1=10^1(1 \cdot 10^{-1}) = 10^2(0\cdot10^{-1}+1\cdot10^{-2})$$

in questa forma i numeri sono detti  _numeri normalizzati in virgola mobile_, 
- l unico numero che non ammette una forma normalizzata è lo $0$ che è trattato in modo speciale
- si può estendere per la rappresentazione dei numeri complessi $z=a+ib$ rappresentandoli come coppie di numeri reali


