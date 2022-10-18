---
type: nota
topic: 
tags: MATH
---

# Calcolare l N-esimo numero primo Willans's formula
---

fonte: https://www.youtube.com/watch?v=j5s0h42GfvM

la _formula di Willans_  riesce a computare l $n$-simo numero primo ma ha una complessità troppo alta per essere utilizzabile di fatti non passa il [[test di Wilf]]
	$$\large1+\sum^{2^n}_{i=1}\left\lfloor
	\left(
	\frac{n}{\sum^i_{j=1}
	\left\lfloor 
		\left (cos\pi\frac{(j-1)!+1}{j}\right )^2
		\right\rfloor}
	\right )^{\frac{1}{n}}
	\right\rfloor$$
utilizza il [[teorema di Wilson]] per determinare se un numero è primo o no $\frac{(j-1)!+1}{j}$ è sempre un numero intero se $j$ è primo o 1



>[!question]
>questa formula è interessante per notare come l aritmetica può essere usata per creare qualcosa simile ad algoritmi, questo potrebbe significa che l aritmetica è [[Turing completezza |Turing-complete]] e quindi [[Turing-Calcolabilita|T-Calcolabile]] \[da verificare\]