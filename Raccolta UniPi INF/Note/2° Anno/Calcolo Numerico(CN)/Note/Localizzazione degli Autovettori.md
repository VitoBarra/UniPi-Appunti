---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Localizzazione degli Autovettori
---
## Teorema di Hirsch
data una matrice $A \in C^{n \times n}$ per ogni [[Norme Matriciali e Norme Vettoriali#Teorema norme matriciali indotte da norme vettoriali|norma matriciale indotta]] vale che per ogni [[Autovettori e Autovalori|autovalore]] di $A$ vale che $|\lambda| \leq \|A\|$ 


questo teorema dice che possiamo locale tutti gli autovalori di una matrice $A$ in un cerchio di raggio $\|A\|$ sul piano complesso  

#### Dimostrazione
$|\lambda| \cdot \|x\| = \|\lambda x\| = \|A x\| \leq \|A\| \cdot \|x\|$  
siccome $\|x\| > 0$ per le proprieta delle norme possiamo dividere tutto per $\|x\|$ e otteniamo $|\lambda| \leq \|A\|$


## Teorema di Gershgorin
data una matrice $A \in \mathbb{C}^{n \times n}$ definiamo cerci di gershgoring $K_i$ con $\ \leq i \leq n$ come
$$K_i= \{z \in \mathbb{C}: |z-a_{i,i}| \leq \sum^{n}_{j=1,j\not=i}|a_{i,j}|\}$$
allora si ha che  se $\lambda$ è un autovalore di $A \implies \lambda \in \cup^n_{i=1}K_1$ 

#### Dimostrazione


## Teorema di Gershgorin 2
se l unione $M-1$ di $k$ cerchi di gershgorin è disgiunta dal unione  dei rimanerne $n-k$  cerchi $M_2$, allora $k$ auto valori appartengono al unione $M_1$ e $n-k$ appartengono a $M_2$ 


### Corollario 
si possono definire anche i cerchi su Gershgorin sulle colonne
$$H_i= \{z \in \mathbb{C}: |z-a_{j,j}| \leq \sum^{n}_{i=1,j\not=i}|a_{i,j}|\}$$

### Corollario
gli [[Autovettori e Autovalori|autovalori]]  devono appartenere sia ai cerchi fatti sulle colonne che quelli fatte sulle righe  ne deriva quindi che gli autovalori appartengono a 
$$\lambda \in (\cup_{i=1}^nK_i) \cap(\cup_{j=1}^nH_j )$$
>[!note]
>l unione dei due cerchi sono uguali solo se la matrice è [[Tipi di matrice quadrata|simmetrica]] 





### Definizione 
una matrice $A \in \mathbb{C}^{n \times n}$ si dice a predominanza diagonale per riga se vale 
$$|a_{ii}| > \sum^n_{j=i,j\not=i} \ \ \ \forall i = 1,\dots,n$$

### Teorema 
Se $A$ è a predominanza diagonale allora $A$ è [[Matrice inversa|invertibile]] 
#### Dimostrazione
bisogno a verificare che $\lambda =0$ non appartiene a $\cup^n_{i=1}K_i$

$$|a_{ii}| = |0- a_{ii}| > \sum^n_{j=i,j\not=i} \ \ \ \forall i = 1,\dots,n$$
da questo passo ragionando sulle definizione si ottiene che 
$$0 \not\in K_i $$
siccome 
$$K_i= \{z \in \mathbb{C}: |z-a_{i,i}| \leq \sum^{n}_{j=1,j\not=i}|a_{i,j}|\}$$
e se 0 appartenesse  a $K_i$ avremmo $z=0$ ma ciò contradice con la definizione quindi $0 \not\in K_i$ 