---
Course: Calcolo Numerico
topic: nota
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Criterio di Stop per metodi iterativi
---
ci sono vari criteri di stop per gli algoritmi che implementano questi [[Metodi Iterativi per soluzioni di sistemi lineari|metodi]].
dato un certa tolleranza di errore $tol$ il criterio _ideale_ sarebbe 
$$\|x^{(k+1)}-x\|\leq tol$$
ma questo non è utilizzabile siccome non conosciamo il valore di $x$ che è la soluzione _vera_
altri criteri sono
- $\|x^{(k+1)}-x^{(k)}\|\leq tol$
- $\cfrac{\|x^{(k+1)}-x^{(k)}\|}{\|x^{(k)}\|}\leq tol$
- $\|Ax^{(k+1)}-b\| \leq tol$
- $\cfrac{\|Ax^{(k+1)}-b\|}{\|x^{(k)}\|}\leq tol$
i vari criteri _NON_ sono equivalenti e restituiranno valori di $k$ diversi. 
#### Teorema
in più in generale se ci si ferma per questi criteri _NON_ è garantito che $\|x^{(k+1)}-x\| \leq tol$

##### Dimostrazione
si vuole dimostrare che $\|x^{(k+1)}-x\| \leq tol$ non sia vero sotto la condizione del utilizzo dei criteri di stop sopra elencati
si sa 
- _l errore_ : $e^{(k+1)}=x^{(k+1)}-x = Pe^{(k)}$

e allora possiamo scrivere
$$
\begin{array}{}
x^{(k+1)}-x^{(k)} &= \\
x^{(k+1)}-x-(x^{(k)}-x) & =  \\
e^{(k+1)}-e^{(k)}& =  \\
Pe^{(k)}-e^{(k)} & = &(P-I)e^{(k)}

\end{array}$$
mettendoci nel ipotesi di convergenza sappiamo
- $p(P)<1 \implies (P-I)$ _[[Matrice inversa|invertibile]]_ 
>[!question]-
>(invertibile siccome se sotraggo 1 alla diagonale e p(P)<1 mi è garantito che la diagonale non si annulli????? (credo valga solo per tiangolari))

e allora possiamo scrivere
$$\begin{array}{}
 e^{(k)}&=&(P-I)^{-1}\cdot (x^{(k+1)}-x^{(k)}) &   \\
\|e^{(k)}\|&=&\|(P-I)^{-1}\cdot (x^{(k+1)}-x^{(k)})\| & \leq \\
&&\|(P-I)^{-1}\|\cdot \|(x^{(k+1)}-x^{(k)})\| & \leq \\
&& \|(P-I)^{-1}\|\cdot tol
\end{array}$$
$\|(P-I)^{-1}\|$ _può_ diventare diventa  _molto grande_ quando il raggio spetrale tende ad 1 ( $p(P) \to 1$). si dice che la matrice $P-I$ sia quasi _singolare_ si avvicina cioè ad non essere invertibile.