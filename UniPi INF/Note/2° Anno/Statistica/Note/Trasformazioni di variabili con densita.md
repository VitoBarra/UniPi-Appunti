---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Trasformazioni di variabili con densità
---
_Supponiamo_ che $X:\Omega \rightarrow \mathbb{R}$ sia una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ con densita $f$ e data la [[Funzioni|funzione]] $h:\mathbb{R} \rightarrow \mathbb{R}$ ci domandiamo se la variabile aleatoria $$Y:\Omega \rightarrow \mathbb{R}, \ \ \ \ Y = h \circ X$$
ha densità. 
Non è detto che $Y$ abbia densità con tutte le possibili $h$  e se ha densita non esiste una regola generale per calcolarla.

Se si riesce a calcolare la _funzione di ripartizione_ $F_{Y}$ di $Y$ allora vale $$F_{y}= \mathcal{P}\{ Y \leq y \} =\mathcal{P}\{ h(X) \leq y  \}$$
e se $h$ ha delle buone prorietà risulta che $F_{y} \in C^{1}$ ovvero è continua con derivata [[Continuità di una funzione|continua]] su tutto $\mathbb{R}$ e perciò si puo derivare $F_{y}$ per ottenere la densita di $Y$
#### Regola del cambio di variabile
_sia_ 
- $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] con densita $f_{X}$ tale che $f_X$ ha valori solo nel _intervallo aperto_ $A$ ed è _nulla_ nel intervallo $A^{c}$  
- $h:A\rightarrow B$ una [[Funzioni|funione biunivoca]] con $B$ un altro _intervallo aperto_ e $h,h^{-1}\in C^{1}$ ovvero [[Continuità di una funzione|continua]] con [[Derivate|derivata]] continua
la variabile $Y=h\circ X$ ha densità $$f_{Y}= \begin{cases}
f_{X}(h^{-1})\cdot\left|\frac{dh^{-1}(y)}{dy}\right|   & y \in  B   \\ 
0  & y \not\in  B  
\end{cases}$$
_Dimostrazione_:
	nel caso in cui $f$ sia [[Continuità di una funzione|continua]] a tratti si ha che $F_{X} \in C^{1}$
	_osservando_ che con le uniche $h$ che soddisfano le ipotesi della prosò posizione sono quelle _strettamente crescenti_ e quelle _strettamente decrescenti_ e quindi si puo dimostrare per casi
	
strettamente _crescenti_:
	vale che $$ \begin{array}{}
F_{Y}(y)  & = &  \mathcal{P}\{Y \leq y  \} & = & \mathcal{P}\{X \leq h^{-1}(y)  \} \\
 &  &  & = & F_{X}(h^{-1}(y))
\end{array}
$$e [[Derivate|derivando]] si ottiene $$f_{Y}(y)=f_{X}(h^{-1}(y))\cdot \frac{dh^{-1}(y)}{dy}$$
strettamente _Decrescente_:
	Vale che $$
	\begin{array}{}
	\mathcal{P}\{ h(X) \leq y \}&=& \\
\mathcal{P}\{ X \geq h^{-1}(y) \}&=&1-F_{X}
\end{array}
	$$ per cui _derivando_ si ottiene lo stesso risultato di prima ma con il segno meno quindi $$f_{Y}(y)=-f_{X}(h^{-1}(y))\cdot \frac{dh^{-1}(y)}{dy}$$
e quindi unendo i due casi si può prendere il valore assoluto e si ottiene l enunciato, come _volevasi dimostrare_ 

