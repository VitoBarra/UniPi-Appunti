---
Subject: "[[UniPi-Appunti/Studi/Triennale Informatica/Note/1° Anno/Analisi/Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: "[[Integrazione numerica]]"
SubTopic: 
---
# Integrazione numerica - Quadratura numerica
---
La __quadratura numerica__ è un modo per fare [[Integrazione numerica|Integrazione numerica]].

Si prendono $n$ campioni dalla funzione $f$ in modo che questi siano equidistanti l uno dal latro e si approssima l integrale con i valori delle rettangoli corrispondenti e quindi vale che 
$$\int ^b_a f(x) \, dx  \approx \sum^n_{i=1}f(x_i)\cfrac{b-a}{n}$$
con $x_i=a+\left(i-\cfrac{1}{2}\right)\cfrac{b-a}{n}$  e rappresenta il contro del $i$-esimo rettangolo
![[Pasted image 20240311034754.png]]