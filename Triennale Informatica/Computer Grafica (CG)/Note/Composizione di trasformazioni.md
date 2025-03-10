---
Course: "[[Computer Grafica (CG)]]"
Area: 
topic: 
SubTopic: 
tags:
  - CG
---

# Composizione di trasformazioni
---

#### Rotazioni
In generale le [[Trasformazioni Lineari Geometriche|rotazioni]] funzionano attorno ad uno _specifico punto_, per effettuare una _rotazione_ di $\alpha$ attorno ad uno specifico _punto_ $\boldsymbol{c}$  bisogna
1. _applicare_ la traslazione $T_{-c}$ mettendo cosi al centro il punto $\boldsymbol{c}$ 
2. _applicare_ la rotazione $R_{\alpha}$
3. _applicare_ la traslazione $T_{c}=T_{-c}^{-1}$ ovvero i [[Matrice inversa|inversa]] per rimettere l _oggetto_ alla posizione originale
ottenendo la formula $$R_{c,\alpha}=T_{c}R_{\alpha}T_{- c}$$
 ![[IMG_0732.jpeg]]
e la matrice si può calcolare come 
$$\begin{array}{}
\boldsymbol{p}’ & = & R_{\alpha}(\boldsymbol{p}-\boldsymbol{c})+\boldsymbol{c} \\
 & = & R_{\alpha}\boldsymbol{p}-R_{\alpha}\boldsymbol{c}+\boldsymbol{c} \\
  & = & \underbrace{ R_{\alpha}\boldsymbol{p} }_{ rotation }+\underbrace{ (I-R_{\alpha})\boldsymbol{c} }_{ traslation}
\end{array}$$
e quindi otteniamo la matrice di _roto-traslazione_ $$R_{\alpha,\boldsymbol{c}}=\begin{bmatrix}
R_{\alpha}  & (I-R_{\alpha})\boldsymbol{c} \\
0 & 1
\end{bmatrix}$$
e per la matrice di _scaling_ vale lo stesso ragionamento sostituendo con la rispettiva matrice e quindi la matrice finale diventa 
$$S_{(s_{x},s_{y}),\boldsymbol{c}}=\begin{bmatrix}
S_{(s_{x},s_{y})}  & (I-S_{(s_{x},s_{y})})\boldsymbol{c} \\
0 & 1
\end{bmatrix}$$

#### Commutatività
le operazioni tra loro [[Proprietà del operazioni - Commutativita|commutative]] sono
- __[[Trasformazioni Lineari Geometriche|Traslazione]]__ con __traslazione__
- __Rotazione__ con __rotazione__
- __Scaling__ con __scaling__
- __scaling uniforme__ e __rotazione__
in generale queste tipo di operazioni NON sono commutative ad esempio le matrici di __rotazione__ e __traslazione__ non sono commutative tra loro
![[IMG_0751.jpeg]]

