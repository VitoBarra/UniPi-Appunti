---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: "[[Integrazione numerica]]"
SubTopic:
---
# Integrazione Monte Carlo
---
L __integrazione monte carlo__ è un modo per fare [[Integrazione numerica|Integrazione numerica]] ed è un algoritmo di tipo [[Algoritmi Randomizzati#Algoritmi Randomizzati|monte carlo]].

si vuole calcolare l [[Integrali|integrale]] $\int ^b_af(x)\, dx$   a partire da $n$ sample della funzione $f$ scelti in modo [[Sequenza casuali|random]]
allora partendo dal fatto che 
_sia_ $g(x)$ una funzione dotata di [[Variabili aleatoria - Momenti|momento primo]] $E[g(x)]=\int ^b_ag(x)p(x) \, dx$ (la media)
_allora_ $E[g(x)]$ puo essere approssimato come $$E[g(x)]\approx \cfrac{1}{n}\sum^n_{i=1}g(x_i)$$ considerando ora in particolare $g(x)=\cfrac{f(x)}{p(x)}$  e allora vale che $$
\begin{align}
I & =\int _b^af(x) \, dx=\int _b^a \cfrac{f(x)}{p(x)}p(x) \, dx = E[g(x)] \implies \\
I & \approx \cfrac{1}{n}\sum^n_{i=1}\cfrac{f(x_i)}{p(x_i)}
\end{align}
$$ e possiamo scegliere arbitrariamente la [[Distribuzione di probabilità|distribuzione]] quindi prendendo la [[Probabilita con distribuzione uniforme|distribuzione uniforme]] $p(x)=\cfrac{1}{b-a}$  si ha che 
$$I \approx \cfrac{1}{n}\sum^n_{i=1}\cfrac{f(x_i)}{p(x_i)}=\cfrac{1}{n}\sum^n_{i=1}f(x_i)(b-a)$$
che intuitivamente significa che stimo facendo la media della somma del aria di $n$ rettangoli larghi quando l intervallo di integrazione $[a,b]$ e alti quanto il valore del sample $f(x_i)$
![[Pasted image 20240311041145.png]]

[source ](https://en.wikipedia.org/wiki/Monte_Carlo_integration)