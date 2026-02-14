---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# CRN - Modello mass-action 
---
Il **Modello mass-action** è il modello cinetico deterministico per [[Chemical Reaction Network (CRN)|CRN]] fondato sulla **legge di azione di massa**, una legge empirica della chimica secondo cui, in una soluzione **ben mescolata**, la velocità di una reazione elementare è proporzionale al prodotto delle concentrazioni dei reagenti, ciascuna elevata al proprio coefficiente stechiometrico.  
  
La **legge di azione di massa** costituisce quindi il principio fisico–chimico su cui si basa l’intero modello: essa specifica la forma funzionale delle velocità di reazione e fornisce la semantica dinamica di una [[Chemical Reaction Network (CRN)|CRN]] in termini di [[Ordinary Differential Equation (ODE)|ODE]]. $$\ell_1 S_1 + \dots + \ell_\rho S_\rho \xrightleftharpoons[k_{-1}]{k} \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$le velocità (rate) sono:$$  
\begin{array}{rcl}  
v_f & = & k \displaystyle\prod_{i=1}^{\rho}[S_i]^{\ell_i} \\  
v_b & = & k_{-1} \displaystyle\prod_{i=1}^{\gamma}[P_i]^{\ell'_i}  
\end{array}  
$$Il **rate** ha unità di misura $mol/(L\cdot sec)$, cioè variazione di concentrazione per unità di tempo. Una reazione reversibile è detta in **equilibrio dinamico** quando $v_f=v_b$, cioè quando $$k\displaystyle\prod_{i=1}^{\rho}[S_i]^{\ell_i}=k_{-1} \displaystyle\prod_{i=1}^{\gamma}[P_i]^{\ell'_i}$$ all’equilibrio le concentrazioni restano costanti ma le reazioni continuano a verificarsi compensandosi.


L’unità di misura della **costante cinetica** $k$ dipende dall’ordine complessivo della reazione, ossia dalla somma dei coefficienti stechiometrici dei reagenti. Sia $n=\sum_i \ell_i$ l’ordine della reazione. Poiché il rate $v$ deve avere unità di misura $mol/(L\cdot sec)$ e ciascuna concentrazione $[S_i]$ ha unità $mol/L$, si ricava Dimensionalmente:$$  \mathrm{unit}(k) = \frac{mol/(L\cdot sec)}{\left({mol}/{L}\right)^n}  
= \frac{L^{\,n-1}}{sec\cdot mol^{\,n-1}}  
$$  esempi:  
- $A \xrightarrow{k} B$ con $v=k[A] \Rightarrow \mathrm{unit}(k)=1/sec$  
- $A+B \xrightarrow{k} C$ con $v=k[A][B] \Rightarrow \mathrm{unit}(k)=L/(sec\cdot mol)$  
- $2A+B \xrightarrow{k} C$ con $v=k[A]^2[B] \Rightarrow \mathrm{unit}(k)=L^2/(sec\cdot mol^2)$
Le costanti cinetiche dipendono dalle unità adottate: un cambiamento di scala delle concentrazioni (es. mol → μmol) o del tempo (sec → h) richiede una trasformazione coerente del valore numerico di $k$.



Le reazioni chimiche possono essere modellate tramite [[Ordinary Differential Equation (ODE)|ODE]]. Per la reazione$$\ell_1 S_1 + \dots + \ell_\rho S_\rho \;\xrightleftharpoons[k_{-1}]{k}\; \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$Le ODE si ottengono applicando la **variazione stechiometrica** moltiplicata per il rate netto $v_f - v_b$.

Per ciascun reagente $S_i$:$$
\frac{d[S_i]}{dt}
=
-\ell_i\, v_f
+
\ell_i\, v_b
=
-\ell_i k \prod_{h=1}^{\rho} [S_h]^{\ell_h}
+
\ell_i k_{-1} \prod_{h=1}^{\gamma} [P_h]^{\ell'_h}
$$Per ciascun prodotto $P_j$:$$
\frac{d[P_j]}{dt}
=
\ell'_j\, v_f
-
\ell'_j\, v_b
=
\ell'_j k \prod_{h=1}^{\rho} [S_h]^{\ell_h}
-
\ell'_j k_{-1} \prod_{h=1}^{\gamma} [P_h]^{\ell'_h}
$$Ottenendo quindi il [[ODE - Sistemi|sistema di ODE accoppiate]] completo:$$
\left\{
\begin{aligned}
\frac{d[S_1]}{dt} &= \ell_1 k_{-1} \prod_{j=1}^{\gamma} [P_j]^{\ell'_j}
- \ell_1 k \prod_{i=1}^{\rho} [S_i]^{\ell_i} \\
\vdots \\
\frac{d[S_\rho]}{dt} &= \ell_\rho k_{-1} \prod_{j=1}^{\gamma} [P_j]^{\ell'_j}
- \ell_\rho k \prod_{i=1}^{\rho} [S_i]^{\ell_i} \\
\frac{d[P_1]}{dt} &= \ell'_1 k \prod_{i=1}^{\rho} [S_i]^{\ell_i}
- \ell'_1 k_{-1} \prod_{j=1}^{\gamma} [P_j]^{\ell'_j} \\
\vdots \\
\frac{d[P_\gamma]}{dt} &= \ell'_\gamma k \prod_{i=1}^{\rho} [S_i]^{\ell_i}
- \ell'_\gamma k_{-1} \prod_{j=1}^{\gamma} [P_j]^{\ell'_j}
\end{aligned}
\right.
$$Le ODE risultanti descrivono l’evoluzione temporale continua delle concentrazioni sotto l’ipotesi di soluzione ben mescolata.

Da questo modello possiamo simulare l evoluzione del sistema impostandolo come un [[ODE - Problema di Cauchy|problema di cauchy]] dando dei valori iniziale alle specie molecolari e simulando l evoluzione del sistema data la complessità spesso tramite [[ODE - Integrazione Numerica| integrazione numerica]]

Oltre al modello deterministico esistono modelli stocastici (es. algoritmo di Gillespie) quando il numero di molecole è basso e cinetiche non-Mass-Action (es. Michaelis–Menten, Hill) quando il meccanismo elementare non è esplicitamente modellato. Le CRN costituiscono il formalismo quantitativo per descrivere la dinamica dei [[Cell pathways]].