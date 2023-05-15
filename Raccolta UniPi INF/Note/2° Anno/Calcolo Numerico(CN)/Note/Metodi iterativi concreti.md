---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Metodi iterativi concreti
---
è un [[Metodi Iterativi|metodi interativo]] utile siccome non c é bisogno di calcolare la matrice di iterazione.
Scompongo la matrice A come
$$A=D-L-U =$$
![[Pasted image 20230510215538.png]]
## metodo di _jacobi_ (metodo spostamenti successivi)

^4e6ab2

e quindi possimao scrivere come $A = M - N$ con 
- $M=D$ 
- $N=L+D$ 
- la mia matrice di interazione $J =D^{-1}(L+U)$
posso applicare questo metodo solo alle matrici con $a_{ii} \not= 0\ \ \ \forall i =1,\dots,n$ ovvero solo a quelle matrici che _NON_ hanno elementi nulli sulla _diagonale_. cosi non fosse $D$ non sarebbe [[Matrice inversa|invertibile]].
quindi il _metodo_ diventa
$$\begin{cases}
x^{(0)} \in \mathbb{K}^n\\
x^{(k+1)} = Jx^{(k)}+D^{-1}b
\end{cases}$$
Possiamo pero riscrivere la seconda espressione come
$$
\begin{array}{}
x^{(k+1)} &=& Jx^{(k)}+D^{-1}b \\
x^{(k+1)} &= &D^{-1}((L+U)x^{(k)}+b)  \\
Dx^{(k+1)} &= &Lx^{(k)}+Ux^{(k)}+b)
\end{array}$$
espandendo le matrici si ottiene
![[Pasted image 20230510223010.png]]
da qui possiamo valutare ogni elemento di $x$ moltiplicando
![[Pasted image 20230510223148.png]]
e da questo possiamo scrivere la relazione 
$$x_i^{(k+1)}= \frac{1}{a_{ii}}\left[ b_{i} - \sum^{i-1}_{j=1} a_{ij}x_{j}^{(k)}- \sum^{n}_{j=i+1}a_{ij}x_j{(k)} \right]$$
- Posso dividere per $a_{ii}$ siccome assumo che siano _diversi_ da 0

### Metodo di  gauss-seidel (metodo di spostamento simultanei)

^32b667

- $M=D-L$ (la parte triangolare inferiore della matrice A)
- $N = U$
- la mia matrice di interazione $G=(D-L)^{-1}U$ 
posso applicare questo metodo solo alle matrci con $a_{ii} \not= 0\ \ \ \forall i =1,\dots,n$ ovvero solo a quelle matrici che _NON_ hanno elementi nulli sulla _diagonale_. cosi non fosse $D-L$ non sarebbe [[Matrice inversa|invertibile]].
quindi il _metodo_ diventa
$$\begin{cases}
x^{(0)} \in \mathbb{K}^n\\
x^{(k+1)} = Gx^{(k)}(D-L)^{-1}b
\end{cases}$$
possiamo Riscrivere la seconda equazione come 
$$
\begin{array}{}
x^{(k+1)} &=& Gx^{(k)}+(D-L)^{-1}b \\
x^{(k+1)} &= &(D-L)^{-1}(Ux^{(k)}+b)  \\
(D-L)x^{(k+1)} &= &Ux^{(k)}+b
\end{array}$$
espandendo le matrici si ottiene
![[Pasted image 20230510232155.png]]
 
e da qui possiamo riscrivere
![[Pasted image 20230510232329.png]]
e da qui si ottiene 
$$x_i^{(k+1)}= \frac{1}{a_{ii}}\left[ b_{i} - \sum^{i-1}_{j=1} a_{ij}x_j^{(k+1)}- \sum^{n}_{j=i+1}a_{ij}x_j^{(k)} \right]$$
- Posso dividere per $a_{ii}$ siccome assumo che siano _diversi_ da 0




### Criterio di Stop
ci sono vari criteri di stop per gli algoritmi che implementano questi metodi.
dato un certa tolleranza di errore $tol$ il criterio _ideale_ sarebbe 
$$\|x^{(k+1)}-x\|\leq tol$$
ma questo non è utilizzabile siccome non conosciamo il valore di $x$ che è la soluzione _vera_
altri criteri sono
- $\|x^{(k+1)}-x^{(k)}\|\leq tol$
- $\cfrac{\|x^{(k+1)}-x^{(k)}\|}{\|x^{(k)}\|}\leq tol$
- $\|Ax^{(k+1)}-b\| \leq tol$
- $\cfrac{\|Ax^{(k+1)}-b\|}{\|x^{(k)}\|}\leq tol$
i vari criteri _NON_ sono equivalenti e restituiranno valori di $k$ diversi. 
#### Teorema
in più in generale se ci si ferma per questi criteri _NON_ è garantito che $\|x^{(k+1)}-x\| \leq tol$

##### Dimostrazione
si vuole dimostrare che $\|x^{(k+1)}-x\| \leq tol$ non sia vero sotto la condizione del utilizzo dei criteri di stop sopra elencati
si sa 
- _l errore_ : $e^{(k+1)}=x^{(k+1)}-x = Pe^{(k)}$

e allora possiamo scrivere
$$
\begin{array}{}
x^{(k+1)}-x^{(k)} &= \\
x^{(k+1)}-x-(x^{(k)}-x) & =  \\
e^{(k+1)}-e^{(k)}& =  \\
Pe^{(k)}-e^{(k)} & = &(P-I)e^{(k)}

\end{array}$$
mettendoci nel ipotesi di convergenza sappiamo
- $p(P)<1 \implies (P-I)$ _[[Matrice inversa|invertibile]]_ 
>[!question]-
>(invertibile siccome se sotraggo 1 alla diagonale e p(P)<1 mi è garantito che la diagonale non si annulli????? (credo valga solo per tiangolari))

e allora possiamo scrivere
$$\begin{array}{}
 e^{(k)}&=&(P-I)^{-1}\cdot (x^{(k+1)}-x^{(k)}) &   \\
\|e^{(k)}\|&=&\|(P-I)^{-1}\cdot (x^{(k+1)}-x^{(k)})\| & \leq \\
&&\|(P-I)^{-1}\|\cdot \|(x^{(k+1)}-x^{(k)})\| & \leq \\
&& \|(P-I)^{-1}\|\cdot tol
\end{array}$$
$\|(P-I)^{-1}\|$ _può_ diventare diventa  _molto grande_ quando il raggio spetrale tende ad 1 ( $p(P) \to 1$). si dice che la matrice $P-I$ sia quasi _singolare_ si avvicina cioè ad non essere invertibile.



#### Teorema di convergenza sufficiente
sia $A \in \mathbb{R}^{n \times n}$, se $A$ è a [[Predominanza diagonale|Predominanza diagonale]]
1. $A$ è invertibile
2. i metodi [[#^4e6ab2|J]] e [[#^32b667|GS]] sono _applicabili_ ovvero $a_{i,i}\not =0 \ \ \forall i = 1,\dots,n$ 
3. I metodi [[#^4e6ab2|J]] e [[#^32b667|GS]] sono _convergenti_

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
	- Assumiamo ora che esiste un _autovalore_ $\lambda \geq 1$ notiamo che $H$ sotto l ipotesi del metodo [[#^4e6ab2|J]] e [[#^32b667|GS]] sia anche essa a predominanza diagonale co porterebbe a dire che questa è invertibile ma questo va in contrasto con ciò che abbiamo dimostrato al passo prima 
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
			siccome ho mostrato che $|\lambda||a_{ii}|>\sum^{i-1}_{j=1}|\lambda a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}|$ allora questa la matrice $H$ per GS è a _predominanza diagonale_
		 per J:
		 ![[Pasted image 20230511023123.png]]
		  siccome ho mostrato che $|\lambda||a_{ii}|>\sum^{i-1}_{j=1}| a_{ij}|+\sum_{j=i+1}^{n}|a_{ij}|$ allora questa la matrice $H$ per GS è a _predominanza diagonale_
		  in questi casi $H$ è invertibile (_non singolare_ ) e questa è una contradizione quindi $|\lambda|<1$ e quindi i due metodi  _convergo_