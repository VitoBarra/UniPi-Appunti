---
Course: Ricerca Operativa
topic: nota
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Teoremi su Problema duale
---
## Lemma di Farkas

I sistemi

$$
\begin{cases}
c^Tx >0 \\
Ax \leq 0
\end{cases} \ \ \ \ \ \ \ \ \ e \ \ \ \ \ \ \ \
\begin{cases}
y^TA = c^T \\
y \geq 0
\end{cases}
$$

sono in alternativa , cioè uno ammette soluzioni se e solo se l altro non ha soluzioni.

in termini di [[Programmazione lineare|PL]] il Lemma di Farkas equivale a dire che nel problema primale esiste una [[Poliedro#Direzione di recessione|direzione di  recessione]] che è anche di crescita se e solo se la regione ammissibile del problema duale è vuota

---

### Teoremi di dualità forte e debole

un problema di PL in forma canonica è detto primale nella forma

$$
\begin{cases}
\max c^Tx \\
x \in P =\{x \in \mathbb{R}^n \ | \ Ax \leq b\}
\end{cases}
\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \
(\mathcal{P})
$$

in cui la regione ammissibile $P \not= \emptyset$.

### Teorema di dualità debole

Se $x\in P$ e $y\in D$, allora $c^Tx \leq y^Tb$. quindi $v(\mathcal{P}) \leq v(\mathcal{D})$

### Teorema di dualità forte

- Se il [[Poliedro|poliedro]] duale $D = \emptyset$, allora il valore ottimo del primale $v(\mathcal{P}) = +\infty$
- Se il [[Poliedro|poliedro]] duale $D \not= \emptyset$, allora $v(\mathcal{P})$  è finito e $v(\mathcal{P}) = v(\mathcal{D})$
