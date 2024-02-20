---
Course: "[[Computer Grafica (CG)]]"
Subject: Computer Grafica
Area: 
Topic: 
SubTopic: 
tags:
  - CG
---

# Composizione di trasformazioni
---

#### Rotazioni
In generale le [[Trasformazioni Geometriche affini|rotazioni]] funzionano attorno ad uno _specifico punto_, per effettuare una _rotazione_ di $\alpha$ attorno ad uno specifico _punto_ $\boldsymbol{c}$  bisogna
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
le matrici di _traslazione_ sono tra loro commutative e lo sono anche tra loro le matrici di _rotazione_ e _scaling_, questa cosa pero non vale in generale ad esempio NON sono commutative le matrici di rotazione e traslazione
![[IMG_0751.jpeg]]

