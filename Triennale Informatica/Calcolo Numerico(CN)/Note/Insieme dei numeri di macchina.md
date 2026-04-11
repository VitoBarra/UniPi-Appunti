---
Course: "[[Calcolo Numerico(CN)]]"
tags:
  - CN
topic:
---

# Insieme dei numeri di macchina
---
il [[Rappresentazione in base di numeri reali|Teorema della rappresentazione]] ci assicura che un numero puo essere rappresentato nella formula li spiegata ma utilizza spazio infinito e i calcolatori non hanno spazi infiniti, ciò significa che bisogna dare dei criteri per definire quali numeri sono rappresentabili nel calcolatore. tenendo conto del accuratezza di rappresentazione.
l insieme dei numeri esattamente rappresentabili è detto _Insieme di numeri di macchina_

### Insieme dei numeri di macchina
l _Insieme dei numeri di macchina_ in rappresentazione floating point con $t$ cifre è definiti come 
$$\mathscr{F}(\beta,t,m,M) = \{0\} \cup \{x \in \mathbb{R}\mid x= segno(x)\beta^p \sum _{i=1}^t d_i\beta^{-i}\}$$
dove : 
- $\beta$ è la base che si utilizza
- $t$  è il numero di cifre decimali a disposizione
- $m$ è il numero massimo del esponente negativo
- $M$ è il numero massimo del esponente positivo
e si ha che:
- $-m \leq p \leq M$
-  $d_1 \not= 0$
-  $0 \leq d_i \leq \beta -1$ interi
questo è un [[Insieme Simmetrico]] rispetto l origine


#### Proprietà
- Numero positivo più _piccolo_ rappresentabile 
	- $w = \beta^{-m-1}$
- numero più _grande_  rappresentabile
	- $\Omega = \beta^M(1-\beta^{-t})$
- [[Insiemi - Cardinalita|Cardinalità]] dei numeri di macchina:
	- $|\mathscr{F}| = 1 + 2(m+M+1)(\beta -1)(\beta^{t-1})$
		- +1 per lo zero
		- $\times 2$ perché è simmetrico
		- $(m+M+1)$ gli esponenti 
		- $(\beta -1)(\beta^{t-1})$ possibili mantisse
- Distanza tra due numeri
	- _sia_ $x=(-1)^s\beta^p\alpha \in \mathscr{F}(\beta,t,m,M)$ _allora_ il successivo numero di macchina risulta essere $y = (-1)^s\beta^p(\alpha+\beta^{-t})$ 
	- da qui vale che la distanza  $|y-x| = \beta^{p-t}$ 
		- quindi la distanza dipende da $p$ ovvero dal ordine di grandezza che stiamo considerando



#### Rappresentazione in memoria
 il teorema della [[Rappresentazione in base di numeri reali|Rappresentazione in base di numeri reali]] ci dice che possiamo rappresentare un numero di macchina come 
![[IMG - Insieme dei numeri di macchina segno esponente cifre.jpeg]]

standard IEEE per l aritmetica
- _double_: 64 bit 
	- 1 bit per il segno 
	- 11 bit per l esponente
	- 52 bit per la mantissa
		- il primo bit non è davvero memorizzato si assume sia 1 quindi si rappresentano 53 bit per la mantissa
	- $\mathscr{F}(2,53,1021,1024)$
	- approssima per arrotondamento 
	- rappresentazione speciali
		- $p=M$  (parte del esponente tutto a 1)
			- se mantissa tutta a 0 e esponente tutti a 1  interpretati come $+\infty \ — \infty$ a seconda del segno 
			- se esponente tutto 1 e mantissa diversa da tutto zero ritorna NaN
		- $d_1 =0$ (numeri denormalizati)
			- esponente tutto 0  
				- usati per estendere i numeri di macchina e permettere di rappresentare i numeri nel range  $\beta^{-m-t} \leq x \leq \beta^{-m}(\beta^{-1}-\beta^{-t})$
	- solo in numeri dello standard  esistono nella aritmetica di macchina  
- _float_: 32 bit

### Virgola fissa
registro da $N$ bit che rappresenta una parte di numero $N$ in 3 parti
 - 1 bit per il segno 
 -  $I$ bit per la parte intera
 - $N-I-1$ per la parte frazionaria

Questa rappresentazione ha molti problemi 
