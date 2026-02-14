---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# CRN - Funzione logistica per reazioni autocatalitiche
---
La **Funzione logistica** descrive una cinetica [[CRN - Modello mass-action|non–mass-action]] utilizzata per modellare processi autocatalitici o dinamiche con **capacità limitata**, in cui la crescita è inizialmente esponenziale ma viene progressivamente saturata da un vincolo.

La forma generale è:
$$\frac{dP}{dt}=\alpha P\left(1-\frac{P}{K}\right)$$
dove:
- $\alpha>0$ è il tasso di crescita;
- $K>0$ è la **capacità portante** (valore di saturazione).

Per $P\ll K$ si ha crescita quasi esponenziale $\cfrac{dP}{dt}\approx \alpha P$ mentre per $P\to K$ il termine $1-\frac{P}{K}\to 0$ e la dinamica si arresta. Il punto $P=K$ è uno stato stazionario stabile.

All’interno di una [[Chemical Reaction Network (CRN)|CRN]] la funzione logistica può emergere da un meccanismo autocatalitico del tipo:
$$A + B \xrightarrow{k} 2B$$
Con conservazione della quantità totale
$$T=[A]+[B]$$
costante nel tempo, si può eliminare la variabile $[A]$ dal sistema. Dalla reazione autocatalitica
$$A + B \xrightarrow{k} 2B$$partendo dalle [[Ordinary Differential Equation (ODE)|ODE]] in [[CRN - Modello mass-action|mass-action]]:$$
\begin{cases}
\dfrac{d[A]}{dt}=-k[A][B] \\
\dfrac{d[B]}{dt}=k[A][B]
\end{cases}
$$e sostituendo nella seconda equazione:$$\frac{d[B]}{dt}=k(T-[B])[B]$$Sviluppando si ottiene : $$\frac{d[B]}{dt}=kT[B]\left(1-\frac{[B]}{T}\right)$$ che è una dinamica logistica della forma con:
$$\alpha=kT, \qquad K=T$$
Interpretazione:
- la crescita di $B$ è proporzionale alla quantità già presente (autocatalisi);
- la saturazione è determinata dall’esaurimento del reagente $A$;
- il sistema converge a $[B]=T$ e $[A]=0$.
Dal punto di vista dinamico, la funzione logistica introduce una non linearità quadratica che combina crescita e saturazione in un’unica equazione ridotta, eliminando la necessità di simulare esplicitamente tutte le specie quando è presente una legge di conservazione.


### Confronto con mass-action 
Si consideri la reazione autocatalitica  $$A + B \xrightarrow{k} 2B$$  Simulazione numerica con $k=0.01$, $[A]_0=100$, $[B]_0=10$ e quantità totale  
$$T=[A]_0+[B]_0=110$$  
  
**ODE ottenute da cinetica mass-action**                                   **ODE ottenuta da funzione logistica**$$
\begin{cases}
\dfrac{d[A]}{dt} = -k_1 [A][B] \\
\dfrac{d[B]}{dt} = k_1 [A][B]
\end{cases}
\qquad\qquad
\dfrac{d[B]}{dt} = k_1 T [B]\left(1 - \dfrac{[B]}{T}\right)
$$Il modello logistico elimina la variabile $[A]$ sfruttando la legge di conservazione e produce una dinamica equivalente per $[B]$ quando la quantità totale è costante.  
![[IMG - CRN - Funzione logistica per reazioni autocatalitiche.png]]
