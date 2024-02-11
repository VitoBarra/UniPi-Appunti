---
Course: "[[Algebra Lineare (AL)]]"
topic: 
tags:
  - AL
---

# Matrice inversa
---
_sia_ una [[Matrice|matrice]] $A \in M(n)$ 
_allora_ la sua _inversa_ denotata con $A^{-1}$ è una altra matrice tale che
$$
AA^{-1}=A^{-1}A=I_n
$$

> [!warning ] Non tutte le matrice sono invertibili
>una matrice non invertibile è chiamata anche _singolare_ questa è invertibile se una di queste cose _equivalenti_  è vera:
>- $Det(A) \not= 0 \iff$
>- Tutti gli [[Autovettori e Autovalori| autovalori]] sono $\lambda_i \not = 0 \iff$
>- i nucleo [[Nucleo]] deve essere $ker (A) = \{0\} \iff$
>-  il  [[Rango]] pieno avvero $rank(A) = Dim(A)$  [[Dimensione di uno spazio vettoriale| ^]] 
>
>in piu anche se 
>- ha [[Predominanza diagonale]]
>


Nella pratica basta vedere se una colonna e una riga sono composte da tutti zero, se è questo il caso allora è _non invertibile_, eventualmente se non si vede subito si può controllare dopo aver ridotto a scalino con il metodo [[Mosse di Gauss|gauss-giornad]]


> [!note] invertibilità e sistemi lineari
> se una matrice é invertibile il suo [[Sistemi lineari e lineari omogenei|sistema lineare associato]] ha un _unica_ soluzione [[Soluzioni di un sistema lineare|soluzione]] siccome una matrice invertibile implica [[Funzioni#Funzione Iniettiva|iniettiva]] e [[Funzioni#Funzione surgettiva|suriettiva]] della _funzione_ che esprimono

##### Proprietà
- $(AB)^{-1} = A^{-1} B^{-1}$

### Algoritmo per ricavare la matrice inversa

 Si prende la matrice $n × (2n)$

$$
C = (A|l_n)
$$

ottenuta affiancando $A$ e la matrice identità $l_n$. Trasformiamo quindi $C$ usando l’algoritmo di Gauss-Jordan. Se $rk(A) = n$, alla fine dell’algoritmo tutti i pivot stanno nelle prime $n$ colonne. In particolare abbiamo ottenuto una nuova matrice $n × (2n)$

$$
 C' = (I_n | A^{-1})
$$
