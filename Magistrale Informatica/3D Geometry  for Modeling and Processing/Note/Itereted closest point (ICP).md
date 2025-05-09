---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Itereted closest point (ICP)
---
L'**Iterated Closest Point** (**ICP**) è un [[Algoritmi|algoritmo]] iterativo che raffina un [[Rigid matching di geometrie|allineamento grezzo]] ed è utilizzato per la [[Registrazione di una superfice|registrazione di superfici]] tridimensionali.

La sua struttura si basa sull'assunzione di poter corrispondere insiemi di punti tra due superfici. A partire da una trasformazione iniziale, si identificano le coppie di punti più vicine tra la superficie sorgente $M$ (model) e quella di riferimento $S$ (scene), e si calcola una nuova rototraslazione che porta questi punti a sovrapporsi meglio.
Questa procedura viene ripetuta iterativamente fino a convergenza, ovvero fino a quando errore medio quadratico nella distanza tra le superfici scende sotto una soglia prestabilita. 
l errore è calcolato come:
$$
E= \cfrac{1}{n}\sum_i^n \| R \cdot p_i + t - q_i \|^2
$$
dove $p_i$ sono i punti $M$, $q_i$ i punti della superfice $S$, $R$ è la matrice di rotazione e $t$ il vettore di traslazione.
![[IMG - Itereted closest point (ICP) alinamento.png]]
l'intero algoritmo puo essere scritto come:
```pseudo
	\begin{algorithm}
	\caption{Iterative Closest Point (ICP)}
	\begin{algorithmic}
	\Require Scene, Model
	\Ensure Rotation matrix $Rot$, Translation vector $Trans$
	\State $E' \gets +\infty$
	\State $(Rot, Trans) \gets \text{Initialize-Alignment}(Scene, Model)$
	\Repeat
	    \State $E \gets E'$
	    \State $Aligned\text{-}Scene \gets \text{Apply-Alignment}(Scene, Rot, Trans)$
	    \State $Pairs \gets \text{Return-Closest-Pairs}(Aligned\text{-}Scene, Model)$
	    \State $(Rot, Trans, E') \gets \text{Update-Alignment}(Scene, Model, Pairs, Rot, Trans)$
	\Until{$|E' - E| < Threshold$}
	\State \textbf{return} $(Rot, Trans)$

	\end{algorithmic}
	\end{algorithm}
```


Una delle fasi più delicate è la **selezione delle coppie** di punti. Se la scelta avviene in maniera casuale, l'allineamento può risultare inaccurato. Per migliorare la qualità del matching, si può utilizzare una distribuzione dei punti che rifletta la distribuzione delle **normali** sulla superficie. In questo modo si garantisce che le direzioni delle normali siano uniformemente rappresentate, aumentando la probabilità di allineare correttamente anche elementi più sottili o dettagliati.
![[IMG - Itereted closest point (ICP) sampling delle normali (pispolino).png]]


per scegliere il punto associato su altra mesh si usa il punto punto più vicino nella mesh target, 
![[IMG - Itereted closest point (ICP) punto piu vicino.png]]
oppure si **proiettare lungo la normale** del punto sorgente. Questo accorgimento consente un allineamento più coerente in presenza di discontinuità o superfici parziali.
![[IMG - Itereted closest point (ICP) cercare i punti atraverso la normale.png]]

Durante il processo di ottimizzazione, è utile **pesare le corrispondenze** in base a criteri come la **compatibilità delle normali** o la **distanza iniziale** tra i punti. Inoltre, è prassi comune **escludere coppie di punti troppo distanti**, che risulterebbero fuorvianti per il calcolo della trasformazione.
![[IMG - Itereted closest point (ICP) esclusione di punti troppo distanti.png]]
Una particolare attenzione va rivolta ai punti situati sugli **estremi delle superfici**. In molti casi, le superfici da allineare non sono complete, e alcune aree non trovano corrispondenza nell'altra mesh. In questi casi, è consigliabile **rifiutare le corrispondenze sui bordi**, adottando un approccio simile a RANSAC per escludere matching inconsistenti.
![[IMG - Itereted closest point (ICP) punti sul bordo da escludere.png]]

Una volta stabilita una buona corrispondenza e raggiunta la convergenza, il risultato dell'allineamento risulta molto più preciso rispetto alla configurazione iniziale. La distanza media tra le superfici si riduce sensibilmente e l'allineamento finale può essere considerato adeguato per applicazioni metriche o di integrazione tra dati 3D.

![[IMG - Itereted closest point (ICP) allinamente finale.png]]
![[IMG - Itereted closest point (ICP) risultato dopo la registrazione.png]]
