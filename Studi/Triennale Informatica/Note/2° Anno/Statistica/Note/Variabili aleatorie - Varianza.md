---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili aleatorie - Varianza
---
#### Varianza (Definizione)
_Sia_ $X$ una variabile aleatoria che ammette [[Variabili aleatoria - Momenti|momento secondo]] 
_allora_ è detta _varianza_ il numero 
$$Var(X)=\mathbb{E}[(X-\mathbb{E}[X])^{2}]$$
e questa dipende solo dalla _legge di probabilita_ $\mathcal{P}_{X}$ e sviluppando i calcoli si ottiene $$Var(x)=\mathbb{E}[X^{2}]-\mathbb{E}[X]^{2}$$
e vale $$Var(aX+b)=a^{2}Var(X)$$
#### Deviazione standard (Definizione)
_sia_ $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] che ammette [[Variabili aleatoria - Momenti|momento secondo]] 
_allora_ si dice [[Residui quadratici in modulo]]_scarto quadratico medio_ o _deviazione standard_ il numero $$\sigma(X)=\sqrt{ Var(X) }$$

#### Diseguaglianza di Chebyshev
_sia_ $X$  una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] e $d>0$ un numero 
_vale_ $$\mathcal{P}\{|X-\mathbb{E}[X]>d|\} \leq \frac{Var(X)}{d^2}$$
_Dimostrazione_:
	questa diseguaglianza deriva direttamente dalla _[[Diseguaglianza di Markov|diseguaglianza di markov]]_ ponendo $Y=(X-\mathbb{E}[X])^{2}$, $a=b^{2}$ e tenendo presente che $$\mathcal{P}\{ |X-\mathbb{E}[X]|>b \}=\mathcal{P}\{ (X-\mathbb{E}[X])^{2}>b^{2}\}$$
> [!tip]
> la varianza è $0\iff X=0$  o se è costante tranne che per un insieme trascurabile ovvero $\mathcal{P}\{ |X-\mathbb{E}[X] \not=0 \}=0$ 