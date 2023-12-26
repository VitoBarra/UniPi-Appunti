---
type: nota
course: Algebra Lineare
topic: Applicazioni Lineari
tags:
  - AL
Parent MOC: "[[Algebra Lineare (AL)]]"
---

# Applicazioni Lineari
---
_siano_ $V$ e $W$ due [[Spazio Vettoriale|spazi vettoriali]]
_allora_ Un’_applicazione lineare_ è una [[Funzioni|funzione]] fra [[Spazio Vettoriale|spazi vettoriali]]$$f:V\rightarrow W$$che soddisfano i seguenti assiami
- $f(0)=0$
- $f (v + w) = f (v ) + f (w)$ per ogni $v,w\in V$
- $f (\lambda v ) = \lambda f (v)$  per ogni $v \in V$   e $\lambda \in\mathbb{K}$

##### Esempi di applicazioni lineari
sia $A \in M(m,n,\mathbb{K})$ una [[Matrice|matrice]] e $f: \mathbb{K}^n\rightarrow \mathbb{K}^m$
- $f(v) = A v$  una funzione parametrizzata da $A$
    - $f(v)=0$ l’applicazione banale con $A$ è la matrice nulla
    - $id_V(v)$ o $id(v) = v$ l’applicazione indetta  con $A$  è la matrice $I_n$

questo esempi generale vale anche per i capi $\mathbb{K}$ con dimensione minore

- $f:\mathbb{K}^n \rightarrow \mathbb{K}$
- $f:\mathbb{K} \ \ \rightarrow \mathbb{K}$

dove $A$ diventa un $\lambda \in \mathbb{K}$ e l input un vettore o un numero

##### Esempi di applicazioni *non* lineari
- $f(x)= 2x+1$ non sodisfa l’ assioma 1
- $f(x) = x^2$ non soddisfa l’ assioma 2


#### Teoria
La _composizione_ di _applicazioni lineari_ resta _lineare_
