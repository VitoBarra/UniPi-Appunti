---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# Matrice Hessiana
---
La **matrice Hessiana** è uno strumento fondamentale nello studio delle **funzioni multivariate**, in particolare per l'analisi locale del comportamento di una funzione reale $f : \mathbb{R}^n \to \mathbb{R}$. Essa rappresenta la generalizzazione della **derivata seconda** nel caso di più variabili, ed è strettamente connessa con il concetto di **gradiente** [[Funzioni Multivariata - Gradiente]] e di **differenziabilità** [[Funzioni differenziabili]].

Data una funzione $f(x_1, x_2, \dots, x_n)$ sufficientemente regolare (cioè due volte continuamente derivabile), la matrice Hessiana è definita come la matrice quadrata delle derivate seconde parziali:

$$
H_f(x) = 
\begin{bmatrix}
\frac{\partial^2 f}{\partial x_1^2} & \frac{\partial^2 f}{\partial x_1 \partial x_2} & \dots & \frac{\partial^2 f}{\partial x_1 \partial x_n} \\
\frac{\partial^2 f}{\partial x_2 \partial x_1} & \frac{\partial^2 f}{\partial x_2^2} & \dots & \frac{\partial^2 f}{\partial x_2 \partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial^2 f}{\partial x_n \partial x_1} & \frac{\partial^2 f}{\partial x_n \partial x_2} & \dots & \frac{\partial^2 f}{\partial x_n^2}
\end{bmatrix}
$$

Se le derivate miste sono continue, il **teorema di Schwarz** (o delle derivate incrociate) assicura che la matrice Hessiana è simmetrica, cioè $\frac{\partial^2 f}{\partial x_i \partial x_j} = \frac{\partial^2 f}{\partial x_j \partial x_i}$. Questo teorema è una conseguenza della **differenziazione implicita** [[Differenziazione Implicita]] in contesti più generali.

La matrice Hessiana è cruciale per determinare la **natura dei punti critici** di una funzione: punti dove il **gradiente** si annulla. In particolare, se $x_0$ è tale che $\nabla f(x_0) = 0$, si può analizzare il segno della matrice Hessiana in $x_0$ per stabilire la natura del punto critico:

- Se $H_f(x_0)$ è **definita positiva**, allora $x_0$ è un **minimo locale**.
- Se è **definita negativa**, allora $x_0$ è un **massimo locale**.
- Se non è definita né positiva né negativa (cioè **indefinita**), allora $x_0$ è un **punto sella**.

Queste condizioni si collegano direttamente al concetto di **funzioni convesse e concave** [[Funzioni Convesse-Concave]]. In particolare, una funzione è **convessa** se la sua matrice Hessiana è definita positiva semi-definita in ogni punto del dominio.

Nel contesto dell'**ottimizzazione multivariata**, l'uso della Hessiana è indispensabile per applicare condizioni di **secondo ordine**, estendendo il **Teorema di Lagrange** [[Teorema di Lagrange]] alle funzioni di più variabili.

In molte applicazioni pratiche e teoriche, come nell'approssimazione locale di funzioni attraverso **espansioni di Taylor** [[Espanzioni di funzioni in polinomi]], la matrice Hessiana compare naturalmente:

$$
f(x) \approx f(x_0) + \nabla f(x_0)^T (x - x_0) + \frac{1}{2}(x - x_0)^T H_f(x_0)(x - x_0)
$$

Questa espressione è alla base di metodi numerici per l’ottimizzazione, come il metodo di Newton.

Infine, la matrice Hessiana è strettamente legata anche alla **Jacobiana** [[Jacobiana di una funzione]], di cui rappresenta un caso particolare: infatti, essa può essere vista come la Jacobiana del gradiente. Tale connessione evidenzia la struttura gerarchica delle derivate parziali in contesti multivariati [[Funzioni Multivariata - Gradiente]].
