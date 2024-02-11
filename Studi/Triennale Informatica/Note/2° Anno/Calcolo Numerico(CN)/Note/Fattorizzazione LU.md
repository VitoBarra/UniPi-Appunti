---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Fattorizzazione LU
---
_Data_ una [[Matrice|matrice]] $A \in \mathbb{R}^{n\times n}$ si dice fattorizzai le nella forma LU se esistono $U\in \mathbb{R}^{n\times n}$  [[Matrici quadrate|matrice triangolare superiore]] ed $L\in \mathbb{R}^{n\times n}$ [[Matrici quadrate|matrice triangolare inferiore]] con elementi uguali ad $1$ sulla diagonale principale tali che $A = L\cdot U$ 

Se $A \in \mathbb{R}^{n\times n}$ [[Matrice inversa|invertibile]] il suo $\det(A)\not = 0$  ed è fattorizzabile in forma $LU$ allora dal [[Teorema di Binet|Teorema di Binet]]  abbiamo $\det(LU) =\det(L)\det(U)\not=0$ con $\det(L)=1$ sempre. quindi anche  $U$ è invertibile, dunque il [[Sistemi lineari e lineari omogenei|sistema lineare]] $Ax = b$ può essere risolto mediante la sequenza di sistemi triangolare 
$$\begin{cases}
Ly=b \\
Ux=y
\end{cases}
$$
## Teorema di unicità
_Sia_ $A_k \in \mathbb{R}^{k\times k}$  una _sottomatrice minore di testa_ di $A \in \mathbb{R}^{n\times n}$ con $1\leq k\leq n$ 
_se_ sono [[Matrice inversa|invertibili]] tutte i $k= 1,\dots,n-1$ minori di testa
_allora_ esiste _un unica_ fattorizzazione $LU$ di $A$

> [!warning] 
> questo teorema da solo delle condizioni _sufficienti_ ma _non necessarie_. quindi se non sono soddisfatti i criteri non possiamo dire nulla sul esistenza della fattorizzazione 

#### Dimostrazione
dimostriamo per induzione sulla dimensione $n$ della matrice. Per il caso $n=1$ vale
$A=[a] = [1][a]$ ed è _l unica fattorizzazione_ $LU$ di $A$

Supponiamo il teorema vero per matrici di ordine $m \leq n-1$ e dimostriamo per una matrice $A$ di ordine $n$ 

la relazione $A = LU$ può essere riscritta come 
$$
 \left[
 \begin{array}{c|c}
  A_{n-1} &z \\
  \hline
  v^T & \alpha
 \end{array} 
 \right] = 
 \left[
 \begin{array}{c|c}
  L_{n-1} & 0 \\
  \hline 
  w^T & 1
 \end{array} 
 \right] 
 \cdot
 
 \left[
 \begin{array}{c|c}
  U_{n-1} &y \\
  \hline
  0^T & \beta
 \end{array} 
 \right] 
$$
dove la matrice $A$ e le matrici incognite $L$ ed $U$ sono partizionate a blocchi con $A_{n-1}, L_{n-1}, U_{n-1} \in \mathbb{R}^{(n-1) \times (n-1)}$  questa relazione è equivalente al sistema di equazioni
$$
\begin{cases}
A_{n-1} = L_{n-1}U_{n-1} \\
z = L_{n-1}y\\
v^{T}= w^{T}U_{n-1} \\
\alpha = w^Ty + \beta
\end{cases}$$
per ipotesi del teorema le Sottomatrici $A_1, \dots,A_{n-2}$ delle matrice $A_{n-1}$ sono invertibili per cui  per _ipotesi induttiva_ posso concludere l esistenza e l unicità della fattorizzazione $LU$ di $A_{n-1}$.

dimostro quindi per $A_{n}$
Siano  $L_{n-1}$ ed $U_{n-1}$ i fattori triangolari di $A_{n-1}$ per ipotesi del teorema $A_{n-1}$ è invertibile quindi $U_{n-1}$ è invertibile e quindi i sistemi lineare che definiscono la seconda e terza equazione ammettono soluzione unica. dati infine $w$ e $y$ l ultima equazione permette di determinare univocamente il valore di $\beta$ 


