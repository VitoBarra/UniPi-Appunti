---
Course: Calcolo Numerico
topic: nota
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Localizzazione degli Autovettori
---
## Teorema di Hirsch
_sia_ una matrice $A \in \mathbb{C}^{n \times n}$  e  $\lambda_{i}$ l $i$-esimo [[Autovettori e Autovalori|autovalore]]  di $A$ 
_vale che_ per ogni [[Norme Matriciali e Norme Vettoriali#Teorema norme matriciali indotte da norme vettoriali|norma matriciale indotta]] $$|\lambda_{i}| \leq \|A\| \ \ \ \forall i $$ 
questo teorema dice che possiamo _locale_ tutti gli autovalori di una matrice $A$ in un cerchio di raggio $\|A\|$ sul piano [[Insieme dei Numeri complessi|complesso]]  

#### Dimostrazione
_siano_ $\lambda$ un _autovalore_ e $x$ l _autovettore_ associato a $\lambda$ di $A$ abbiamo quindi $Ax=\lambda x$
e quindi 
$$\begin{array}{}
|\lambda| \cdot \|x\|  & = &  \\
 \|\lambda x\|  & = &  \text{per linearita di } \|\cdot\| \\ 
 \|A x\|  & \leq &  \|A\| \cdot \|x\|
\end{array}
$$
abbiamo che  $\|x\| > 0$ per le _proprietà delle norme_ e quindi 
$$\begin{array}{}
|\lambda|\cdot\| x\|  & \leq & \|A\|\cdot\|x\|    & \implies\\
|\lambda|  &  \leq  &\|A\|
\end{array}$$


## Teorema di Gershgorin
data una matrice $A \in \mathbb{C}^{n \times n}$ definiamo _cerchi di gershgoring_ $K_i$ con $1 \leq i \leq n$ come
$$K_i= \left\{z \in \mathbb{C}: |z-a_{i,i}| \leq \sum^{n}_{j=1,j\not=i}|a_{i,j}|\right\}$$
_se_ $\lambda$ è un [[Autovettori e Autovalori|autovalore]] di $A$
_allora_ si ha che  $$ \lambda \in \cup^n_{i=1}K_i$$
#### Dimostrazione
Sia $\lambda$ _autovalore_ di $A$ con corrispondente autovettore $x$.
La relazione $Ax = \lambda x$ implica che
$$\sum^n_{j=1}a_{i,j}x_{j}=\lambda x_{i} \ \ 1\leq i \leq n$$
da qui 
$$
\begin{array}{}
\sum^n_{j=1}a_{i,j}x_{j} & = & \lambda x_{i} \\
\sum^n_{j=1 , j \not =i}a_{i,j}x_{j}&=&\lambda x_{i} -a_{i,i}x_{i} \\
(\lambda-a_{i,i})x_{i} & = & \sum^n_{j=1,j\not=i}a_{i,j}x_{j}
\end{array}
$$
sia $p$ l indice di $|x_{p}|=\|x\|_{\infty}$  la [[Norme Matriciali e Norme Vettoriali|norma infinito]] ovvero della componente di modulo massimo.
$$(\lambda-a_{p,p})x_{p}=\sum^n_{j=1,j\not=p}a_{p,j}x_{j}$$
e da qui passando ai _valori assoluti_$$\begin{array}{}
|(\lambda-a_{p.p})x_{p}|=|\lambda-a_{p,p}||x_{p}|=\\ \left|\sum^n_{j=1,j\not=p}a_{p,j}x_{j}\right| \leq \sum^n_{j=1,j\not=p}|a_{p,j}||x_{j}|
\end{array}
$$ e siccome $|x_{p}|>0$ per definizione di [[Autovettori e Autovalori|autovettore]] posso dividere è ottenere
$$|\lambda-a_{p,p}|\leq\sum^n_{j=1,j\not=p}|a_{p,j}|\cfrac{|x_{j}|}{|x_{p}|}  $$
ed essendo $|x_{p}|=\|x\|_{\infty}$ posso dire che 
$$\sum^n_{j=1,j\not=p}|a_{p,j}|\cfrac{|x_{j}|}{|x_{p}|} \leq \sum^n_{j=1,j\not=p}|a_{p,j}|$$
e quindi 
$$|\lambda-a_{p,p}| \leq \sum^n_{j=1,j\not=p}|a_{p,j}| $$
e questo implica che  $$\lambda \in K_{p} \ \subset \cup_{i=1}^{n}K_{i}$$_esattamente la tesi_


## Teorema di Gershgorin 2
se l unione $M_{1}$ di $k$ cerchi di Gershgorin è disgiunta dal unione dei rimanerne $n-k$  cerchi $M_2$, allora $k$ auto valori appartengono al unione $M_1$ e $n-k$ appartengono a $M_2$ 


### Corollario 
si possono definire anche i cerchi su Gershgorin sulle colonne
$$H_i= \{z \in \mathbb{C}: |z-a_{j,j}| \leq \sum^{n}_{i=1,j\not=i}|a_{i,j}|\}$$

### Corollario
gli [[Autovettori e Autovalori|autovalori]]  devono appartenere sia ai cerchi fatti sulle colonne che quelli fatte sulle righe  ne deriva quindi che gli autovalori appartengono a 
$$\lambda \in (\cup_{i=1}^nK_i) \cap(\cup_{j=1}^nH_j )$$
>[!note]
>l unione dei due cerchi sono uguali solo se la matrice è [[Matrici quadrate|simmetrica]] 
