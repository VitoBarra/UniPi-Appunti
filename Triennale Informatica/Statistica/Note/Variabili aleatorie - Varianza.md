---
Course: "[[Statistica (STAT)]]"
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
e questa dipende solo dalla _legge di probabilità_ $\mathcal{P}_{X}$ e sviluppando i calcoli si ottiene $$Var(x)=\mathbb{E}[X^{2}]-\mathbb{E}[X]^{2}$$
che è possibile provare come: $$
\begin{array}{}
\text{Var}[X]  & = &  \mathbb{E}[(X - \bar{X})^2]  \\
 & = &  \sum_{i=1}^l \left( x_i - \bar{X} \right)^2 \mathcal{P}(x_i)  \\
 & = &  \sum_{i=1}^l \left( x_i^2 - 2 x_i \bar{X} + \bar{X}^2 \right) \mathcal{P}(x_i) \\
 & = & \sum_{i=1}^l x_i^2 \mathcal{P}(x_i) - 2 \bar{X} \sum_{i=1}^l x_i \mathcal{P}(x_i) + \bar{X}^2 \sum_{i=1}^l \mathcal{P}(x_i)\\
 & = &  \mathbb{E}[X^2] - 2 \bar{X} \bar{X} + \bar{X}^2 \cdot 1 \\
 & = &  \mathbb{E}[X^2] - \bar{X}^2 \\
\end{array}
$$


e vale $$Var(aX+b)=a^{2}Var(X)$$
#### Deviazione standard (Definizione)
_sia_ $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] che ammette [[Variabili aleatoria - Momenti|momento secondo]] 
_allora_ si dice [[Residui quadratici in modulo]]_scarto quadratico medio_ o _deviazione standard_ il numero $$\sigma(X)=\sqrt{ Var(X) }$$

