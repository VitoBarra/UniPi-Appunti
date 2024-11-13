---
Course: "[[Calcolo Numerico(CN)]]"
topic: nota
tags:
  - CN
---
# Problemi Mal Condizionati
---
Non tutti i problemi sono numericamente calcolabili siccome esistono alcune situazioni in cui una _piccola variazione_ porta ad un errore oltre il 100%, questi casi vengono detti problemi _mal condizionati_ caratterizzati da alto _[[Tipi di Errore nel calcolo numerico|errore inerente]]_

### Esempio

$$
\begin{cases}
1.01x+1.02y = 2.03 \\
0.99x+y = 1.99
\end{cases}
$$

ha soluzione $x=1,y=1$ alterando leggermente il sistema otteniamo

$$
\begin{cases}
1.01x+1.02y = 2.03 \\
x+y = 1.99
\end{cases}
$$

che ha soluzione $\tilde{x} = -0.02 ,\tilde{y} = 2.01$

quindi una variazione sconsiderata giustificata geometricamente dallo strettissimo angolo che crea l intersezione delle dure rette

![[UniPi-Appunti/Triennale Informatica/Calcolo Numerico(CN)/Media/Untitled.png]]
