---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Base di  uno spazio vettoriale 
---
Una sequenza  di $v_1,\dots,v_n \in V$ vettori dove $V$ è uno [[Spazio Vettoriale|spazio vettoriale]] è detta base se
- I vettori sono indipendenti
- I vettori _generano_ $V$

### Basi canoniche
- spazio dei vettori $\mathbb{K}^n$ consistente da esattamente $n$  vettori:

    $$
    e_1=
    \begin{pmatrix}
    1\\
    0\\
    \vdots\\
    0
    \end{pmatrix}\ \ \ \ \
    e_2=
    \begin{pmatrix}
    0\\
    1\\
    \vdots\\
    0
    \end{pmatrix}\ \ \ \ \
    \cdots \ \ \ \ \

    e_n=
    \begin{pmatrix}
    0\\
    0\\
    \vdots\\
    1
    \end{pmatrix}
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
    