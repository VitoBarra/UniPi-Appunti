---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Da rappresentazione point base a campo scalare
---
Il problema di passare da una rappresentazione a [[Point Cloud (nuvola di punti)|nuvola di punti]] a una [[Mesh Poligonali|Mesh Poligonali]]  
La [[Normale di una superfice parametrica|normale]] per ogni punto campionato è importante per riuscire a ricostruire la superfice reale
![[IMG - importanza delle normali.png]]
in alcuni casi pero  le normali non sono disponibili, per cui è necessario ricostruirle da una semplice nuvola di punti. 



Il metodo più diffuso si basa sulla **Principal Component Analysis** (PCA), che approssima localmente la superficie come un ellissoide schiacciato.

1. **Centrare i punti locali**  
   Per ogni punto di interesse $\mathbf{p}_i$, si seleziona un intorno di $k$ vicini più prossimi e si calcola:
   $$
   \mathbf{q}_i = \mathbf{p}_i - \mathbf{c}
   $$
   dove $\mathbf{c}$ è il centro di massa dei $k$ punti.

2. **Costruire la matrice di covarianza**  $$
   \mathbf{C}_{\mathrm{ov}} \;=\; \sum_i \mathbf{q}_i\,\mathbf{q}_i^T
   \;=\;
   \begin{bmatrix}
     \sum_i q_{i_x}^2 & \sum_i q_{i_x}q_{i_y} & \sum_i q_{i_x}q_{i_z} \\
     \sum_i q_{i_y}q_{i_x} & \sum_i q_{i_y}^2 & \sum_i q_{i_y}q_{i_z} \\
     \sum_i q_{i_z}q_{i_x} & \sum_i q_{i_z}q_{iy} & \sum_i q_{i_z}^2
   \end{bmatrix}
   $$

3. **Autovalori e autovettori**  
   Si calcolano autovalori $\lambda_1 \le \lambda_2 \le \lambda_3$ e autovettori corrispondenti $\mathbf{v}_1,\mathbf{v}_2,\mathbf{v}_3$. L’ellissoide di covarianza ha un asse molto corto in direzione dell’autovettore associato al più piccolo autovalore, che approssima il piano tangente:  
   $$\text{normale locale}\;\approx\;\mathbf{v}_1$$  ![[IMG - point per principal component analisys.png]]

4. **Scelta del verso della normale e propagazione**  
   La PCA fornisce una retta, non un verso. Si sceglie un punto di partenza con normale ben definita, si assegna arbitrariamente il segno di $\mathbf{v}_1$ e quindi si propaga la coerenza ai vicini, preferendo sempre l’orientazione più simile a quella già fissata. Spesso si ottengono regioni locali coerenti, ma la sincronizzazione globale può richiedere euristiche aggiuntive.  
![[IMG - direzione di normale scelta segno.png]]
