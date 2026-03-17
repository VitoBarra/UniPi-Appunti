---
Course: "[[Analisi]]"
topic: nota
tags:
  - Analisi
---
# Serie
---
La **_serie_** e' un'espressione della forma $$\sum_{n=1}^{+\infty}a_n$$ associata a una [[Successioni|successione]] $(a_n)_{n\geq 1}$ e viene definita attraverso la successione delle somme parziali $$S_N=\sum_{n=1}^{N}a_n$$

_Sia_ $(a_n)_{n\geq 1}$ una successione reale.
_Allora_ la serie $$\sum_{n=1}^{+\infty}a_n$$ converge se esiste finito il [[Limiti|limite]] $$\lim_{N\to+\infty}S_N$$ e in tal caso vale $$\sum_{n=1}^{+\infty}a_n=\lim_{N\to+\infty}S_N$$
Se questo limite non esiste oppure e' infinito, la serie diverge.

Una condizione necessaria di convergenza e' $$a_n\to 0$$ ma non e' sufficiente.

Tra le serie piu' importanti c'e' la serie $$\sum_{n=1}^{+\infty}\frac{1}{n^{\alpha}}$$ che:
- converge se $\alpha>1$;
- diverge se $\alpha\leq 1$.