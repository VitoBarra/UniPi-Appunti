---
type: nota
course: Algebra Lineare
topic: Applicazioni Lineari 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]


# Applicazioni Lineari
---

Un’applicazione lineare è una funzione fra spazi vettoriali

$$
f:V\rightarrow W
$$

 compatibile con le operazioni di somma e prodotto per scalare quindi è lineare se

- $f(0)=0$
- $f (v + w) = f (v ) + f (w)$ per ogni $v,w\in V$
- $f (\lambda v ) = \lambda f (v)$  per ogni $v \in V$   e $\lambda \in K$

### esempi di applicazioni lineari:

sia $A \in M(m,n,\mathbb{K})$  e $f: \mathbb{K}^n\rightarrow \mathbb{K}^m$

- $f(v) = A v$  una funzione parametrizzata da $A$
    - $f(v)=0$ l’applicazione banale con $A$ è la matrice nulla
    - $id_V(v)$ o $id(v) = v$ l’applicazione indetta  con $A$  è la matrice $I_n$

questo esempi generale vale anche per i capi $\mathbb{K}$ con dimensione minore

- $f:\mathbb{K}^n \rightarrow \mathbb{K}$
- $f:\mathbb{K} \ \ \rightarrow \mathbb{K}$

dove $A$ diventa un $\lambda \in \mathbb{K}$ e l input un vettore o un numero

### esempi di applicazioni *non* lineari:

- $f(x)= 2x+1$ non sodisfa l’ assioma 1
- $f(x) = x^2$ non soddisfa l’ assioma 2

>La composizione di applicazioni lineari resta lineare
