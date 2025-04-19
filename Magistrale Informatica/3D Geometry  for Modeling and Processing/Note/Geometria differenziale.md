---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Geometria differenziale
---
La geometria differenziale è un ramo della matematica che studia le proprietà geometriche delle varietà differenziabili, ovvero spazi che localmente assomigliano a $\mathbb{R}^n$ e su cui è possibile fare analisi differenziale. L’idea di base è quella di estendere i concetti del calcolo differenziale, come derivate e integrali, a oggetti più astratti e complessi rispetto ai semplici spazi euclidei. Per esempio, una curva liscia nello spazio tridimensionale può essere descritta da una funzione differenziabile $\gamma: I \to \mathbb{R}^3$, dove $I$ è un intervallo reale. Lo studio della curvatura e della torsione di questa curva rientra nella geometria differenziale.

Una varietà differenziabile $M$ è uno spazio topologico che localmente può essere descritto da coordinate in $\mathbb{R}^n$ tramite mappe dette carte. La struttura differenziabile permette di definire concetti come vettori tangenti, campi vettoriali e forme differenziali. Un esempio importante è il concetto di spazio tangente $T_pM$ in un punto $p \in M$, che è uno spazio vettoriale che approssima localmente la varietà intorno a $p$.

Un ruolo centrale nella geometria differenziale è giocato dalle connessioni e dalle metriche. Una metrica riemanniana $g$ su una varietà permette di misurare angoli, lunghezze e volumi. Dato un campo vettoriale $X$ e un altro campo vettoriale $Y$, la connessione di Levi-Civita $\nabla_X Y$ descrive come cambia $Y$ lungo $X$ in modo compatibile con la metrica.

Attraverso la curvatura si cattura l’informazione su come lo spazio si “piega”. Il tensore di curvatura di Riemann, denotato da $R$, misura quanto la derivazione covariante non commuta: se $\nabla$ è la connessione, allora
$$
R(X, Y)Z = \nabla_X \nabla_Y Z - \nabla_Y \nabla_X Z - \nabla_{[X, Y]} Z
$$
per campi vettoriali $X, Y, Z$.

La geometria differenziale ha applicazioni in fisica, in particolare nella relatività generale, dove lo spaziotempo è modellato come una varietà lorentziana. Ma è anche fondamentale in molte aree della matematica pura, come la topologia differenziale e la teoria delle varietà.
