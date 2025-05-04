---
Course: "[[Computational Mathematics for Learning and Data Analisys (CMLDA)]]"
tags:
  - CMLDA
Area: 
topic: 
SubTopic:
---
# Singular Value Decomposition (SVD)
---
La **Singular Value Decomposition (SVD)** è una tecnica fondamentale dell'algebra lineare applicata in numerosi ambiti, dalla compressione delle immagini all'analisi dei dati. Essa fornisce una rappresentazione matriciale che permette di comprendere e manipolare le trasformazioni lineari in modo efficiente e teoricamente solido.

Data una matrice $A \in \mathbb{R}^{m \times n}$, la decomposizione ai valori singolari consiste nell'esprimere $A$ come prodotto di tre matrici:$$
A = U \Sigma V^T
$$dove:

- $U \in \mathbb{R}^{m \times m}$ è una matrice ortogonale le cui colonne sono gli **autovettori** di $AA^T$
- $\Sigma \in \mathbb{R}^{m \times n}$ è una matrice rettangolare diagonale, con elementi non negativi $\sigma_i$ disposti in ordine decrescente lungo la diagonale principale, detti **valori singolari**
- $V \in \mathbb{R}^{n \times n}$ è una matrice ortogonale le cui colonne sono gli **autovettori** di $A^TA$

I valori $\sigma_i$ rappresentano la radice quadrata degli autovalori di $A^TA$ (o equivalentemente di $AA^T$) e riflettono la quantità di "energia" o informazione contenuta nei corrispondenti **modi singolari**. La matrice $\Sigma$ è spesso rappresentata visivamente come una sequenza di ellissi (vedi riferimento all'immagine associata), dove ciascun asse principale ha lunghezza proporzionale a un valore singolare. La decomposizione consente quindi una visione geometrica della trasformazione operata da $A$: rotazione secondo $V^T$, scalatura secondo $\Sigma$ e nuova rotazione secondo $U$.

Nel caso in cui $A$ non sia quadrata o abbia rango non massimo, i valori singolari nulli corrispondono a direzioni in cui la trasformazione schiaccia completamente lo spazio. Questo aspetto è essenziale, ad esempio, nella riduzione dimensionale (come discusso nella nota sulla PCA), dove si può approssimare $A$ tramite una matrice a rango ridotto conservando solo i primi $k$ valori singolari:

$$
A_k = U_k \Sigma_k V_k^T
$$

Questa approssimazione, detta **troncamento SVD**, minimizza l'errore in norma di Frobenius rispetto a ogni altra matrice di rango $k$.

La SVD si rivela inoltre cruciale nella risoluzione di sistemi lineari sovradeterminati e nella pseudoinversa di Moore-Penrose, data da:

$$
A^+ = V \Sigma^+ U^T
$$

dove $\Sigma^+$ è ottenuta invertendo i valori singolari non nulli di $\Sigma$ e trasponendo la matrice.

Questa decomposizione costituisce quindi un ponte tra l'algebra lineare teorica e le applicazioni numeriche, offrendo un linguaggio comune per analizzare la struttura intrinseca dei dati e delle trasformazioni.
