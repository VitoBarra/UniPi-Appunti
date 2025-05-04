---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Parametrizzazione - As-rigid-as-possible
---
La **Parametrizzazione - As-rigid-as-possible** è una tecnica sviluppata per ottenere una [[Parametrizzazione|parametrizzazione]] di una [[Mesh Poligonali|mesh]] $\mathcal{M}$ basata sull’alternanza tra fasi di ottimizzazione locale e globale. Questo approccio rientra nella categoria dei metodi local-global, in cui ciascuna iterazione si compone di due fasi principali: una fase locale, in cui si ottiene una soluzione ottima per ciascun triangolo isolatamente, e una fase globale, in cui si integrano le soluzioni locali per ottenere una parametrizzazione coerente sull’intera mesh.

Durante l'**ottimizzazione locale**, ogni triangolo viene parametrizzato in un dominio di riferimento  preservando area e forma cioè  senza introdurre [[Parametrizzazione - Distorsione|distorsione]] interna. 
In questa fase si ottiene una soluzione formalmente corretta per ciascun triangolo singolarmente, ma incoerente a livello globale, poiché i vertici condivisi da più triangoli non coincidono esattamente. 
Per correggere questa incoerenza, segue un passaggio di **ottimizzazione globale** in cui si minimizza l’errore generato dalla fusione delle soluzioni locali, cercando di minimizare la [[Parametrizzazione - Distorsione|distorsione]] introdotta.

Il processo viene reiterato: la soluzione globale aggiornata fornisce nuovi vincoli per un successivo passaggio locale, migliorando progressivamente la qualità complessiva della parametrizzazione. 

![[IMG - parametrizzazione as-rigid-as-possible.png]]
Sebbene questo approccio non garantisca formalmente proprietà topologiche desiderabili come l’[[applicazioni tra insiemi|iniettività]], in pratica produce risultati molto efficaci. In particolare, si osserva una distribuzione più uniforme della distorsione, con una riduzione significativa della distorsione di area a fronte di una leggera concessione sulla distorsione angolare (conformale).
![[IMG - parametrizzazione as-rigid-as-possible risultato.png]]
