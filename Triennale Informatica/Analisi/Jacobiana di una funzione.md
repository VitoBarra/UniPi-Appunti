---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# Jacobiana di una funzione
---
La **Jacobiana di una funzione** vettoriale di variabili reali rappresenta una delle generalizzazioni fondamentali del concetto di derivata per funzioni a più variabili. Essa assume un ruolo centrale nell'analisi locale delle trasformazioni differenziabili tra spazi euclidei, trovando applicazione in numerosi contesti, dalla geometria differenziale all'analisi numerica, fino alla meccanica classica.

Sia data una funzione differenziabile 
$$
\mathbf{f}: \mathbb{R}^n \rightarrow \mathbb{R}^m, \quad \mathbf{f}(\mathbf{x}) = 
\begin{bmatrix}
f_1(x_1, \dots, x_n) \\
\vdots \\
f_m(x_1, \dots, x_n)
\end{bmatrix},
$$
dove $\mathbf{x} = (x_1, \dots, x_n) \in \mathbb{R}^n$. La matrice Jacobiana della funzione $\mathbf{f}$ è definita come la matrice $m \times n$ composta dalle derivate parziali delle sue componenti rispetto alle variabili indipendenti:
$$
J_{\mathbf{f}}(\mathbf{x}) = \begin{bmatrix}
\frac{\partial f_1}{\partial x_1} & \cdots & \frac{\partial f_1}{\partial x_n} \\
\vdots & \ddots & \vdots \\
\frac{\partial f_m}{\partial x_1} & \cdots & \frac{\partial f_m}{\partial x_n}
\end{bmatrix}.
$$

Nel caso particolare in cui $m = n$, la Jacobiana è una matrice quadrata e il suo determinante, detto **determinante jacobiano**, riveste un ruolo cruciale nello studio delle trasformazioni invertibili e nei cambi di variabili negli integrali multipli. Infatti, se $J_{\mathbf{f}}(\mathbf{x})$ è non singolare (cioè ha determinante diverso da zero) in un intorno di un punto $\mathbf{x}_0$, allora, per il teorema della funzione inversa, la funzione $\mathbf{f}$ è localmente invertibile in $\mathbf{x}_0$.

Nella nota [Derivate Parziali e Continuità](#) si è già evidenziato come la continuità delle derivate parziali garantisca la derivabilità della funzione. Questo è un prerequisito per poter costruire la Jacobiana. Inoltre, in [Trasformazioni Differenziabili tra Spazi Euclidei](#), è discusso come la Jacobiana possa essere interpretata geometricamente come l'applicazione lineare che meglio approssima $\mathbf{f}$ in un intorno del punto $\mathbf{x}$.

Nel diagramma seguente, tratto dalla nota [Visualizzazione Geometrica della Jacobiana](#), si osserva l'effetto locale della trasformazione $\mathbf{f}$ su una regione infinitesima dello spazio $\mathbb{R}^n$. La matrice Jacobiana agisce come una mappa lineare che deforma infinitesimi volumi (o aree, nel caso bidimensionale), scalando e ruotando la regione in modo affine. Le direzioni principali e i fattori di scala dipendono dagli autovalori e autovettori della matrice, ove applicabile.

Dal punto di vista operativo, il calcolo della Jacobiana è uno strumento fondamentale in molteplici ambiti computazionali. Ad esempio, nei metodi di ottimizzazione come il metodo di Newton generalizzato per funzioni vettoriali, la Jacobiana sostituisce la derivata semplice, permettendo la linearizzazione del sistema non lineare.

Infine, è importante sottolineare che la Jacobiana, come illustrato anche nella sezione [Esempi di Campo di Vettori e Jacobiane](#), permette di comprendere la dinamica locale di sistemi complessi, offrendo una rappresentazione tangente della funzione in esame. Il suo studio si intreccia con quello della matrice hessiana per funzioni scalari, approfondito nella nota [Hessiana e Ottimizzazione](#), completando così il quadro analitico della derivabilità multivariata.
