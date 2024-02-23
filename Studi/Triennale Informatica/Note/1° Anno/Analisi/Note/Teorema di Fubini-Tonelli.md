---
Subject: "[[UniPi-Appunti/Studi/Triennale Informatica/Note/1° Anno/Analisi/Analisi|Analisi]]"
topic: nota
tags:
  - Analisi
---
# Teorema di Fubini-Tonelli
---

#### Teorema di Fubini-Tonelli 
_Sia_ $A$ un [[Insiemi Misurabili|Insiemi Misurabili]] tale che $A = A_{1}\times A_{2}$
_Se_ $f(x)$ è una [[Funzioni|funzione]] non negativa
_Allora_ $$
\begin{array}{}
\int \int_{A}  f(x,y)\, dx  \, dy=  \\
\int_{A_{1}} \left( \int_{A_{2}}  f(x,y) \, dy \right) \, dx=  \\
\int_{A_2} \left( \int_{A_1}  f(x,y) \, dx \right) \, dy 
\end{array}
$$
ovvero possiamo invertire l ordine di [[Integrali|integrazione]] è il risultato non cambia