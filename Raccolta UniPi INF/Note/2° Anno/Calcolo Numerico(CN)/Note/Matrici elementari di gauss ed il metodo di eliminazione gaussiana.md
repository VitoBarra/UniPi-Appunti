---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Matrici elementari di gauss ed il metodo di eliminazione gaussiana
---
il metodo di eliminazione gaussiana è la formalizzazione per una facile scrittura del algoritmo delle  [[Mosse di Gauss|metodo di gauss]] per le risoluzione del sistemi lineari


### Matrice Elementare di gauss
una matrice $E \in \mathbb{R}^{n \times n}$ si dice elementare di gauss se esiste $k \in \mathbb{N}$ con $1 \leq k \leq n$ e $v \in \mathbb{R}^n$ con _le prime_ $k$ _componenti_ $v_1 = \dots v_k=0$ tale che 
$$E = I_n-ve_k^T$$
dove $e_k$ indica il $k-$esimo vettore della [[Base di uno spazio vettoriale#Basi canoniche|base coranica]] in $\mathbb{R}^n$ 

>[!example]-
>$k=2$ e $v=\begin{bmatrix}0 & 0 & v_{3} &  \cdots & v_{n}\end{bmatrix}$
>
>$$\begin{array}
E_2 = I_{n}-
\begin{bmatrix} 
 0 \\ 0  \\ v_{3}  \\ \vdots  \\ v_{n} 
\end{bmatrix}
\begin{bmatrix}
0 & 1 & 0 & \cdots & 0 
\end{bmatrix} = \\
\begin{bmatrix} 
 1 &  &  &  &  &   \\
   &  &  &  &  &   \\
   &  &  &  &  &   \\
   &  &  &  &  &   \\
   &  &  &  &  & 1   
\end{bmatrix}-\begin{bmatrix} 
 0 &  &  &  &  & 0 \\
 0 &  &  &  &  & 0 \\
   & v_{3} &  &  & \\ 
   &  &  &  &  &   \\
   & v_{n} &  &  &  
\end{bmatrix}
\end{array}$$
>![[Pasted image 20230517163351.png]]



valgono le Seguenti _proprietà_
1. Le matrici elementare di gauss sono matrici [[Tipi di matrice quadrata|triangolari inferiori]]  con elementi uguali ad 1 sulla diagonale principale. per _queste due ragioni_ questa è [[Matrice inversa|invertibile]]
2. Se $E = I_n-ve^T_k$ è una matrice elementare di gauss sua _invera_ è  $E^{-1}= I_n+v_e^T$ infatti vale$$
   \begin{array}{}
 EE^{-1} & =& (I_n-ve_k^T)(I_n+ve^T_k) & = &  I_n+ve_k^T-ve_k^T-ve^T_kve^T_k & = \\I_n -(e^T_kv)ve_k^T &= & I_{n}+0ve_k^T  & =  & I_{n} 
\end{array}$$
3. _Sia_ $x \in \mathbb{R}^n$ con $x_k \not = 0$. _allora_ esiste un matrice elementare di gauss $E \in \mathbb{R}^{n \times n}$ tale che $Ex= [x_1,\dots,x_k,0,\dots,0]^T$ ovvero che annulli tutti gli elementi della colonna $>k$. per _dimostrare_ questa prosperità abbiamo dalla definizione che $E=I-ve^T_{k}$ e da qui vediamo che $$x_j-v_jx_k=0 \iff v_j= \frac{x_j}{x_k}, \ \ k+1 \leq j \leq n$$
	-  $x_j-v_jx_k=0$ viene direttamente dalla _moltiplicazione_ $Ex$ 
4. Se $E_{k}=I_n-ve_k^T$ e $E_{h} = I_n-we_\ell^T$ son matrici elementare i di gauss con $h > k$ allora $e^T_kw=0$ e dunque 	$$E_{k}\cdot  E_{h} = I_n-ve^T_k-we_\ell$$ciò implica che la matrice prodotto risulta costruita semplicemente apponendo nella corretta posizione i vettori $v$ e $w$ dei fattori ![[Pasted image 20230517170805.png]]
5. sia $E=I_n-ve^T_k$ una _matrice eleminare di gauss_ e $y$ un _vettore_ il prodotto $Ey$  può essere calcolata con al più $O(n-k)$ operazioni moltiplicative. si ha infatti che $$Ey=z\implies \begin{cases}
 z_j=y_j &per& 1 \leq j \leq k \\
 z_j=y_j-v_jy_k & per &j >k
\end{cases}
$$
