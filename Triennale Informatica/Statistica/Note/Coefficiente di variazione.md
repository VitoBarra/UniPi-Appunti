---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Coefficiente di variazione
---
Il **coefficiente di variazione** è un indice di dispersione relativo, usato per confrontare la variabilità di insiemi di dati che hanno scale o unità di misura diverse.

L'idea è misurare quanto grande è la [[Statistica descrittiva - Dati Numerici#Deviazione standard (definizione)|deviazione standard]] rispetto alla [[Statistica descrittiva - Dati Numerici#Media (definizione)|media]] dei dati.

Sia $x=(x_1,\dots,x_n)$ un vettore di dati numerici con media $\overline{x}\neq 0$.
Il **coefficiente di variazione** è definito come $$CV(x)=\frac{\sigma(x)}{|\overline{x}|}$$dove $\sigma(x)$ è la deviazione standard dei dati.

Se si usa la deviazione standard empirica, allora si ottiene il coefficiente di variazione empirico$$CV_e(x)=\frac{\sigma_e(x)}{|\overline{x}|}$$Spesso viene espresso in percentuale:
$$
CV(x)\cdot 100\%
$$

Il coefficiente di variazione misura la dispersione dei dati **in rapporto al loro valore medio**.

- Se $CV(x)$ è piccolo, allora i dati sono poco dispersi rispetto alla media.
- Se $CV(x)$ è grande, allora i dati sono molto dispersi rispetto alla media.

A differenza della [[Statistica descrittiva - Dati Numerici#Varianza (definizione)|varianza]] e della deviazione standard, il coefficiente di variazione è un numero puro, cioè non dipende dall'unità di misura dei dati.

Per questo motivo è utile per confrontare fenomeni misurati su scale diverse.


#### Proprietà
Sia $a\neq 0$ e sia $y_i=ax_i$ per ogni $i$.

Allora
$$
\overline{y}=a\overline{x}
$$
e
$$
\sigma(y)=|a|\sigma(x)
$$
quindi
$$
CV(y)=\frac{\sigma(y)}{|\overline{y}|}
=\frac{|a|\sigma(x)}{|a\overline{x}|}
=\frac{\sigma(x)}{|\overline{x}|}
=CV(x)
$$

Quindi il coefficiente di variazione non cambia se tutti i dati vengono moltiplicati per una stessa costante non nulla.

#### Osservazioni
Il coefficiente di variazione è significativo soprattutto quando la media è diversa da zero e rappresenta una quantità positiva.

Se $\overline{x}=0$, il coefficiente di variazione non è definito.

Se la media è molto vicina a zero, il coefficiente può diventare molto grande e difficile da interpretare.

Per dati che possono assumere valori negativi, bisogna usare cautela: il rapporto tra deviazione standard e media può perdere il significato intuitivo di variabilità relativa.
