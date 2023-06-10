---
type: nota
course: Algebra
topic: 
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Minimo comune multiplo tra polinomi
---


### Definizione
Sia $f, g \in \mathbb{Q}[x]$ il _Minimo comune multiplo_ è definito come il polinomio monico di grado minimo nel insieme  
$$S= \{h \in \mathbb{Q}[x]-\{0\} \ \ \mid \ \  f\mid h,\ \ \ g \mid h\}$$
$S$ non è vuoto (forse) siccome al minimo c è $f*g$ e quindi esiste il piu piccolo intero positivo $d$ tale che $S \cap P_d[x] \not = \emptyset$ 
$S \cap P_d[x]$ contiene un [[Polinomi|polinomio]] monico $h$. questo è unico

#### Dimostrazione unicità di $h$
supponiamo $\tilde{h}$ un altro polinomio monico e  $\tilde{h} \in S \cap P_d[x]$ 
allora poiché  $h,\tilde{h}$ sono polinomi monico di grado $d$ allora $h - \tilde(h)$ o è $=0$ o un piloto io con grado $<d$
- $=0 \implies h = \tilde{h}$
- $\not =0 \implies$
	- $$f \mid h \ \ \ \ \ f \mid \tilde{h} 
	\ \ \ \ \ \ g \mid h \ \ \ \ \ g \mid \tilde{h} \implies \\
		f\mid(h-\tilde{h}) \ \ \ g\mid(h-\tilde{h})
	$$
	quindi  $h - \tilde{h}$ è un elemento di $S$ di grado strettamente inferiore rispetto ad $h$ e $\tilde{h}$ il che è una contraddizione 
	

