---
type: nota
course: Algebra Lineare
topic: 
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Matrice inversa
---

### Definizione
sia una matrice $A \in M(n)$ la sua inversa è $A^{-1}$  ovvero una matrice tale che

$$
AA^{-1}=A^{-1}A=I_n
$$

> [!warning ] #### Osservazione
non tutte le matrice sono invertibili
>una matrice è invertibile se una di queste cose _equivalenti_  è vera:
>- $Det(A) \not= 0$
>- Tutti gli [[Autovettori e Autovalori| autovalori]] sono diversi da $0$
>- i nucleo [[Nucleo]] deve essere composto solo dallo $0$
>-  il  [[Rango]] pieno avvero $rank(A) = Dim(A)$  [[Dimensione di uno spazio vettoriale| ^]]


Nella pratica basta vedere se una colonna e una riga sono composte da tutti zero, se è questo il caso allora è _non invertibile_, eventualmente se non si vede subiti si puo controllare dopo avver ridotto a scalino con il metodo [[Mosse di Gauss|gauss-giornad]]

![[Raccolta UniPi INF/Note/1° Anno/Algebra Lineare (AL)/Media/Untitled 12.png]]

Osservazione: se $A$ invertibile $\implies det(A) \not= 0$

### Proprietà:

- $(AB)^{-1} = A^{-1} B^{-1}$

### Algoritmo per ricavare la matrice inversa:

 Si prende la matrice $n × (2n)$

$$
C = (A|l_n)
$$

ottenuta affiancando $A$ e la matrice identità $l_n$. Trasformiamo quindi $C$ usando l’algoritmo di Gauss-Jordan. Se $rk(A) = n$, alla fine dell’algoritmo tutti i pivot stanno nelle prime $n$ colonne. In particolare abbiamo ottenuto una nuova matrice $n × (2n)$

$$
 C' = (I_n | A^{-1})
$$

### esempio:

$$
\begin{pmatrix}
2 & 1 &| &1&0 \\
1 & 1 &| &0&1
\end{pmatrix}
\rightarrow
\begin{pmatrix}
1 & 0 &| &1&-1 \\
1 & 1 &| &0&1
\end{pmatrix}
\rightarrow
\begin{pmatrix}
1 & 0 &| &1&-1 \\
0 & 1 &| &-1&2
\end{pmatrix}
$$
