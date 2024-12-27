---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Diseguaglianza di Cauchy-Schwartz
---
__Siano__
- $a, b \in \mathbb{R}^n$ due vettori
- $\|\cdot\|_c$ la [[Norme Matriciali e Norme Vettoriali|norma euclidea]] 
__Allora__ vale che:
$$ (a^T b)^2 \leq ||a||^2 ||b||^2$$
Che ci dice che il prodotto di due vettori è limitato dal prodotto della norma dei vettori coinvolti.

_dimostrazione_
	segue quella nel caso $\mathbb{R}^{2}$ 



Nel contesto della statistica:
_siano_ $X$ e $Y$ due _[[Variabili Aleatorie (Casuali)|variabili aleatorie]]_ 
_se_ queste hanno _[[Variabili aleatoria - Momenti|momento secondo]]_ 
_allora_ vale $$\mathbb{E}[|XY|] \leq \sqrt{ \mathbb{E}[X^{2}] } \cdot \sqrt{ \mathbb{E}[Y^{2}] }$$



