---
Course: "[[Algebra Lineare (AL)]]"
tags:
  - AL
---
# Base di  uno spazio vettoriale 
---
_sia_  $V$ uno [[Spazi Vettoriali|spazio vettoriale]]  e  $v_1,\dots,v_n \in V$ una sequenza di vettori 
_allora_ la sequenza è detta _base_ di $V$ se
- I vettori sono tutti tra loro _[[Dipendenza Lineare|indipendenti]]_
- I vettori _[[Sottospazio Vettoriale generato|generano]]_ $V$
e questo puo essere scritta anche come [[Matrici|matrice]] dove ogni colonna è un vettore
#### Basi canoniche
- spazio dei vettori $\mathbb{K}^n$ consistente da esattamente $n$  vettori:$$
    \begin{array}{}
e_1=\begin{pmatrix}
    1\\0\\\vdots\\0
    \end{pmatrix} & 
e_2=\begin{pmatrix} 
    0\\1\\ \vdots\\0
    \end{pmatrix} & 
    \cdots  & 
e_n=\begin{pmatrix}
    0\\0\\\vdots\\1
    \end{pmatrix}
\end{array}
    $$


---

- polinomi $\mathbb{K}[x]$:                                     $1,x,x^2,x^3,\cdots,x^n \cdots$
    - polinomi di grado n $\mathbb{K}_n[x]$:           $1,x,x^2,x^3,\cdots,x^n$

-  spazio delle matrici $M(n,m,\mathbb{K})$:

    $$
    \begin{matrix}
    e_1=
    \begin{pmatrix}
    1 &\cdots& 0\\
    \vdots&\ddots&\vdots\\
    0 &\cdots& 0
    \end{pmatrix}& &
    e_2=
    \begin{pmatrix}
    0 &\cdots& 1\\
    \vdots&\ddots&\vdots\\
    0 &\cdots& 0
    \end{pmatrix}\\
    e_3=
    \begin{pmatrix}
    0 &\cdots& 0\\
    \vdots&\ddots&\vdots\\
    1 &\cdots& 0
    \end{pmatrix}&\cdots&
    e_n=
    \begin{pmatrix}
    0 &\cdots& 0\\
    \vdots&\ddots&\vdots\\
    0 &\cdots& 1
    \end{pmatrix}
    \end{matrix}
    $$
    