---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Teorema di convergenza sufficiente per J e GS
---
_sia_ $A \in \mathbb{R}^{n \times n}$ una matrice
_se_ $A$ è a [[Predominanza diagonale|Predominanza diagonale]]
_allora_
1. $A$ è invertibile
2. I metodi [[Metodo di jacobi (metodo spostamenti successivi)|J]] e [[Metodo di  gauss-seidel (metodo di spostamento simultanei)|GS]] sono _applicabili_ ovvero $a_{i,i}\not =0 \ \ \forall i = 1,\dots,n$ 
3. I metodi [[Metodo di jacobi (metodo spostamenti successivi)|J]] e [[Metodo di  gauss-seidel (metodo di spostamento simultanei)|GS]] sono _convergenti_

##### Dimostrazione
1. è dimostrato in [[Predominanza diagonale|Predominanza diagonale]]
2. predominanza diagonale quindi vale $$|a_{ii}|> \sum^{n}_{j=1,j \not=i}|a_{ij}|\geq 0 \implies |a_{ii}|>0 \iff a_{ii} \not =0 \  \ \ \ \forall i =1,\dots,n$$
3. per dimostrare la convergenza dei metodi 

osserviamo che per i criteri di convergenza il metodo è _[[Metodi Iterativi per soluzioni di sistemi lineari#2. Teorema condizione necessaria (e sufficiente)|convergente]]_ se il $p(P)< 1$ e quindi $|\lambda|<1 \ \ \ \ \forall \lambda$.

dalla definizione di [[Calcolare autovalori e autovettori|autovalori]] so che gli _autovalori_ $\lambda$  di $P$ sono le _radici_ di $\det(P-\lambda I) =0$ e quindi posso scrivere$$
\begin{array}{}	
 0 & = \\
 \det(P-\lambda I) &=\\  
 \det(M^{-1}N-\lambda I)&= \\
 \det(M^{-1}N-\lambda M^{-1}M)&=  \\
 \det(M^{-1}(N-\lambda M)) &= \\
 \det(-M^{-1}(\lambda M-N)) &= \\
 \det(-M^{-1})\cdot \det(\lambda M-N)) &=
\end{array}$$
dove l ultimo passaggio è possibile grazie al [[Teorema di Binet]]
per la regola del annullamento del prodotto almeno uno dei due termini finali deve essere 0, il $\det(-M^{-1})$ non può altrimenti $M$ non sarebbe invertibile e ciò ci porta a dire che $\det(\lambda M-N)=0$  
ponendo $H = \lambda M-N$ vediamo subito che é una matrice [[Matrice inversa|non invertibile]] (_singolare_)

Dimostriamo [[Tipi di dimostrazione|per assurdo]]  che sotto l ipotesi di _predominanza diagonale_ valga che $\lambda < 1$ Assumendo che esiste un _autovalore_ $\lambda \geq 1$ 
Dobbiamo trovare una contradizione e lo facciamo dimostrando che $H$ è [[Matrice inversa|invertibile]]. 
lo facciamo dimostrando che $H$ sia a _[[Predominanza diagonale|predominanza diagonale]]_. 
partendo dalla definizione abbiamo $$ \begin{array}{}
        |a_{ii}|&>&\sum^{i-1}_{j=1}|a_{ij}|+\sum^n_{j=i+1}|a_{ij}| 
       \end{array}$$e siccome vale $|\lambda|\geq 0$ (per _[[Valore assoluto|valore assoluto]]_)
$$\begin{array}{}
|\lambda||a_{ii}|&>&|\lambda|\sum^{i-1}_{j=1}|a_{ij}|+|\lambda|\sum_{j=i+1}^{n}|a_{ij}|
\end{array} 
$$
e siccome vale $|\lambda|\geq 1$ (per _ipotesi_)		$$\begin{array}{}
 \geq & \sum^{i-1}_{j=1}|\lambda a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}| \\
  \geq & \sum^{i-1}_{j=1}| a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}|
\end{array}$$per G.S:$$H=\lambda M-N=
		\begin{bmatrix}
        \lambda a_{11}  &  a_{12} &  \cdots & a_{1n} \\
        \lambda a_{21}  & \ddots & \ddots  & \vdots \\ \vdots  & \ddots & \ddots  & \vdots \\
         \lambda a_{n1} & \dots & \dots  & \lambda a_{nn}
  
	\end{bmatrix}$$
per la _preminenza diagonale_ deve valere
$$|\lambda a_{ii}|>\sum^{i-1}_{j=1}|\lambda a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}|$$
ma ho gia mostrato che $$|\lambda||a_{ii}|\geq|\lambda a_{ii}|>\sum^{i-1}_{j=1}|\lambda a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}|$$
allora la matrice $H$ per GS è a _predominanza diagonale_ quindi invertibile e quindi _contradizione_


per J:$$H=\lambda M-N=
		\begin{bmatrix}
        \lambda a_{11}  &  a_{12} &  \cdots & a_{1n} \\
        a_{2n}  & \ddots & \ddots  & \vdots \\ \vdots  & \ddots & \ddots  & \vdots \\
          a_{n1} & \dots & \dots  & \lambda a_{nn}
\end{bmatrix}$$
per la _preminenza diagonale_ deve valere
$$|\lambda a_{ii}|>\sum^{i-1}_{j=1}| a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}|$$
ma ho gia mostrato che $$|\lambda||a_{ii}|\geq|\lambda a_{ii}|>\sum^{i-1}_{j=1}| a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}|$$ allora la matrice $H$ per $J$ è a _predominanza diagonale_ quindi invertibile e quindi _contrazione_

generando una _contradizione_ entrambi i casi abbiamo dimostrato che tutti gli auto valori devono essere necessariamente $|\lambda|<1$ e di conseguenza I due metodi _convergono_

