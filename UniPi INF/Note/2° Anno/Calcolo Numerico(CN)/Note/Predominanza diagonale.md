---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Predominanza diagonale
--- 
una [[Matrice|matrice]] $A \in \mathbb{C}^{n \times n}$ si dice a _predominanza diagonale_ per riga se vale 
$$|a_{ii}| > \sum^n_{j=1,j\not=i}|a_{i,j}| \ \ \ \forall i = 1,\dots,n$$

### Teorema 
Se $A$ è a predominanza diagonale allora $A$ è [[Matrice inversa|invertibile]] 

#### Dimostrazione
bisogna verificare che $\lambda =0$ non sia un [[Calcolare autovalori e autovettori|autovalore]] di $A$ 
lo facciamo utilizzando [[Localizzazione degli Autovettori#Teorema di Gershgorin|cerchi di Gershgorin]] e dobbiamo mostrare che $\lambda = 0 \not \in \cup^n_{i=1}K_i$

$$|a_{ii}| = |0- a_{ii}| > \sum^{n}_{j=1,j\not=i}|a_{i,j}| \ \ \ \forall i = 1,\dots,n$$
da questo è in contrasto con la definizione di [[Localizzazione degli Autovettori#Teorema di Gershgorin|cerchi di Gershgorin]] che vuole le relazione opposta. quindi posso concludere 
$$0 \not\in K_i $$
siccome 
$$K_i= \{z \in \mathbb{C}: |z-a_{i,i}| \leq \sum^{n}_{j=1,j\not=i}|a_{i,j}|\}$$
e se $0$ appartenesse  a $K_i$ avremmo $z=0$ ma ciò contradice con la definizione quindi $0 \not\in K_i$ 