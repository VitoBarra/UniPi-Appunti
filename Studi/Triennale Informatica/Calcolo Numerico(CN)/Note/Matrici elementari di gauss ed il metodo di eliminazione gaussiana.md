---
Course: Calcolo Numerico
topic: nota
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
1. Le matrici elementare di gauss sono matrici [[Matrici quadrate|triangolari inferiori]]  con elementi uguali ad 1 sulla diagonale principale. per _queste due ragioni_ questa è [[Matrice inversa|invertibile]]
2. Se $E = I_n-ve^T_k$ è una matrice elementare di gauss sua _inversa_ è  $E^{-1}= I_n+v_e^T$ infatti vale$$
\begin{array}{}
EE^{-1} & =& (I_n-ve_k^T)(I_n+ve^T_k)\\
I_n+ve_k^T-ve_k^T-ve^T_kve^T_k & = &  I_n -v(e^T_kv)e_k^T \\
I_{n}+v0e_k^T  & = & I_{n} 
\end{array}$$ ^714b11
3. _Sia_ $x \in \mathbb{R}^n$ con $x_k \not = 0$. _allora_ esiste un matrice elementare di gauss $E \in \mathbb{R}^{n \times n}$ tale che $Ex= [x_1,\dots,x_k,0,\dots,0]^T$ ovvero che annulli tutti gli elementi della colonna $>k$. per _dimostrare_ questa proprietà abbiamo dalla definizione che $E=I-ve^T_{k}$ e da qui vediamo che $$x_j-v_jx_k=0 \iff v_j= \frac{x_j}{x_k}, \ \ k+1 \leq j \leq n$$ ^5ab199
	-  $x_j-v_jx_k=0$ viene direttamente dalla _moltiplicazione_ $Ex$ 
4. Se $E_{k}=I_n-ve_k^T$ e $E_{h} = I_n-we_h^T$ son matrici elementare  di gauss con $h > k$ allora $e^T_kw=0$ e dunque $$
   \begin{array}{}
   E_{k}\cdot  E_{h}  & = & (I_n-ve_k^T)(I_n-we_h^T)\\
    I-ve_k^T -we_h^T +v(e_k^Tw)e_h^T& = &I-ve_k^T -we_h^T +v0e_h^T \\
 I_n-ve^T_k-we^T_h &  & 
	\end{array}
   $$ciò implica che la matrice prodotto risulta costruita semplicemente apponendo nella corretta posizione i vettori $v$ e $w$  ![[Pasted image 20230517170805.png]] ^62bbc3
5. sia $E=I_n-ve^T_k$ una _matrice eleminare di gauss_ e $y$ un _vettore_ il prodotto $Ey$  può essere calcolata con al più $O(n-k)$ operazioni moltiplicative. si ha infatti che $$Ey=z\implies \begin{cases}
 z_j=y_j &per& 1 \leq j \leq k \\
 z_j=y_j-v_jy_k & per &j >k
\end{cases}
$$
### Metodo di eliminazione gaussiana
Questo è un metodo che sfrutta le prosperità delle matrici elementari di gauss per trasformare una matrice  in una matrice triangolare superiore applicando essenzialmente il modo sistematico il [[Mosse di Gauss|metodo di gauss]]

si indicano con $a_{1}^{(k)},\dots,a_{n}^{(k)}$ i vettori colonna di $A_{k} = a_{i,j}^{(k)}$ con  $n \leq i,j\leq n$ e $0 \leq k\leq n$

_Assumendo_ $a_{1,1}^{(0)} \not = 0$ allora per la [[#^5ab199|properita 3]]  posso determinare $E_{1}$ _tale che_$$E_{1}\boldsymbol a_{i}^{(0)}=[a_{1,1}^{(0)},0,\dots,0]^{T}$$
con $$E_{1}=I_{n}-\left[0,\frac{a_{2,1}}{a_{1,1}^{(0)}},\frac{a_{3,1}}{a_{1,1}^{(0)}}, \dots,\frac{a_{n,1}}{a_{1,1}^{(0)}}\right]^{T}e^T_{1}$$
i termini $m_{2,1}^{(0)}=\frac{a_{2,1}}{a_{1,1}^{(0)}},m_{3,1}^{(0)}=\frac{a_{3,1}}{a_{1,1}^{(0)}}, \dots,m_{n,1}^{(0)}=\frac{a_{n,1}}{a_{1,1}^{(0)}}$ sono detti _moltiplicatori di gauss_ mentre $a_{1,1}$ é detto __pivot__

abbiamo dunque che 
$$A_{1}=E_{1}A_{0}, \ \ \ \ b_{1} = E_{1}b_{0} $$
![[Pasted image 20230531173721.png]]

a questo punto alla fine del processo abbiamo che 
$$E_{n-1}E_{n-2}\dots,E_{1}A_{0}=A_{n-1} =R$$
con $R$ una matrice [[Matrici quadrate|triangolare superiore]] 

possiamo riscrivere le relazioni $A_{k}=E_{k}A_{k-1}$ e $b_{k}=E_{k}b_{k-1}$ in termini di componenti e abbiamo 
$$
\begin{array}{}

A_{k} & = & \begin{cases}
a_{i,j}^{(k)}=a_{i,j}^{(k-1)}  & if & i \leq k \lor j \leq k-1 \\
a_{i,k}^{(k)} = 0  & if & i>k \\
a_{i,j}^{(k)} = a_{i,k}^{(k-1)}-m_{i,k}^{(k-1)}b_{k}^{(k-1)} & if & i>k \land j>k
\end{cases} \\ \\ \\

b_{k} & = &  \begin{cases}
b_{i}^{(k)}=b_{i}^{(k-1)}  &  if & i \leq k \\
b_{i}^{(k)}=b_{i}^{(k-1)}-m_{i,k}^{(k-1)}b_{k}^{(k-1)}  & if  & i>k
\end{cases}
\end{array}
$$
 e la risoluzione del sistema lineare $Ax=b$ viene ricondotta alla soluzione del sistema triangolare
 $$Rx=b_{n-1}$$
 e risulta che 
 $$A=E_{1}^{-1}\dots E_{n-1}^{-1}R $$
 Dalla [[#^714b11|proprieta 2]] segue che le _[[Matrice inversa|inverse]]_ delle matrici elementari sono matrici elementari ottenute semplicemente cambiando il segno del vettore $v$. Dalla [[#^62bbc3|proprieta 4]] segue che il prodotto delle matrici elementari $$L = E_{1}^{-1}\dots E_{n-1}^{-1}$$è determinato apponendo nel corretto ordine i moltiplicatori di Gauss
 ![[Pasted image 20230531175458.png]]
applicando questo metodo si ha che la [[Complessita|complessita]] del calcolo della fattorizzazione e la risoluzione del sistema risulta $$\sum^{n-1}_{k=1}k^{2}+2\sum^{n-1}_{k=1}k = \frac{n^{3}}{3}+O(n^{2}) = O(n^{3})$$
operazioni moltiplicative