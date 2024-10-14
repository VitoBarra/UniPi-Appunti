---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Funzione di Ripartizione
---
in [[Statistica descrittiva|statistica]] una _funzione di ripartizione_ è modo per descrivere un vettore dei dati Numerici

### Funzione di ripartizione empirica (definizione)
_sia_ $x$ un vettore ordinato in modo cresce di dati 

la _funzione di ripartizione_ empirica $F_e(.): \mathbb{R} \rightarrow \mathbb{R}$  su $\mathbb{R}$  è definita come$$
F_e(t)=\frac{\#\{x_i|x_i\leq t\}}{n}
$$
per questa [[Funzioni|funzione]] vale che 
- è debolmente crescente
- per $\forall t <x_1$ è $F_{e}(t)=0$
- per $\forall t \geq x_n$ è $F_{e}(t)  = 1$
è una funzione a "gradoni" che al aumentare di $t$ ogni volta che incontra un dato fa un salto di $\cfrac{1}{n}$ se ci sono $m$ dati uguali, il salto è di $\frac{m}{n}$ 

alcuni esempi sono:
il vettore di dati $(1.2,-0.7,3.4,1.6,2.1)$ quindi riordinando $(-0.7,1.2,1.6,2.1,3.4)$ e si traccia la funzione
	![[UniPi INF/Note/2° Anno/Statistica/Media/Untitled 5.png]]

nel caso di un vettore con 65 elementi gli scalini sono molto meno “visibili”
	![[UniPi INF/Note/2° Anno/Statistica/Media/Untitled 6.png]]
