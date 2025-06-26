---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---
# Parametrizzazione - Mass-spring
---
Il modello **Mass–spring** è un algoritmo per costruire una [[Parametrizzazione|parametrizzazione]] di una [[Mesh Poligonali|mesh]] $\mathcal{M}$, in cui i [[Computer grafica - Primitive Geometriche|vertici]] sono masse e gli edge molle con lunghezza a riposo. 
L’obiettivo è trovare una configurazione di minimo dell’energia elastica, che si traduce in una parametrizzazione bidimensionale.

In 2D si vuole calcolare la parametrizzazione $f^{-1}$:
- $p_i,p_j,p_k$ punti sulla [[Mesh Poligonali|mesh]] $\mathcal{M}$
- $f^{-1}(p_i)=u_i,f^{-1}(p_k)=u_k$ punti di cui conosco la parametrizzazione
voglio calcolare la parametrizzazione del punto mancante $p_j$ ovvero $f^{-1}(p_j)=u_j$. Questa si ottiene come equilibrio delle molle (gli edge), garantendo la preservazione dei rapporti di lunghezza.
![[GIF - mass-spring 2D.gif]]

Nel caso 3D si sceglie un vertice $i$ è si fissano i vertici del vicinato $\mathcal{N}_i$. Si sceglie la nuova posizione del vertice interno minimizzando l’energia tra quel vertice e i vertici sul bordo
L'energia potenziale della molla in **spazio parametri** tra due punti $p_i$ e $p_j$ è data da:
$$ \frac{1}{2} D_{ij} \| \mathbf{u}_i - \mathbf{u}_j \|^2 $$
dove:
- $D_{ij} > 0$ è la costante elastica (rigidezza) della molla
- $\| u_i - u_j \|$ è la lunghezza calcolata in [[Norme Matriciali e Norme Vettoriali|norma 2]] della molla nello spazio parametrico
![[IMG - mass-spring in 3D.png]]
Questo vale per tutti i vertici $i$ e per tutti i vicinati $\mathcal{N}_i$, sia quindi $\varepsilon=\{(i,j) \mid i \in \mathcal{M},j\in \mathcal{N}_i  \}$  l'energia totale da **[[Problemi di ottimizzazione|minimizzare]]** è espressa come:$$
E = \sum_{(i,j)\in \varepsilon }\frac{1}{2}D_{ij}(\|\mathbf{u}_i-\mathbf{u}_j\|)^2
$$per raggiungere la condizione di minimo si calcolano le [[derivate|derivate parziali]] di $E$ per ogni $u_i$ $$ \frac{\partial E}{\partial u_i} = \sum_{j \in N_i} D_{ij} (u_i - u_j) $$che ponendola a $0$ si ottiene $$\begin{array}{}
\sum_{j \in N_i} D_{ij} (u_i - u_j)  & = & 0 \\
\sum_{j \in N_i} D_{ij} u_i   & = & \sum_{j \in N_i} D_{ij}u_j \\
u_i & = &\displaystyle \cfrac{\sum_{j \in N_i} D_{ij}u_j}{\sum_{j \in N_i} D_{ij}}
\end{array}$$Possiamo riscrivere il peso associato ad ogni $u_j$ come $$\lambda_{ij}=\displaystyle \cfrac{D_{ij}}{\sum_{j \in N_i} D_{ij}}$$ è siccome $D_ij>0$ vale che $$0<\lambda_{ij}<1 \quad \quad \sum_{j \in N_i}\lambda_{ij}=1$$ è quindi si riscrive come $$\mathbf{u}_i =\sum_{j\in\mathcal{N}_i}\lambda_{ij}\mathbf{u}_j$$ e per le proprietà di $\lambda_{ij}$ si vede che $u_i$ è definito come [[Convessita|combinazione convessa]] dei suoi vertici vicini $\mathcal{N}_i$:

risolvere il problema diventa quindi risolvere [[Sistemi lineari e lineari omogenei|sistema lineare]] dove ogni linea esprime un $u_i$ e siccome ogni vertice è connesso ad un numero limitato di altri vertici (in media $7$) il [[Sistemi lineari e lineari omogenei|sistema lineare]] ottenuto è **sparso** 
![[IMG - coordinate in spazio parametri.png]]
si possono generare i pesi di interpolazione convessa $\lambda_{ij}$ per poter considerare altre feature geometriche, usando  un generico peso $w_{ij}$ si definisce:$$
\lambda_{ij}=\frac{w_{ij}}{\sum_{k\in\mathcal{N}_i}w_{ik}}
$$e questi possono essere scelti in vario modo ad esempio
- **Caso stifness**: $w_{ij}=D_{ij}$ è il caso classico.
- **Caso uniforme**: $w_{ij}=1$ uguale per tutti gli edge
- **Caso proporzionale alle distanze**: $w_{ij}=l_{ij}$ dove $l_{ij}$  è la lunghezza del edge. Questa preserva forma e grandezza dei triangoli originale anche nello spazio parametri![[IMG  - MassSpring effetti dei tipi di pesi.png]]ma **proporzionali alla lunghezza**  è il fatto che introducono [[Parametrizzazione - Distorsione|distorsione]] in caso di superfici già planari: ![[IMG - mass-spring caso planare in cui l algoritmo fallisce.png]]

altri pesi pesi che prendono in considerazione gli angoli dei triangoli formati dagli edge sono:  
- **Pesi cotangenti**: $w_{ij}=\cot\alpha_{ij}+\cot\beta_{ij}$ 
- **Variante con fattore geometrico**: $w_{ij}=\cfrac{\cot\alpha_{ij}+\cot\beta_{ij}}{r_{ij}^2}$
- **Discrete harmonic coordinates**:  $w_{ij}=\cot\gamma_{ij}+\cot\gamma_{ji}$ 
- **Mean value coordinates**: $w_{ij}=\cfrac{\tan\frac{\alpha_{ij}}2+\tan\frac{\beta_{ji}}2}{r_{ij}}$![[IMG - pesi per mass-spring con pesi calcolati con cotangenti.png]]

Per risolvere il [[Sistemi lineari e lineari omogenei|sistema lineare]] si fissano i vertici di bordo è si risolve per tutti gli altri vertici ottenendo la **harmonic mapping**:
![[IMG - Parametrizazzione lama con vincoli sul boundry.png]]

### Mass - spring minimi quadrati
Nonostante il modello **Mass–spring** rappresenti un approccio efficace alla [[Parametrizzazione|parametrizzazione]] delle [[Mesh Poligonali|mesh]], esso non è l’unico metodo disponibile. Un'alternativa importante è data dalla risoluzione del problema ai **minimi quadrati**, imponendo condizioni al contorno in modo completo oppure parziale. In un primo approccio, si possono assegnare **valori noti della funzione** $f^{-1}$ su **tutti i vertici di bordo**, vincolando così completamente il contorno del dominio parametrico. In questo caso, si risolve un sistema lineare derivante dalla minimizzazione globale di una funzione di energia, con l’obiettivo di ottenere una distribuzione regolare e coerente delle coordinate nel dominio parametrico.

Un secondo approccio, più flessibile, consiste invece nel fissare **soltanto una parte dei vertici di bordo**, evitando di vincolare completamente il dominio parametrico. In questo contesto, il problema dei minimi quadrati viene formulato imponendo che la soluzione sia **conforme**, ovvero che la mappa preservi gli angoli. Questo si traduce nella richiesta che il **Laplaciano della distorsione** sui triangoli sia tale da rendere i **fattori di scala singolari** $\sigma_1$ e $\sigma_2$ il più possibile uguali. Tale condizione implica che i cerchi nello spazio 3D vengano trasformati in cerchi anche nello spazio parametrico, garantendo quindi una mappatura localmente simile a una trasformazione conforme.

Formalmente, si cerca una funzione che minimizzi una **funzionale di energia quadratica** soggetta a **vincoli parziali**, utilizzando i metodi classici della discretizzazione differenziale, come il calcolo dei **Laplaciani discreti**. A differenza del metodo mass–spring, in cui si richiede che ogni punto sia una [[Convessità|combinazione convessa]] dei propri vicini, qui si mira a minimizzare la **distorsione angolare** su tutta la mesh, cercando una mappa $f^{-1}$ che distribuisca il più uniformemente possibile le coordinate parametriche. Questo approccio è particolarmente utile quando non è possibile o desiderabile fissare completamente il bordo del dominio.

![[IMG - Parametrizzazione Mass-spring Soluzione con i minimi quadrati.png]]

Come mostrato, l’uso del bilaplaciano come estensione del Laplaciano consente di ottenere una soluzione più regolare, migliorando la smoothness del risultato finale e riducendo eventuali artefatti locali. In questo quadro, l'approccio ai minimi quadrati rappresenta un'alternativa raffinata e potente per ottenere una parametrizzazione coerente, fluida e, in alcuni casi, più fedele rispetto alla tecnica mass–spring.





