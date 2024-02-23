---
Subject: Algebra
topic: nota
tags: ALG
---

Prev: [[Algebra (ALG)]]

# Rappresentazione in base di numeri interi
---
Siano $n\geq 0$ e  $b\geq 2$ interi. allora si dice che $n$ ha una rappresentazione in base $b$ se esiste una sequenza $\{a_0,\dots,a_k\}$ tale che  $0\leq a_j < b$
$$n = \sum_{i=0}^{k} a_ib^i$$
questa stringa si chiama rappresentazione in base $b$ del intero $n$


#### Esistenza e univocità
fissata una base $b \geq 2$ ogni intero $n\geq0$ _puo_ essere rappresentato in base $b$ _univocamente_

##### Dimostrazione esistenza
sia $P(n)$ la preposizione che $n$. ha una rappresentazione in base $b$ allora $P(0)$ è ovviamente vera.
supponiamo che sia vera $p(0)\dots p(k)$ allora
$$k+1 = bq +r, \ \ \\ 0 \leq r <b$$
inoltro poiché $b>1$ sappiamo che $q<k+1$ per ipotesi 
$$q= q_mb^m+\dots+q_0$$
ne segue che 
$$k+1= bq+r=b(q_mb^m+\dots+q_0)+r = q_mb^{m+1}+\dots+q_0b+r$$
è una rappresentazione in di $n$ in base $b$ per [[Tipi di dimostrazione#Dimostrazione per induzione|induzione]] è dimostrato che si può rappresentare e qualsiasi numero
##### Dimostrazione univocità
sia $S$ l insieme di tutti gli interi non negativi che non hanno una rappresentazione unica in base $b$. Se $S$ non è vuoto, ha un elemento più piccolo $n$. chiaramente $n \geq b$ (siccome tutti i numeri fino a $b$ si possono rappresentare direttamente con una cifra).  Siano.
 $$n= a_kb^k + \dots+a_1b+a_0 \ \ \ \ \ \ \ \ \ \ n= c_lb^k+\dots+c_1b+c_0$$
 due diverse rappresentazioni di $n$ in base $b$ possiamo riscriverle mettendo in evidenza una $b$ come
 $$n= (a_kb^{k-1} + \dots+a_1)b+a_0 \ \ \ \ \ \ \ \ \ \ n= (c_lb^{k-1}+\dots+c_1)b+c_0$$
 e rinominando abbiamo 
  $$n=Ab+a_0 \ \ \ \ \ \ \ \ \ \ n= Cb+c_0$$
  dove $0\leq a_0 < b$ e $0 \leq c_0 <b$.
  questo sono espressioni nella forma del [[Teorema della divisione]]. da univocità delle coppie $(q,r)$ del teorema del univocità sappiamo che $A=C$ e $a_0=c_0$.
  - capiamo se $A$ (e quindi anche $C$) hanno due rappresentazioni diverse.
	- questo non è possibile siccome $n$ è gia il minimo numero che ha due rappresentazione diverse e che abbiamo $A<n$ è una contraddizione 
 