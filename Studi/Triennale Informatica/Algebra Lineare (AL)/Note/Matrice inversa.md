---
Course: "[[Algebra Lineare (AL)]]"
topic: 
tags:
  - AL
---

# Matrice inversa
---
_sia_ una [[Matrici|matrice]] $A \in M(n)$ 
_allora_ la sua _inversa_ denotata con $A^{-1}$ è una altra matrice tale che
$$
AA^{-1}=A^{-1}A=I_n
$$

> [!warning ] Non tutte le matrice sono invertibili
>una matrice non invertibile è chiamata anche _singolare_ questa è invertibile se una di queste cose _equivalenti_  è vera:
>- $Det(A) \not= 0 \iff$
>- Tutti gli [[Autovettori e Autovalori| autovalori]] sono $\lambda_i \not = 0 \iff$
>- i nucleo [[Nucleo di un applicazione lineare]] deve essere $ker (A) = \{0\} \iff$
>-  il [[Rango]] pieno avvero il rango è uguale alla [[Dimensione di uno spazio vettoriale| dimensione dello spazio vettoriale]]  $rank(A) = Dim(A)$  
>
>in piu anche se 
>- ha [[Predominanza diagonale]]
>


Nella pratica basta vedere se una colonna e una riga sono composte da tutti zero, se è questo il caso allora è _non invertibile_, eventualmente se non si vede subito si può controllare dopo aver ridotto a scalino con il metodo [[Mosse di Gauss|gauss-jordan]]


> [!note] invertibilità e sistemi lineari
> se una matrice é invertibile il suo [[Sistemi lineari e lineari omogenei|sistema lineare associato]] ha un _unica_ soluzione [[Soluzioni di un sistema lineare|soluzione]] siccome una matrice invertibile implica [[Funzioni#Funzione Iniettiva|iniettiva]] e [[Funzioni#Funzione surgettiva|suriettiva]] della _funzione_ che esprimono

##### Proprietà
- $(AB)^{-1} = A^{-1} B^{-1}$

### Algoritmo per ricavare la matrice inversa

 Sia $C$ una [[Matrici|matrice]]  $n \times (2n)$ definita come $$C = (A\mid I_n)$$ 
$C$ è ottenuta affiancando ad $A$ la matrice identità $I_n$. 
Trasformiamo  $C$ in modo da ottenere  $A$ in forma Gauss-Jordan.
Se $A$ è invertibile, alla fine dell’algoritmo tutti i pivot stanno nelle prime $n$ colonne. In particolare abbiamo ottenuto $C'$ una nuova matrice  $n\times (2n)$ tale che$$
 C' = (I_n \mid A^{-1})
$$
