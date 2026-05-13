---
Course: "[[Analisi]]"
tags:
  - Analisi
topic: nota
---
# Funzioni Convesse-Concave
Le **funzioni convesse e concave** sono [[Funzioni|funzioni]] il cui grafico sta rispettivamente sotto o sopra i segmenti che uniscono coppie di punti del grafico stesso.

Se il dominio di una funzione $f$ è un intervallo $I=[a,b]$, allora $I$ è un [[Convessita|insieme convesso]]: quindi per ogni $x_1,x_2\in I$ e per ogni $\lambda\in[0,1]$ anche la [[Convessita#Combinazione convessa|combinazione convessa]] $\lambda x_1+(1-\lambda)x_2$ appartiene a $I$.

- Una funzione $f$ è **convessa** in un intervallo $I$ se per ogni $x_1,x_2\in I$ e per ogni $\lambda\in[0,1]$ vale:
$$f(\lambda x_1+(1-\lambda)x_2)\leq \lambda f(x_1)+(1-\lambda)f(x_2)$$
- Una funzione $f$ è **concava** in un intervallo $I$ se per ogni $x_1,x_2\in I$ e per ogni $\lambda\in[0,1]$ vale:
$$f(\lambda x_1+(1-\lambda)x_2)\geq \lambda f(x_1)+(1-\lambda)f(x_2)$$
![[IMG - concavita di una funzione.png]]


Se $f$ è due volte [[Derivate|derivabile]] in un intervallo $I$, allora:
- $f$ è convessa se e solo se $f''(x)\geq 0$ per ogni $x\in(a,b)$;
- $f$ è concava se e solo se $f''(x)\leq 0$ per ogni $x\in(a,b)$.

![[IMG - funzioni immagini concave e convesse.gif]]
- Se $f$ è **convessa**, ogni minimo locale è anche minimo globale.
- L'insieme dei punti di minimo di una funzione convessa è un insieme convesso.
- Se $f$ è **strettamente convessa**, allora il minimo globale, se esiste, è unico.
- Se $f$ è **concava**, ogni massimo locale è anche massimo globale.
- Se $f$ è **strettamente concava**, allora il massimo globale, se esiste, è unico.
