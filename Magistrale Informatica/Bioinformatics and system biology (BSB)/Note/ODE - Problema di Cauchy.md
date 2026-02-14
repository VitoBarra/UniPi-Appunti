---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# ODE - Problema di Cauchy
---
Il **Problema di Cauchy** per una [[Ordinary Differential Equation (ODE)|ODE]] consiste nel determinare una funzione $y(x)$ che soddisfi un’[[Equazioni differenziali|equazione differenziale]] e una condizione iniziale assegnata. Forma generale:$$\frac{dy}{dx}=f(x,y),\quad y(x_0)=y_0$$dove $f:D\subseteq\mathbb{R}\times\mathbb{R}^n\to\mathbb{R}^n$ è un [[Campo vettoriale|campo vettoriale]] e $(x_0,y_0)\in D$.

Il problema riguarda:
- **Esistenza**: esiste una soluzione?
- **Unicità**: la soluzione è unica?
- **Dipendenza continua dai dati iniziali**.

**Teorema di esistenza e unicità** (**Picard–Lindelöf**): se $f$ è continua in un intorno di $(x_0,y_0)$ e localmente lipschitziana rispetto a $y$, allora esiste ed è unica una soluzione locale del problema di Cauchy.

Forma integrale equivalente:
$$y(x)=y_0+\int_{x_0}^{x} f(s,y(s))\,ds$$
La dimostrazione del teorema si basa su un procedimento di iterazione successiva (metodo di Picard).

Intervallo massimale di esistenza: la soluzione può essere prolungata finché rimane in un dominio dove $f$ è definita e regolare.

Sensibilità ai dati iniziali: piccole variazioni in $y_0$ producono variazioni controllate nella soluzione se vale la condizione di Lipschitz.

Il **Problema di Cauchy** costituisce la formulazione standard per l’analisi teorica e per l’implementazione dei metodi di [[ODE - Integrazione Numerica|integrazione numerica]].