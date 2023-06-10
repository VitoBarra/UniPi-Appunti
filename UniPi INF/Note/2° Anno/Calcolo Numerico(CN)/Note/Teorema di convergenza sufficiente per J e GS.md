---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Teorema di convergenza sufficiente per J e GS
---
sia $A \in \mathbb{R}^{n \times n}$, se $A$ è a [[Predominanza diagonale|Predominanza diagonale]]
1. $A$ è invertibile
2. I metodi [[Metodo di jacobi (metodo spostamenti successivi)|J]] e [[Metodo di  gauss-seidel (metodo di spostamento simultanei)|GS]] sono _applicabili_ ovvero $a_{i,i}\not =0 \ \ \forall i = 1,\dots,n$ 
3. I metodi [[Metodo di jacobi (metodo spostamenti successivi)|J]] e [[Metodo di  gauss-seidel (metodo di spostamento simultanei)|GS]] sono _convergenti_

##### Dimostrazione
1. è dimostrato in [[Predominanza diagonale|Predominanza diagonale]]
2. predominanza diagonale quindi vale $$|a_{ii}|> \sum^{n}_{j=1,j \not=i}|a_{ij}|\geq 0 \implies |a_{ii}|>0 \iff a_{ii} \not =0 \  \ \ \ \forall i =1,\dots,n$$
3. sappiamo che il metodo è _convergente_ se il $p(P)< 1$ e quindi $|\lambda|<1 \ \ \ \ \forall \lambda$
	- gli [[Calcolare autovalori e autovettori|autovalori]] $\lambda$  di $P$ sono le radici di $\det(P-\lambda I) =0$ e quindi posso scrivere$$
\begin{array}{}	
0=\det(P-\lambda I) &=& \det(M^{-1}N-\lambda I)&= \\
&& \det(M^{-1}N-\lambda M^{-1}M)&=  \\
&& \det(M^{-1}(N-\lambda M)) &= \\
&& \det(-M^{-1}(\lambda M-N)) &= \\
&& \det(-M^{-1})\cdot \det(\lambda M-N)) &=
\end{array}$$ 
	- per la regola del annullamento del prodotto almeno uno dei due termini finali deve essere 0, il $\det(-M^{-1})$ non può altrimenti M non sarebbe invertibile e ciò ci porta a dire che $\det(\lambda M-N)=0$  e perciò $H = \lambda M-N$ é una matrice [[Matrice inversa|non invertibile]] (_singolare_)
	- Assumiamo ora che esiste un _autovalore_ $\lambda \geq 1$ notiamo che $H$ sotto l ipotesi del metodo [[Metodo di jacobi (metodo spostamenti successivi)|J]] e [[Metodo di  gauss-seidel (metodo di spostamento simultanei)|GS]] sia anche essa a _predominanza diagonale_ e quindi invertibile ma questo va in contrasto con ciò che abbiamo dimostrato al passo prima 
	- per dimostrare che $H$ sia a _predominanza diagonale_ parto dalla definizione $$ \begin{array}{}
        |a_{ii}|&>&\sum^{i-1}_{j=1}|a_{ij}|+\sum^n_{j=i+1}|a_{ij}| 
       \end{array}$$
       e siccome vale $|\lambda|\geq 0$ (per valore assoluto)
$$\begin{array}{}
|\lambda||a_{ii}|&>&|\lambda|\sum^{i1}_{j=1}|a_{ij}|+|\lambda|\sum_{j=i+1}^{n}|a_{ij}|
\end{array} 
$$
	   e siccome vale $|\lambda|\geq 1$ (per _ipotesi_)
		$$\begin{array}{}
 \geq & \sum^{i-1}_{j=1}|\lambda a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}| \\
  \geq & \sum^{i-1}_{j=1}| a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}|
\end{array}$$
		per G.S:
			![[Pasted image 20230511022715.png]]
			siccome ho mostrato che $|\lambda||a_{ii}|>\sum^{i-1}_{j=1}|\lambda a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}|$ allora la matrice $H$ per GS è a _predominanza diagonale_
		 per J:
		 ![[Pasted image 20230511023123.png]]
		  siccome ho mostrato che $|\lambda||a_{ii}|>\sum^{i-1}_{j=1}| a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}|$ allora la matrice $H$ per J è a _predominanza diagonale_
		  in questi casi $H$ è invertibile (_non singolare_ ) e questa è una contradizione quindi $|\lambda|<1$ e quindi i due metodi  _convergo_