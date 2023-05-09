---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Matrici elementari di gauss ed il metodo di eliminazione gaussiana
---

### Matrice Elementare di gauss
una matrice $E \in \mathbb{R}^{n \times n}$ si dice elementare di gauss se esiste $k \in \mathbb{N}$ con $1 \leq k \leq n$ e $v \in \mathbb{R}^n$ con $v_1 = \dots v_k=0$ tale che 
$$E = I_n-ve_k^T$$
dove $e_k$ indica il $k-$esimo vettore della [[Base di uno spazio vettoriale#Basi canoniche|base coranica]] in $\mathbb{R}^n$ 

valgono le Seguenti _proprietà_
1. Le matrici elementare di gauss sono matrici [[Tipi di matrice quadrata|triangolari inferiori]] [[Matrice inversa|invertibili]] con elementi uguali ad 1 sulla diagonale principale 
2. Se $E = I_n-ve^T_k$ è una matrice elementare di gauss akita $E^{-1}= I_n+v_e^T$ infatti vale $$(I_n-ve_k^T)(I_n+ve^T_k)= I_n+ve_k^T-ve_k^T-v(e^T_kv)e^T_k=I_n$$
3. Sia $x \in \mathbb{R}^n$ con $x_k \not = 0$. allora esiste un matrice elementare di gauss $E \in \mathbb{R}^{n \times n}$ tale che $Ex= [x_1,\dots,x_k,0,\dots,0]^T$ infatti basterà porre $E=I_n-ve_k^T$ con $$x_j-v_jx_k=0 \iff v_j= \frac{x_j}{x_k}, \ \ k+1 \leq j \leq n$$
4. Se $E=I_n-ve_k^T$ e $\hat E = I_n-we_\ell^T$ son matrici elementare i di gauss con $\ell > k$ allora $e^T_kw=0$ e dunque $$E\cdot \hat E = I_n-ve^T_k-we_\ell$$ciò implica che la matrice prodotto risulta costruita semplicemente apponendo nella corretta posizione i vettori $v$ e $w$ dei fattori 
5. il prodotto $Ey$ di una matrice  elementare di gauss $E= I_n-ve^T_k$ per un vettore puo essere calcolat con al poi $n-k$ operazioni moltiplicative. si ha infatti che $$Ey=z\implies \begin{cases}
 z_j=y_j &per& 1 \leq j \leq k \\
 z_j=y_j-v_jy_k & per &j >k
\end{cases}
$$
