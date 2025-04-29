---
Course: "[[Calcolo Numerico(CN)]]"
tags:
  - CN
Area: 
topic: 
SubTopic:
---
# Interpolazione Bilineare

L'**interpolazione bilineare** è un metodo che stima il valore di una funzione su una superficie bidimensionale (piano) tra quattro punti noti, utilizzando una [[Rette|combinazione di rette]] che _congiungono_ i valori lungo due dimensioni.  
Questo approccio estende l'[[Interpolazione Lineare|interpolazione lineare]] al caso bidimensionale, fornendo una stima continua e lineare all'interno di un rettangolo.

_siano_ quattro coordinate corrispondenti ai vertici di un rettangolo:
$$(x_0, y_0),\ (x_1, y_0),\ (x_0, y_1),\ (x_1, y_1)$$
e i loro rispettivi valori della funzione:
$$(f_{00},\ f_{10},\ f_{01},\ f_{11})$$
_allora_ la formula per l'_interpolazione bi-lineare_ è data da:$$f(x,y) = (1 - t_x)(1 - t_y)f_{00} + t_x(1 - t_y)f_{10} + (1 - t_x)t_y f_{01} + t_x t_y f_{11}$$

dove:
- $f(x,y)$ è il _valore interpolato_,
- $(x,y)$ è il punto bidimensionale in cui si desidera stimare il valore,
- $t_x = \frac{x-x_0}{x_1-x_0}$ è la posizione normalizzata lungo $x$,
- $t_y = \frac{y-y_0}{y_1-y_0}$ è la posizione normalizzata lungo $y$,
- $f_{00}$, $f_{10}$, $f_{01}$, $f_{11}$ sono i valori della funzione nei vertici del rettangolo.

In pratica, si esegue prima un'[[interpolazione lineare|interpolazione lineare]] lungo $x$ per le due righe, e poi un'interpolazione lungo $y$ sui risultati ottenuti.
