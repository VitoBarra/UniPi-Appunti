---
Course: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
---
# Radicale
---

### Definizione
il radicale e definito come l'insieme dei [[Vettori Ortogonali|vettori ortogonali]] a tutti gli altri ovvero:

$$
V^\bot =\{v\in V\ |\ \langle v,w\rangle = 0\ \ \forall w \in V \}
$$

 Osservazioni:

- I vettori presenti in $V^\bot$ sono anche isotropi
- $V^\bot$ e sottospazio di $V$

### Esistenza:

il prodotto scalare e non degenere $\iff V^\bot=\{0\}$

### Esempi:

Come primo esempio esaminiamo i prodotti scalari $g_S$ su $\mathbb{R}^n$. Sia

$$
S \in M(n, \mathbb{R})
$$

una matrice simmetrica.

**Proposizione 7.1.23.** Il radicale di $g_S$ e il sottospazio $\ker S$. Quindi il prodotto scalare $g_S$ e degenere $\iff \det S = 0$.

Dimostrazione. Se $y \in \ker S$, allora per ogni $x \in \mathbb{R}^n$ abbiamo

$$
g_S(x,y) = {}^t x S y = 0
$$

perche $Sy = 0$. D'altra parte, se un vettore $y \in \mathbb{R}^n$ e tale che

$$
{}^t x S y = 0
$$

per ogni $x \in \mathbb{R}^n$, allora scriviamo

$$
y' = Sy
$$

e otteniamo

$$
{}^t x y' = 0
$$

per ogni $x \in \mathbb{R}^n$. Questo implica facilmente che $y' = 0$, cioe che $y \in \ker S$.
