---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Chemical Reaction Network (CRN)
---
Una **Chemical Reaction Network (CRN)** è una rappresentazione formale di un sistema [[Chimica|biochimico]] come insieme finito di [[Reazioni chimiche|reazioni chimiche]] elementari tra specie molecolari interagenti. Le **CRN** assumono che le specie molecolari si muovano in una **soluzione ben mescolata** (*well-stirred*), cioè in un mezzo fluido omogeneo in cui le molecole non sono fisicamente separate e possono incontrarsi liberamente.
![[IMG - well-stired fluid.png]]
In tale ipotesi:
- le molecole si muovono in modo casuale (moto browniano);
- ogni coppia o gruppo di molecole ha la stessa probabilità di incontrarsi;
- le concentrazioni sono spazialmente uniformi;
- la probabilità di reazione dipende esclusivamente dalle **concentrazioni** delle specie coinvolte.
L’ipotesi di soluzione ben mescolata costituisce una **approssimazione macroscopica**: trascura effetti spaziali, compartimentazione cellulare, fenomeni di diffusione limitante e micro-eterogeneità, ma rende possibile una modellazione matematica compatta tramite sistemi di [[Ordinary Differential Equation (ODE)|equazioni differenziali ordinarie]] oppure mediante modelli stocastici a popolazione discreta.


Formalmente, una reazione elementare è descritta come $$\ell_1 S_1 + \dots + \ell_\rho S_\rho \xrightleftharpoons[k_{-1}]{k} \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$dove:
- $S_i$ sono i **reagenti**,
- $P_i$ sono i **prodotti**,
- $\ell_i,\ell'_i\in\mathbb{N}$ sono i **coefficienti stechiometrici**, che esprimono il numero di molecole di ciascun tipo consumate o prodotte,
- $k,k_{-1}\in\mathbb{R}_{\ge0}$ sono le **costanti cinetiche**: $k$ è associata alla direzione diretta della reazione, mentre $k_{-1}$ alla direzione inversa.
Le reazioni sono in generale considerate **reversibili**, poiché a livello molecolare entrambi i versi sono possibili. Tuttavia, in molti casi biologici la costante cinetica inversa è trascurabile ($k_{-1}\approx 0$), e la reazione viene modellata come irreversibile.
Le reazioni  fondamentali descrivibili in questo formalismo sono:
- **Sintesi**: $\varnothing \xrightarrow{k} S$
- **Degradazione**: $S \xrightarrow{k} \varnothing$
- **Trasformazione**: $S \xrightarrow{k} P$
- **Binding**: $S_1+S_2 \xrightarrow{k} P$
- **Unbinding**: $S \xrightarrow{k} P_1+P_2$
- **Catalisi**: $E+S \xrightarrow{k} E+P$

![[IMG - Tipi di reazioni per CRN.png]]
Le reazioni complesse possono essere decomposte in combinazioni di queste forme elementari. In particolare, la **catalisi** può essere scomposta come sequenza di:
- binding: $E+S \to ES$
- trasformazione: $ES \to EP$
- unbinding: $EP \to E+P$
![[IMG - scomposizione della catalisi.png]]
Nonostante ciò, la catalisi è sufficientemente frequente nei sistemi biologici da essere spesso trattata come tipo primitivo nelle CRN, in quanto rappresenta il meccanismo fondamentale dell’azione enzimatica.


La quantità di una specie molecolare $S$ è espressa come concentrazione $[S]$ ($mol/L$). Lo **stato del sistema** è il [[Vettori|vettore]] delle **concentrazioni** $$x(t)=([S_1](t),\dots,[S_m](t))$$ e l’**evoluzione temporale** è determinata dalle **velocità di reazione**, funzione di $x(t)$.

La **legge di azione di massa (mass-action)** è l’assunzione cinetica standard: in una soluzione **ben mescolata** la frequenza di collisione tra reagenti è proporzionale al prodotto delle loro concentrazioni, infatti si ha che per una generica reazione $$\ell_1 S_1 + \dots + \ell_\rho S_\rho \xrightleftharpoons[k_{-1}]{k} \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$le velocità (rate) sono:$$  
\begin{array}{rcl}  
v_f & = & k \displaystyle\prod_{i=1}^{\rho}[S_i]^{\ell_i} \\  
v_b & = & k_{-1} \displaystyle\prod_{i=1}^{\gamma}[P_i]^{\ell'_i}  
\end{array}  
$$Il **rate** ha unità di misura $mol/(L\cdot sec)$, cioè variazione di concentrazione per unità di tempo. Una reazione reversibile è detta in **equilibrio dinamico** quando $v_f=v_b$, cioè quando $$k\displaystyle\prod_{i=1}^{\rho}[S_i]^{\ell_i}=k_{-1} \displaystyle\prod_{i=1}^{\gamma}[P_i]^{\ell'_i}$$ all’equilibrio le concentrazioni sono costanti ma le reazioni continuano a verificarsi compensandosi.


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