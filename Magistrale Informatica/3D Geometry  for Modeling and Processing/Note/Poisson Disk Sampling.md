---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Poisson Disk Sampling
---
il __Poisson Disk Sampling__ (PDS) è un tipo di  [[Sampling|Sampling]] ed è definita come 
__sia__ 
- $X$ un campionamento $X = \{(x_i, r_i) \mid i = 1, \dots, n\}$ dove $x_i$ è il punto e $r_i$ è un raggio di un cerchio con centro $x_i$ di un certo dominio $\Omega$
- $d(\cdot,\cdot)$ una certa [[Definizione di distanza|distanza]].
Se vale che 
1. **Distanza minima**: $\forall (x_i, x_j) \in X, d(x_i,x_j) > \min(r_i, r_j)$
2. **Campionamento imparziale**: La probabilità che una regione sia coperta è proporzionale solo alla sua dimensione.
3. **Proprietà di campionamento massimale**: $\Omega \subseteq \bigcup \text{disk}(x_i, r_i)$
__Allora__ è questo è un __Poisson disk sampling__

I vincoli della definizione di una **PDS** non richiedono necessariamente una qualche struttura regolare ma alcune strutture regolari sono **PDS** come ad esempio un sampling come centro di una griglia di esagoni, una struttura cosi regolare puo portare a molto aliasing e non è quindi un buon **PDS**
![[Pasted image 20241208222753.png]]


#### Dart Throwing
l algoritmo __Dart Throwing__ è usato per generare __[[Poisson Disk sampling|Poisson Disk sampling]]__ su superfici 2D.
la [[algoritmi|algoritmo]] intuitivo segue come: 
1. generare randomicamente un punto e controllare se i vincoli sono rispettati 
2. se **si** il punto si tiene e se ne cerca uno nuovo 
3. se **no** in punto viene cancellato
piu precisamente:
```pseudo
	\begin{algorithm}
	\caption{Dart Throwing}
	\begin{algorithmic}

	\State $n\_miss \gets 0$
	\While{$n\_miss / (n\_miss + \#X) < \text{threshold}$}
		\State $x\_cand \gets \text{RandomPoint()}$
		\If{not $x\_cand \subseteq \text{covered}(X)$} 
			\State $X \gets X + x\_cand$ 
		\Else 
			\State $n\_miss \gets n\_miss + 1$   
		\EndIf  
    \EndWhile 

	\end{algorithmic}
	\end{algorithm}
```
In generale questo algoritmo non garantisce un **sampling massimare** e  una lenta convergenze infatti ha una [[Complessita|complessità in tempo]] $O(n^2)$ rispetto al numero di sample. questo accade siccome la [[Definizione di Probabilita|probabilità]] di generare randomicamente un punto dove i vincoli sono validi [[Limiti|tende]] a zero al aumentare dei punti corretti. 



#### Dart Throwing Salloping
il __Dart Throwing Salloping__ è una variante del __Dart Throwing__ che funziona solo superfici 2D ed è difficile da estendere in 3D. 
Si vuole massimizzare la probabilità di campionare aree di cui non si è fatto ancora il sampling e per fare ciò l algoritmo si basa sul fatto che se il sampling non è massimale allora deve essere una regione disponibile per aggiungere un nuovo punto nel vicinato della zone dove non è possibile aggiungere nuovi punti.

Per fare ciò si salva il bordo della zone __unavailable__ come [[Lista linkata|lista linkata]] e archi di cerchio, e per prendere un nuovo sample si prende un punto sul bordo. 
Dopo aver aggiunto il punto le strutture dati vanno aggiornate e reiterare
![[Pasted image 20241208233643.png]]
questo algoritmo ha [[Complessita|complessità]] $O(n\log n)$ rispetto al numero di sample dove il $\log n$ viene dal accesso alla struttura dati![[Pasted image 20241208234938.png]]
$$
N_p = D(p, 4r) - \bigcup_{p' \in P} 
\begin{cases} 
D(p', 4r), & \text{if } p' < p \\
D(p', 2r), & \text{if } p' \geq p
\end{cases}
$$
![[Pasted image 20241208235554.png]]


### Hierarchical Dart Throwing
L'algoritmo __Hierarchical Dart Throwing__ è una variante ottimizzata del algoritmo **Dart Throwing** basata sul utilizzo di [[Indici Spaziali - Quad-Tree e Oct-Tree|quad-Tree]] nel caso 2D o sui  [[Indici Spaziali - Quad-Tree e Oct-Tree|oct-Tree]] in 3D.

L'algoritmo divide lo spazio in una griglia regolare, dove ogni cella è la radice di un **[[Indici Spaziali - Quad-Tree e Oct-Tree|quad-tree]]**. La dimensione delle celle è scelta in base al raggio $r$ dei dischi che si vogliono considerare, infatti il lato dei quadrati della cella è $l=\frac{r}{\sqrt{ 2 }}$ in questo modo ogni cella puo essere completamente coperta da un disco il cui centro si trova al suo interno.
![[IMG - Dart Throwing gerarchico.png]]


Si utilizza la nozione di:
- **Celle attive**: Celle che non sono ancora completamente coperte da un disco.
- **Lista attiva (active list)**: Liste di celle attive suddivise per livello nel [[Indici Spaziali - Quad-Tree e Oct-Tree|quad-tree]], indicate con $\mathcal{A}_i$
L'algoritmo lavora in modo iterativo selezionando celle attive, verificandone la copertura, e suddividendo le celle non completamente coperte in sotto-celle. Questo approccio consente di focalizzare il campionamento nelle regioni che necessitano di maggiore dettaglio.
Piu formalmente:
```pseudo
\begin{algorithm}
\caption{Hierarchical Dart Throwing}
\begin{algorithmic}
\State $r \gets raggio minimo$
\State $X \gets \emptyset$ 
\State $\mathcal{A}_0 \gets \text{griglia iniziale}$ 

\While{esiste almeno una lista attiva $\mathcal{A}_i$ non vuota}
    \State $S \gets \text{SelectActiveCellWhitProbabilityProportinalToArea}(\mathcal{A}_i)$
    \State Rimuovi $S$ da $\mathcal{A}_i$

    \If{$S$ non è completamente coperta da $X$}
        \State $P \gets \text{RandomPointInCell}(S)$
        \If{$P$ soddisfa il vincolo di distanza minima}
            \State $X \gets X \cup \{P\}$
        \Else
            \State Suddividi $S$ in quattro sotto-celle $\{S_1, S_2, S_3, S_4\}$
            \ForAll{sotto-cella $S_j$ non coperta da $X$}
                \State Aggiungi $S_j$ a $\mathcal{A}_{i+1}$
            \EndFor
        \EndIf
    \EndIf
\EndWhile

\end{algorithmic}
\end{algorithm}

```
![[IMG - darth throwind disk sapling gerarchico.png]]
Il [[Complessita|costo computazionale]] di questo algoritmo dipende da: 
**il costo de test di copertura**:, si utilizza una **griglia secondaria uniforme** con celle di dimensione $r$ (il raggio minimo). Ogni cella di questa griglia può contenere al massimo 4 punti, garantendo un costo costante per la verifica.
**Il costo della scelta di un punto**:
1. Si mantiene la somma delle aree per ogni lista attiva $a_0, a_1, \dots, a_k$.
2. Si genera un numero casuale uniforme in $[0,1]$.
3. Si identifica la lista attiva $m$ corrispondente al numero casuale $\sum^{m-1}_{i=0}a_i \leq a_{tot}x\leq \sum^m_{i=0}a_i$ // NON mi torna
4. Si sceglie una cella casuale nella lista $m$.
non c è una prova definitiva ma questo algoritmo al caso medio dovrebbe avere complessità $\mathcal{O}(n)$ nel numero di punti



### Sampling su superfici
Quando si vuole fare sampling sul dominio delle [[superfici|superfici]] c è bisogno di considerare due distanze principali: la [[Distanza geodetica|Distanza geodetica]] e la [[distanza euclidea|Distanza euclidea]] 
![[IMG - cofronto sampling con distanza euclidea e geodetica.png]]
a secondo del oggetto si puo avere che la [[Distanza euclidea|distanza euclidae]] dia sampling molto piu radi rispetto a quella [[Distanza geodetica|geodetica]], quale delle due è piu corretta dipende dal applicazione 


#### Hierarchical Dart Throwing per superfici
l **Hierarchical Dart Throwing per superfici** è una variante del **Hierarchical Dart Throwing**  che ha come dominio le [[Superfici|superfici]] invece che uno [[spazio euclideo|spazio euclideo]].  
In questa variante si sostituisce la grigllia uniforme con una i triangoli della [[Mesh Poligonali|mesh]] su cui si vuole fare sampling e ogni nodo del [[Indici Spaziali - Quad-Tree e Oct-Tree|quad-tree]] diventa quindi un triangolo, per valutare invece la distanza si usa la [[Distanza geodetica|distanza geodedica]]
![[IMG - Poisson Disk Sampling Dart Trowing gerarchico su superfici.png]]
l algoritmo segue come  
1. Si seleziona un punto casuale, verificando che rispetti la distanza minima $r$ da tutti gli altri punti già presenti.  
2. Si identifica il triangolo che contiene il punto. Se questo triangolo non è interamente contenuto entro una distanza $r$ dal punto, si procede a suddividerlo ripetendo il processo.  
3. I triangoli che soddisfano la condizione di copertura (tutti i loro vertici rispettano la distanza $r$) vengono rimossi dalla lista attiva.  
4. L'algoritmo termina quando la lista attiva è vuota, cioè quando non ci sono più triangoli da suddividere o verificare.  
![[IMG - Dart throwing gerarchico su superfici algoritmo.png]]

Il [[Complessita|costo computazionale]] è composto da:  
il **test di copertura** che è  costante
e sul **campionamento unbiesed** implementato con binning logaritmico. 
Si costruisce un certo numero di bin e ognuno di questo memorizza una lista di triangoli che ricadono all'interno di un determinato intervallo di area. Il procedimento si articola nei seguenti passaggi:
1. Si genera un valore casuale $a$ nell'intervallo $[0, \text{total\_area}]$, dove $\text{total\_area}$ rappresenta l'area complessiva dei triangoli della [[Mesh Poligonali|mesh]].
2. Si esegue una ricerca lineare sui bin finché la somma cumulativa delle aree dei bin $\text{sum\_b}$ supera $a$.
3. A questo punto si seleziona casualmente un triangolo all'interno del bin corrente e lo si accetta con probabilità pari a $\frac{\text{triangle\_area}}{\text{bin\_area}}$. Questo passaggio viene ripetuto fino all'accettazione di un triangolo.
4. Una volta accettato un triangolo, si estrae un punto casuale al suo interno.
questo algoritmo ha costo logaritmico.
![[IMG - dart trowing gerarchico su superfici scelta numero.png]]


Questo  in 3D
![[IMG - Dart trowing gerarchico per superfici in 3D.png]]

#### Sample Generation con sample Removing
un modo per fare  sampling  è mettere piu campione del necessario e poi man mano sceglierne alcuni e rimuovere quelli vicini che non rispetto le condizioni di distanza minima, usando una [[Indici spaziali - Griglia uniforme e spatial Hashing|griglia uniforme]] questa operazione ha costo costante.

Un altro modo è quello di scegliere il punto che rimuove meno punti possibili. Questo non garantisce l ottimalita ma è veloce è facile da implementare.


Una variante di questo permette di fare sampling non uniforme, variando il raggio $r$ con un campo:
![[IMG - Sample removal Iportance sampling.png]]
La funzione di varianziane del raggio deve rispettare certe proprieta matematica, non devve avere derivata prima troppo alta



un altro uso è fare sampling uniforme delle acquisizioni fatte con tecnologie [[Acquisizione modelli 3D dal mondo fisico|time of fligt]]![[IMG - Sample removal esempio per sotto campionare nuvole di punti.png.png]]
alcune varianti tendono a scegliere prima punti sugli edge vivi e solo dopo vengono scelto gli altri. ![[IMG - Sample removal edge preserving sampling.png]]
Lo stesso approccio si puo usare anche per mesh con boundries




