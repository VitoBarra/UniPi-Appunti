---
Course: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Computer grafica - Primitive algebriche
---
gli elementi del _dominio_ della [[Computer Grafica (CG)|computer grafica]] sono
- __scalari__: sono _monodimensionali_ e rappresentano la _magnitudo_ di qualcosa (temperatura, velocita)
- __punti__: rasentano _posizioni_ nello spazio 
- __vettori__: rappresentano una _direzione_,
	- I _vettori_ si usano anche per descrivere gli spostamenti  che hanno associato una _direzione_ e una _magnitudo_, che rappresentano rispettivamente la linea su cui avviene lo spostamento e il “_di quanto_” avviene lo spostamento.

_punti_ e _vettori_ sono multi-dimensionali ovvero hanno piu componenti, ma il numero di questi dipende dalla dimensione in cui stiamo lavorando.

##### Operazioni
Sugli _elementi geometrici_ si  possono eseguire le seguenti operazioni
_somma punto-vettore_: restituisce una nuovo _punto_ che rappresenta la nuova posizione dopo lo spostamento partendo dal punto iniziale. e quindi si ha $$\boldsymbol{p}=\boldsymbol{p_{1}}+\boldsymbol{\mathit{v}} $$
_somma vettore-vettore_: restituisce un vettore e rappresenta due spostamenti consecutivi. e quindi $$\boldsymbol{\mathit{v}}=\boldsymbol{\mathit{v}_{1}}+\boldsymbol{\mathit{v}_{2}}$$
_sottrazione punto-punto_:  restituisce un vettore e rappresenta lo spostamento necessari da punto $\boldsymbol{p_1}$ per raggiungere il punto $\boldsymbol{p_2}$. la _magnitudo_ di questo vettore e quindi $$\boldsymbol{\mathit{v}}=\boldsymbol{p_{1}}- \boldsymbol{p_{2}}$$
_moltiplicazione scalare-vettore_ restituisce un _vettore_ partendo dal vettore $v_{1}$ ne conserva la _direzione_ ma ne cambia la _magnitudo_ moltiplicandola per un fattore. quindi $$\boldsymbol{\mathit{v}}=a\boldsymbol{\mathit{v}}_{1}$$
$$\begin{array}{}
\boldsymbol{p}_{0} +v_{0}=\boldsymbol{p}_{1} \\
\boldsymbol{p}_{1}-\boldsymbol{p}_{0}=v_{0} \\
v_{0}+v_{1}=v_{1}+v_{0}=v_{2} \\ \boldsymbol{p}_{0}+2v_{2}=\boldsymbol{p}_{4}

\end{array}$$
![[IMG_0728.jpeg]]
