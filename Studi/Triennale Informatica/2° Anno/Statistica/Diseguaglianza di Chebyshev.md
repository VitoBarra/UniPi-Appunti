---
Subject: "[[Statistica (STAT)]]"
tags:
  - "#STAT"
Area: 
topic: 
SubTopic:
---

# Diseguaglianza di Chebyshev
---
la __diseguaglianza di Chebyshev__ dice che 
_sia_ $X$  una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] e $d>0$ un numero 
_vale_ $$\mathcal{P}\{|X-\mathbb{E}[X]|>d\} \leq \frac{Var(X)}{d^2}$$
_Dimostrazione_:
	questa diseguaglianza deriva direttamente dalla _[[Diseguaglianza di Markov|diseguaglianza di markov]]_ ponendo $Y=(X-\mathbb{E}[X])^{2}$, $a=b^{2}$ e tenendo presente che $$\mathcal{P}\{ |X-\mathbb{E}[X]|>b \}=\mathcal{P}\{ (X-\mathbb{E}[X])^{2}>b^{2}\}$$
> [!tip]
> la varianza è $0\iff X=0$  o se è costante tranne che per un insieme trascurabile ovvero $\mathcal{P}\{ |X-\mathbb{E}[X]| \not=0 \}=0$ 