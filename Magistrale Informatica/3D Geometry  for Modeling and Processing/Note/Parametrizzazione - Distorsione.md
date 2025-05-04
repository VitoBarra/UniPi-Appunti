---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Parametrizzazione - Distorsione
---
Nel contesto della [[Parametrizzazione|parametrizzazione]], la **distorsione** è una misura quantitativa di quanto una una funzione $f:S\to \Omega$  deformi localmente le proprietà geometriche, come **angoli** e **aree**. 

la distorsione può essere **espressa** guardando cosa succede ai punti sulla superfice $f(u,v)$ considerando una piccola variazione  $\Delta u, \Delta v$ si vuole quindi calcolare $\hat{f}(u + \Delta u, v + \Delta v)$ questo si può fare usando lo [[Sviluppi di Taylor|sviluppo di Taylor]] del primo ordine:  $$
\begin{array}

\hat{f}(u + \Delta u, v + \Delta v)  & = &  f(u, v) + f_u(u, v)\Delta u + f_v(u, v)\Delta v  \\
 & = & \mathbf{p}+J_f(\mathbf{u})\begin{pmatrix} \Delta u \\ \Delta v \end{pmatrix}
\end{array}
$$ dove $f_u = \cfrac{\partial f}{\partial u}$ e $f_v = \cfrac{\partial f}{\partial v}$ sono [[derivate|derivate parziali]] di $f$ e $J_f$ è la [[Jacobiana di una funzione|jacobbiana]] della [[Funzioni|funzione]] $f$  una [[Matrici|matrice]] $3 \times 2$ con le [[Derivate|derivate parziali]] di $f$ come vettori colonna.
la $J_f$ la si può scomporre con la [[Singular Value Decomposition (SVD)|singular value decomposition]] 	$$ J_f = U\Sigma V^T = U\begin{pmatrix} \sigma_1 & 0 \\ 0 & \sigma_2 \\ 0 & 0 \end{pmatrix}V^T $$dove  $\sigma_1 \geq \sigma_2 > 0$ sono i **Valori singolari**  [[Autovettori e Autovalori|Autovalori]] di $J_fJ_f^T$e **matrici ortonormali** $U \in \mathbb{R}^{3 \times 3}$ e $V \in \mathbb{R}^{2 \times 2}$. 
  - La trasformazione $V^T$ ruota i punti attorno a $u$ allineando $V_1$ e $V_2$ agli assi $u$ e $v$.  
  - $\Sigma$ **dilata** di $\sigma_1$ nella direzione $u$ e di $\sigma_2$ nella direzione $v$.  
  - $U$ mappa i vettori unitari $(1, 0)$ e $(0, 1)$ nei vettori $U_i$ e $U_j$ nel piano tangente $T_p$ in $p$.

si ha quindi che la distorsione può essere interpretata soltanto guardando ai valori $\sigma_1$  e $\sigma_2$ 
![[IMG - distorsione dipendenza da autovettori.png]] 


La distorsione può essere classificata a seconda delle proprietà che la $f$ preserva localmente. Le principali tipologie di distorsione sono:
- **Preservazione degli angoli** (***conforme***) $\cfrac{\sigma_1}{\sigma_2}=1$:  allora $f$ conserva gli angoli locali ma non l'area. ![[IMG - distorsione conforme.png]]![[IMG - esempio distorsione conforme.png]]

- **Preservazione dell’area** (***equiarea***) $\sigma_1\cdot\sigma_2=1$ : allora $f$  conserva le **aree** ma non gli angoli ![[IMG - Distorsione equiareal.png]]![[IMG - esempio distorsione equiareo.png]]

- **isometrica** $\sigma_1=\sigma_2=1$: allora $f$  preserva sia **angoli** che **aree**. In questo caso non si verifica alcuna distorsione geometrica. ![[IMG - Mapping isometrica.png]]
