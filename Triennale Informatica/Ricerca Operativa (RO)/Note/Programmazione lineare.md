---
Course: "[[Ricerca Operativa (RO)]]"
topic: nota
tags:
  - RO
---

# Programmazione lineare
---
il problemi di **programmazione lineare** sono un tipo di [[Problemi di ottimizzazione|Problemi di ottimizzazione]] dove la **funzione obiettivo** e **vincoli** sono lineari.
per questo motivo si possono esprimere anche in forma matriciale [[Matrici|Matriciale]]

i **vincoli** sono __uguaglianze o  disuguaglianze__ ed è detta __forma generale__ (sinistra) oppure con solo vincoli di diseguaglianza chiamata __forma canonica__ (destra)$$
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
$$ogni problema in __forma generale__ può essere riscritta in __forma canonica__. 
 dimostrazione:
- $\min c^Tx= -\max (-c^Tx)$
- $a^Tx \geq b \iff-a^Tx \leq -b$
- $a^T =b \iff\begin{cases}a^Tx \leq b \\-a^Tx\leq -b\end{cases}$


La **regione ammissibile**, ovvero tutti i punti che soddisfano i vincoli, di un problema di un problema di **programmazione lineare** è un [[Poliedro|Poliedro]].



In generale i __problemi di ottimizzazione lineare__ si risolvono spesso con il [[Simplex (Simplesso)|metodo del simplesso]] o con [[Programmazione lineare|algoritmi di programmazione lineare]].