# Problemi Mal Condizionati

non tutti i problemi sono numericamente calcolabbili siccome esistono alcune situazioni in cui ina piccola varizione porta ad un errore oltre il 100%, questi casi vengono detti problemi mal condizionati

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

quindi una variazzione sconsiderata giustificata geometricamente dallo strettissimo angolo che crea l intersezione delle dure rette

[[Raccolta UniPi INF/Note/2° Anno/Calcolo Numerico(CN)/Media/Untitled.png]]
