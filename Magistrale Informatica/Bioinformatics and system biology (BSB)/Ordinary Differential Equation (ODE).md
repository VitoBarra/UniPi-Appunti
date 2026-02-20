---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# Ordinary Differential Equation (ODE)
---
Una **Ordinary Differential Equation (ODE)** è un’equazione differenziale che coinvolge una funzione incognita di una sola variabile indipendente e le sue derivate rispetto a tale variabile.

Forma generale (equazione scalare di ordine $n$):
$$F\big(t,x,\dot x,\ddot x,\dots,x^{(n)}\big)=0$$
Forma esplicita del primo ordine:
$$\frac{dx}{dt}=f(t,x)$$

Un sistema di ODE del primo ordine in $\mathbb{R}^n$ è scritto come:
$$\frac{dx(t)}{dt}=f(x(t),t)$$
dove $x(t)=(x_1(t),\dots,x_n(t))$ è il vettore delle variabili di stato e $f:\mathbb{R}^n\to\mathbb{R}^n$ è un campo vettoriale.

Classificazioni principali:
- Ordine: massimo ordine di derivata presente.
- Lineare: $$\frac{dx}{dt}=A(t)x+b(t)$$
- Non lineare: presenza di termini non lineari in $x$.
- Autonoma: $$\frac{dx}{dt}=f(x)$$ (assenza di dipendenza esplicita dal tempo).
- Non autonoma: $$\frac{dx}{dt}=f(x,t)$$

Problema di Cauchy (valore iniziale):
$$\frac{dx}{dt}=f(x,t),\quad x(t_0)=x_0$$
Se $f$ è continua e localmente lipschitziana in $x$, esiste ed è unica la soluzione locale.

Punti di equilibrio (sistemi autonomi):
$$f(x^*)=0$$
Sono stati stazionari del sistema.

Linearizzazione locale attorno a $x^*$:
$$\frac{d\delta x}{dt}=J(x^*)\delta x$$
dove $J$ è la matrice Jacobiana $J_{ij}=\frac{\partial f_i}{\partial x_j}$. La stabilità locale dipende dagli autovalori di $J(x^*)$.

Comportamenti dinamici possibili:
- Convergenza a equilibrio.
- Divergenza.
- Oscillazioni.
- Dinamiche non lineari complesse.

Metodi di soluzione:
- Analitici (separazione delle variabili, fattore integrante, trasformate).
- Numerici (Euler, Runge–Kutta, metodi impliciti per sistemi stiff).

Le ODE costituiscono il formalismo fondamentale per la descrizione matematica di sistemi dinamici continui nel tempo.