---
Course: "[[Computational Mathematics for Learning and Data Analisys (CMLDA)]]"
tags:
  - CMLDA
Area: 
topic: 
SubTopic:
---
# Metodo di ottimizzazione vincolata con moltiplicatori di Lagrange
---
Il metodo dei **moltiplicatori di Lagrange** permette di trovare massimi o minimi di una funzione quando le variabili devono soddisfare un [[vincolo]] di uguaglianza.

Si vuole ottimizzare
$$
f(x_1,\dots,x_n)
$$
soggetta al vincolo
$$
g(x_1,\dots,x_n)=0
$$

In questo contesto non si possono cercare i punti critici imponendo solo
$$
\nabla f(x)=0
$$
perche il moto delle variabili e limitato alla superficie definita dal vincolo.

## Idea geometrica

Nel punto di ottimo vincolato, il gradiente di $f$ deve essere parallelo al gradiente del vincolo:
$$
\nabla f(x^*)=\lambda \nabla g(x^*)
$$
dove $\lambda$ e un numero reale detto **moltiplicatore di Lagrange**.

L'intuizione e che:
- $\nabla f$ punta nella direzione di massima crescita di $f$
- $\nabla g$ e normale alla superficie $g(x)=0$
- nel punto ottimo non ci si puo muovere lungo il vincolo per aumentare o diminuire ulteriormente $f$

Quindi le due normali devono essere allineate.


Si definisce la **funzione lagrangiana**
$$
\mathcal{L}(x,\lambda)=f(x)-\lambda g(x)
$$

Alcuni testi usano anche
$$
\mathcal{L}(x,\lambda)=f(x)+\lambda g(x)
$$

Le due convenzioni sono equivalenti: cambia solo il segno del moltiplicatore.



Per trovare i candidati ottimi si risolve il sistema
$$
\begin{cases}
\nabla_x \mathcal{L}(x,\lambda)=0 \\
g(x)=0
\end{cases}
$$

Esplicitamente:
$$
\begin{cases}
\frac{\partial \mathcal{L}}{\partial x_1}=0 \\
\vdots \\
\frac{\partial \mathcal{L}}{\partial x_n}=0 \\
g(x_1,\dots,x_n)=0
\end{cases}
$$

Il risultato fornisce i **punti candidati**. Per distinguere massimo, minimo o punto di sella bisogna poi valutare la funzione o usare condizioni di secondo ordine.

## Procedura pratica

1. Scrivere la funzione obiettivo $f(x)$.
2. Scrivere il vincolo nella forma $g(x)=0$.
3. Costruire la lagrangiana $\mathcal{L}(x,\lambda)$.
4. Calcolare le derivate parziali rispetto alle variabili e a $\lambda$.
5. Risolvere il sistema ottenuto.
6. Confrontare i valori di $f$ nei punti trovati.

## Piu vincoli di uguaglianza

Se i vincoli sono
$$
g_1(x)=0,\dots,g_m(x)=0
$$
si introduce un moltiplicatore per ciascun vincolo:
$$
\mathcal{L}(x,\lambda_1,\dots,\lambda_m)=f(x)-\sum_{i=1}^m \lambda_i g_i(x)
$$

Il sistema diventa
$$
\begin{cases}
\nabla_x \mathcal{L}(x,\lambda)=0 \\
g_1(x)=0 \\
\vdots \\
g_m(x)=0
\end{cases}
$$

## Osservazioni

- Il metodo fornisce condizioni necessarie, non sempre sufficienti.
- Se $\nabla g(x^\*)=0$, il metodo puo richiedere attenzione aggiuntiva.
- I punti trovati sono candidati: vanno sempre verificati.


![](https://www.youtube.com/watch?v=4NNoxjsv7-k)

![](https://www.youtube.com/watch?v=Klb-yEDVs5U)
