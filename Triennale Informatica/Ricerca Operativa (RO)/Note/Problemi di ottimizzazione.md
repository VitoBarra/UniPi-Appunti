---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags:
  - RO
---


# Problemi di ottimizzazione
---
Un __problema di ottimizzazione__ consiste nel trovare il **massimo** o il **minimo** di una data __funzione obiettivo__ che è soggetta a vincoli. 
I problemi di ottimizzazione sono due due tipi
- __Lineari__: __funzione obiettivo__ e __vincoli__ sono [[Applicazioni Lineari|funzione lineare]] 
- __Non lineari__: __funzione obiettivo__ o __vincoli__ sono [[Funzioni|funzione NON lineari]]. 


### Problemi di ottimizzazione lineare
i __Problemi di ottimizzazione lineare__ possono essere espressi con __uguaglianze o  disuguaglianze__ ed detta __forma generale__ (sinistra) oppure con solo vincoli di diseguaglianza chiamata __forma canonica__ (destra)$$
\begin{array}{}
\begin{cases}
\max (o \ \min) \ c^Tx \\
A_1x \leq b_1 \\
A_2x \geq b_1 \\
A_3x = b_3 \\
(x \in \mathbb{R}^n)
\end{cases}  &  
\begin{cases}
\max \ c^Tx \\
Ax \leq b \\
(x \in \mathbb{R}^n)
\end{cases}
\end{array}
$$ogni problema in __forma generale__ puo essere riscritta in __forma canonica__. 
 dimostrazione:
- $\min c^Tx= -\max (-c^Tx)$
- $a^Tx \geq b \iff-a^Tx \leq -b$
- $a^T =b \iff\begin{cases}a^Tx \leq b \\-a^Tx\leq -b\end{cases}$


In generale i __problemi di ottimizzazione lineare__ si risolvono spesso con il [[Simplex (Simplesso)|metodo del simplesso]] o con [[Programmazione lineare|algoritmi di programmazione lineare]].



## Problemi di Ottimizzazione Non Lineare
Quando almeno uno tra la funzione obiettivo o i vincoli non è lineare, si ha un **problema di ottimizzazione non lineare**.  
In generale, tali problemi possono essere più complessi da risolvere e richiedere tecniche avanzate come:

- **Programmazione quadratica** (se la funzione obiettivo è quadratica e i vincoli sono lineari)
- **Metodi di ottimizzazione vincolata** (ad esempio, metodo dei moltiplicatori di Lagrange)
- **Algoritmi evolutivi o euristici** (ad esempio, algoritmi genetici, simulated annealing)
- **Ottimizzazione convessa** (se la funzione obiettivo e i vincoli soddisfano condizioni di convessità)


