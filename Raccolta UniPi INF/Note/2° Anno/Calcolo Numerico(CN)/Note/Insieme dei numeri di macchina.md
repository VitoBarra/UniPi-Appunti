---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Insieme dei numeri di macchina
---
il [[Rappresentazione in base di un numero|Teorema della rappresentazione]] ci assicura che un numero puo essere rappresentato nella formula li spiegata ma utilizza spazio infinito e i calcolatori non hanno spazi infiniti, ciò siginifica che bisogna dare dei criteri per definire quali numeri sono rappresentabili nel calcolatore. tenendo conto del accuratezza di rappresentazione.
l insieme dei numeri esattamente rapresentabili è detto _Insieme di numeri di macchina_

### Insieme dei numeri di macchina
l _Insieme dei numeri di macchina_   in rappresentazione floating point con $t$ cifre è definiti come 
$$\mathscr{F}(\beta,t,m,M) = \{0\} \cup \{x \in R\mid x= segno(x)\beta^p \sum _{i=1}^t d_i\beta^{-i}\}$$
dove : 
- $\beta$ è la base che si utilizza
- $t$  è il numero di cifre decimali a disposizione
- $m$ è il numero massimo del esponente negativo
- $M$ è il numero massimo del esponente positivo
e si ha che:
- $-m \leq q \leq M$
-  $d_1 \not= 0$
-  $0 \leq d_i \leq \beta -1$ interi
questo  è un [[Insieme Simmetrico]]


##### Proprietà
- Numero positivo più _piccolo_ rappresentabile 
	- $w = \beta^{-m-1}$
- numero piu _grande_  rappresentabile
	- $\Omega = \beta^M(1-\beta^{-t})$
- [[Cardanilita di un insieme|Cardinalità]] dei numeri di macchina:
	- $|\mathscr{F}| = 1 + 2(m+M+1)(\beta -1)(\beta^{t-1})$
		- +1 per lo zero
		- $\times 2$ perche è simmetrico
		- $(m+M+1)$ gli esponenti 
		- $(\beta -1)(\beta^{t-1})$ possibili mantisse
- Distanza tra due numeri
	- Posto $x=(-1)^s\beta^p\alpha \in \mathscr{F}(\beta,t,m,M)$ allora il successivo numero di macchina risulta essere $y = (-1)^s\beta^p(\alpha+\beta^{-t})$ 
	- da qui possiamo scrivere che la distanza  $|y-x| = \beta^{p-t}$ 
		- quindi la distanza dipende da $p$ ovvero dal ordine di grandezza che stiamo considerando



##### Rappresentazione in memoria
 il teorema della [[Rappresentazione in base di un numero]] ci dice che possiamo rappresentare un numero di macchina come 
![[C246B2CD-EF78-4202-9850-49AAFD7D5577.jpeg]]

standard IEEE per l aritmetica
- _double_: 64 bit 
	- 1 bit per il segno 
	- 11 bit per l esponente
	- 52 bit per la mantissa
		- il primo bit non è davvero memorizzato si assume sia 1 quindi si rapresentano 53 bit per la mantissa
	- $\mathscr{F}(2,53,1021,1024)$
	- approssima per arrotondamento 
	- rapresentazione speciali
		- $p=M$  (parte del esponente tutto a 1)
			- se mantissa tutta a 0 e esponente tutti a 1  interpretati come $+\infty \ — \infty$ a seconda del segno 
			- se esponente tutto 1 e mantissa diversa da tutto zero ritorna NaN
		- $d_1 =0$ (numeri denormalizati)
			- esponente tutto 0  
				- usati per estendere i numeri di macchina e permettere di rappresentare i numeri nel range  $\beta^{-m-t} \leq x \leq \beta^{-m}(\beta^{-1}-\beta^{-t})$
	- solo in numeri dello standard non esistono nella aritmetica di macchina  
- _float_: 32 bit