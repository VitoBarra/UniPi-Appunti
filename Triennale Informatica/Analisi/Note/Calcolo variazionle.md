---
Course: "[[Analisi|Analisi]]"
tags:
  - Analisi
Area: 
topic: 
SubTopic:
---
# Calcolo variazionle
---
Il [[Calcolo delle variazioni]] studia il problema di determinare una funzione $y(x)$ che rende stazionario (tipicamente minimo o massimo) un funzionale, cioè un oggetto che associa un numero reale a una funzione. Il caso fondamentale è il funzionale integrale

$J[y] = \int_a^b F(x, y(x), y'(x))\,dx$

dove $F$ è una funzione assegnata detta **lagrangiana**.

L’idea centrale consiste nel considerare una famiglia di funzioni vicine alla funzione candidata $y(x)$ introducendo una **variazione**

$y(x) + \varepsilon \eta(x)$

dove $\eta(x)$ è una funzione arbitraria che soddisfa le condizioni al bordo $\eta(a)=\eta(b)=0$ e $\varepsilon$ è un parametro reale piccolo.

Il funzionale diventa quindi dipendente da $\varepsilon$

$J(\varepsilon) = \int_a^b F(x,\, y+\varepsilon\eta,\, y'+\varepsilon\eta')\,dx$

e la funzione $y(x)$ rende stazionario il funzionale quando la derivata rispetto a $\varepsilon$ si annulla in $\varepsilon=0$

$\frac{dJ}{d\varepsilon}\Big|_{\varepsilon=0}=0$

Calcolando questa derivata e integrando per parti il termine contenente $\eta'$ si ottiene la **condizione necessaria di stazionarietà**, che porta all’**equazione di Eulero–Lagrange**

$\frac{\partial F}{\partial y} - \frac{d}{dx}\left(\frac{\partial F}{\partial y'}\right) = 0$

Ogni funzione $y(x)$ che rende stazionario il funzionale deve soddisfare questa equazione differenziale.

Il problema variazionale fondamentale assume quindi la forma: trovare $y(x)$ tale che

$J[y] = \int_a^b F(x,y,y')\,dx$

sia stazionario sotto le condizioni al bordo

$y(a)=y_a, \qquad y(b)=y_b$

e la soluzione si ottiene risolvendo l’equazione di Eulero–Lagrange con tali condizioni.

Il calcolo delle variazioni costituisce la base matematica della **meccanica lagrangiana**, dove l’azione

$S[q] = \int_{t_1}^{t_2} L(q,\dot q,t)\,dt$

deve essere stazionaria; applicando l’equazione di Eulero–Lagrange si ottengono le equazioni del moto del sistema.


![[IMG - Calcolo variazionle.png]]