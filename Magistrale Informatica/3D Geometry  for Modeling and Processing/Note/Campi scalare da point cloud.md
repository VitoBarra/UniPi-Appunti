---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Campi scalare da point cloud
---
Il **problema affrontato** consiste nel determinare una **superficie** a partire da un [[Point Cloud (nuvola di punti)|nuvola di punti]] $\{x_0, \dots, x_n\}$. A tal fine, si definisce una funzione scalare $f(x)$ come:$$
f(x) = \varphi(\{x_0, \dots, x_n\})
$$dove $\varphi$ è una funzione che costruisce $f$ utilizzando come input l’intero insieme di punti dati. La [[Superfici implicite|superficie implicita]] $S$ viene quindi definita come il luogo dei punti per cui $f$ assume un certo valore costante $\alpha$, ossia:$$
S = \{ x \mid f(x) = \alpha \}$$L’obiettivo è che $S$ interpoli o approssimi la nuvola di punti originale, rappresentandone in maniera continua la geometria implicita

per fare ciò, le [[Normale di una superfice parametrica|normali]] associate ai punti sono spesso utilizzate per migliorare l’accuratezza della ricostruzione. Tali normali possono essere assunte direttamente (ad esempio, nel caso in cui siano fornite insieme alla nuvola di punti)
![[IMG - importanza delle normali.png]]
in alcuni casi pero le [[Normale di una superfice parametrica|normali]] non sono disponibili, per cui è necessario ricostruirle da una semplice [[Point Cloud (nuvola di punti)|nuvola di punti]]. 

Il metodo più diffuso per stimare le normali si basa sulla **[[Principal Component Analysis (PCA)|Principal Component Analysis]]** (PCA), che approssima localmente la superficie come un ellissoide schiacciato.
1. **Centrare i punti locali**  
   Per ogni punto di interesse $\mathbf{p}_i$, si seleziona un intorno di $k$ vicini più prossimi e si calcola:$$
   \mathbf{q}_i = \mathbf{p}_i - \mathbf{c}
   $$dove $\mathbf{c}$ è il centro di massa dei $k$ punti.
2. **Costruire la matrice di [[Variabili aleatorie - Covarianza e correlazione|covarianza]]**  $$
   \mathbf{C}_{\mathrm{ov}} \;=\; \sum_i \mathbf{q}_i\,\mathbf{q}_i^T
   \;=\;
   \begin{bmatrix}
     \sum_i q_{i_x}^2 & \sum_i q_{i_x}q_{i_y} & \sum_i q_{i_x}q_{i_z} \\
     \sum_i q_{i_y}q_{i_x} & \sum_i q_{i_y}^2 & \sum_i q_{i_y}q_{i_z} \\
     \sum_i q_{i_z}q_{i_x} & \sum_i q_{i_z}q_{iy} & \sum_i q_{i_z}^2
   \end{bmatrix}
   $$
3. **Autovalori e autovettori**  
   Si calcolano [[Autovettori e Autovalori|autovalori]] $\lambda_1 \le \lambda_2 \le \lambda_3$ e [[Autovettori e Autovalori|autovettori]] corrispondenti $\mathbf{v}_1,\mathbf{v}_2,\mathbf{v}_3$. L’ellissoide di covarianza ha un asse molto corto in direzione dell’autovettore associato al più piccolo autovalore, che approssima il piano tangente:  $$\text{normale locale}\;\approx\;\mathbf{v}_1$$  ![[IMG - point per principal component analisys.png]]
Questo metodo fornisce una [[Rette|retta]], non una direzione e ne va quindi scelta una per orientare le [[Normale di una superfice parametrica|normali]]. Si sceglie un punto di partenza con normale ben definita, si assegna arbitrariamente il segno di $\mathbf{v}_1$ e quindi si propaga la coerenza ai vicini, preferendo sempre l’orientazione più simile a quella già fissata. Spesso si ottengono regioni locali coerenti, ma la sincronizzazione globale può richiedere euristiche aggiuntive.  
![[IMG - direzione di normale scelta segno.png]]



### Radial basis expantion

Nel contesto della rappresentazione tridimensionale tramite point cloud, un approccio inizialmente diffuso e ancora utilizzato in contesti specifici è quello delle *metaballs*. Questo metodo consente di passare da una rappresentazione a punti a una rappresentazione a superficie continua, assumendo che i punti forniti non siano unicamente campioni della superficie, bensì un campionamento volumetrico dell’intero oggetto. Ogni punto della nuvola è associato a una funzione scalare radiale a decadimento rapido, tipicamente esponenziale o gaussiano, il cui contributo si somma agli altri per generare un campo scalare continuo. Su questo campo si costruisce poi un’isopuperficie, definita come il luogo dei punti in cui la somma delle funzioni scalari locali raggiunge una soglia prefissata. Formalmente, se $p_i$ sono i punti della nuvola e $\phi_i(x)$ sono le rispettive funzioni scalari centrate in $p_i$, la superficie è definita da:

$$
\left\{ x \in \mathbb{R}^3 \mid \sum_i \phi_i(x) = \tau \right\}
$$

dove $\tau$ è un valore di soglia. In questo modello, se i punti $p_i$ sono sufficientemente vicini, le funzioni scalari generano delle "pallettine" che si fondono (blobbano), producendo una superficie continua. Questo approccio è standard nella simulazione di fluidi nei videogiochi, dove i fluidi sono rappresentati tramite particle system e la superficie del fluido è estratta come isosuperficie del campo generato dalle particelle. Tuttavia, il metodo presenta limitazioni: non scala efficacemente con l'aumento del numero di punti, e la superficie risultante non necessariamente passa per i punti, ma si limita a restare nelle loro vicinanze.

Per superare queste problematiche e ottenere una rappresentazione della superficie che interpoli effettivamente i punti della nuvola, si sono sviluppati metodi più matematicamente fondati, in particolare quelli basati su problemi di fitting. Tali approcci costruiscono una funzione scalare continua come combinazione lineare di funzioni base polinomiali, i cui pesi sono determinati imponendo che la funzione risultante sia a distanza minima da un insieme di campioni. Si tratta di una classe di metodi interpolanti su punti sparsi ben studiata nella letteratura numerica, che si riduce a un problema lineare del tipo:

$$
A \mathbf{w} = \mathbf{b}
$$

dove $A$ è una matrice piena di dimensioni pari al numero di punti, $\mathbf{w}$ il vettore dei pesi da determinare e $\mathbf{b}$ un termine noto. Tuttavia, la non sparsità della matrice $A$ implica una scarsa scalabilità del metodo: quando il numero di vertici cresce oltre le migliaia, la risoluzione del sistema diventa computazionalmente proibitiva.

Un’evoluzione significativa per superare questo limite è l’utilizzo delle *Radial Basis Functions* (RBF) con supporto limitato (*bounded*). In questo contesto, ogni funzione base ha dominio limitato e non globale, il che implica che la matrice dei coefficienti del sistema lineare risultante sia sparsa. Questo permette di decomporre il problema in sottoblocchi, rendendo la complessità del fitting lineare rispetto al numero di campioni e permettendo l’applicazione del metodo a dataset di grandi dimensioni.

Una variante ulteriore e affine a questa strategia è il metodo *Multi-Level Partition of Unity*, che impiega anch'esso funzioni base a dominio limitato. Questi metodi, pur fondandosi sullo stesso principio generale delle RBF bounded, introducono un’organizzazione gerarchica delle basi per migliorare ulteriormente l’efficienza e la località del calcolo.
