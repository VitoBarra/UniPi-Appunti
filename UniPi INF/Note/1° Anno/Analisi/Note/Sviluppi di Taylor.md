---
type: nota
course: Analisi
topic: 
tags: Analisi
---

Prev: [[Analisi]]

# Sviluppi di Taylor
---
### Sviluppo con Resto di Lagrange
sia $f$ [[Funzioni differenziabili|derivabile]] $n$ volte su un intervallo $I$ e siano $x,x_0 \in I$ allora esiste un punto $\xi$ compreso tra $x$ e $x_0$ con $x>x_0$ tale che  
$$f(x)= \underbrace{\sum^{n-1}_{h=0}\frac{f^{(h)}(x_0)}{h!}(x-x_0)^h}_{P(x)}+ \underbrace{\frac{f^{(n)}(\xi)}{n!}(x-x_0)}_{R_n(x)}$$
dove $P(x)$ è il [[Polinomi|polinomio]] di Taylor mentre $R_n(x)$ è il [[Teorema della divisione tra polinomi|resto del polinomio]] di Taylor


### Sviluppo con il resto di Peano
Sia $f$ una funzione di classe $C^n$ su un intervallo $I$ e siano $x,x_0 \in I$ allora si ha:
$$f(x)=\sum^n_{h=0}\frac{f^{(h)}(x_0)}{h!}(x-x_0)^h+o((x-x_0)^n)$$
