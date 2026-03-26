---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# Successioni
---
La **successione** e' una [[Funzioni|funzione]] definita sui numeri naturali e a valori reali, cioe' una funzione $$a:\mathbb{N}\to\mathbb{R}$$ il cui valore nel punto $n$ si indica con $a_n$. Una successione si rappresenta quindi come $$a_1,a_2,\dots,a_n,\dots$$

_Sia_ $(a_n)_{n\geq 1}$ una successione reale.
_Allora_ si dice che $(a_n)$ ha [[Limiti|limite]] $l\in\mathbb{R}$ se $$\forall \varepsilon>0\ \exists N\in\mathbb{N}\ \text{tale che}\ |a_n-l|<\varepsilon\ \forall n\geq N$$ e in questo caso si scrive $$\lim_{n\to+\infty}a_n=l$$

Se esiste un limite finito, la successione e' **convergente**; se il limite non esiste oppure e' infinito, la successione e' **divergente**.

Una successione puo' avere proprieta' strutturali rilevanti:
- e' **crescente** se $a_{n+1}\geq a_n$ per ogni $n$;
- e' **decrescente** se $a_{n+1}\leq a_n$ per ogni $n$;
- e' **monotona** se e' crescente oppure decrescente;
- e' **limitata superiormente** se esiste $M\in\mathbb{R}$ tale che $a_n\leq M$ per ogni $n$;
- e' **limitata inferiormente** se esiste $m\in\mathbb{R}$ tale che $a_n\geq m$ per ogni $n$;
- e' **limitata** se e' limitata sia superiormente sia inferiormente.