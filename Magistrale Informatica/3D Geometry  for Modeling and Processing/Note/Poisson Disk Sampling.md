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
il __Poisson Disk Sampling__ (PDS) è un modo per fare [[Sampling|Sampling]] ed è definita come 

__sia__ $X$ un campionamento $X = \{(x_i, r_i) \,|\, i = 1, \dots, n\}$
Se vale che 
1. **Distanza minima**: $\forall (x_i, x_j) \in X, \|x_i - x_j\| > \min(r_i, r_j)$
2. **Campionamento imparziale**: La probabilità che una regione sia coperta è proporzionale alla sua dimensione.
3. **Proprietà di campionamento massimale**: $\Omega \subseteq \bigcup \text{disk}(x_i, r_i)$
__Allora__ è questo è un __Poisson disk sampling__

I vincoli di un PDS non richiedono necessariamente una qualche struttura regolare ma questa puo essere ottenuta ad esempio scegliendo un sampling come centro di una griglia di esagoni. 
![[Pasted image 20241208222753.png]]


#### Dart Throwing
l algoritmo __Dart Throwing__ è usato per  generare __Poisson Disk sampling__ su superfici 2D  e l' intuizione generale  e di generare randomicamente un punto e controllare se i vincoli sono rispettati nel primo caso mantenere il punto nel secondo il piu puo essere cancellato  
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
In generale questo algoritmo non è ottimo e non genera un sampling massimare infatti ha una [[Complessita|complettista]] $O(n^2)$ rispetto al numero di sample e la convergenza è molto lenta questo siccome al aggiungersi di punti la [[Definizione di Probabilita|probabilita]] di generare randomicamente un punto dove i vincoli sono validi diminuisce.



#### Dart Throwing Salloping
il __Dart Throwing Salloping__  è una variante del __Dart Throwing__ che funziona su superfici 2D ed è difficile da estendere in 3D. 
Si vuole massimizzare la probabilità di campionare aree di cui non si è fatto ancora il sampling e per fare ciò l algoritmo si basa sul fatto che se il sampling non è massimale allora deve essere una regione disponibile per aggiungere un nuovo punto nel vicinato della zone dove non è possibile aggiungere nuovi punti.

Per fare ciò si salva il bordo della zone __unavailable__ come [[Struttura dati - Lista linkata|lista linkata]] e archi di cerchio, e per prendere un nuovo sample si prende un punto sul bordo. 
Dopo aver aggiunto il punto le strutture dati vanno aggiornate e reiterare
![[Pasted image 20241208233643.png]]
questo algoritmo ha complessità $O(n\log n)$ rispetto al numero di sample dove il $\log n$ viene dal accesso alla struttura dati
![[Pasted image 20241208234938.png]]
$$
N_p = D(p, 4r) - \bigcup_{p' \in P} 
\begin{cases} 
D(p', 4r), & \text{if } p' < p \\
D(p', 2r), & \text{if } p' \geq p
\end{cases}
$$

![[Pasted image 20241208235554.png]]

### Hierarchical Dart Throwing
l algoritmo __hierarchical Dart Throwing__ è una variante del __Dart Throwing__ si utilizza un [[Quad-Tree e Oct-Tree|quad-Tree]]
![[Pasted image 20241208235909.png]]






per il dominio di una superficie invece si utilizzano delle metriche come la distanza euclidea e la distanza geodetica:
geodesica è la distanza tra punti percorrendo la superficie.


l hierarchical puo essere espanso ale superfici: funziona bene per casi in cui i punti son vicini male se sono divisi da dati triangolo (da capire meglio riguardare lezione)




Diagrammi di voronoi, e duale del diagramma molto buono. 


i diagrammi di voronoi buono hanno il punto vicino al centroide