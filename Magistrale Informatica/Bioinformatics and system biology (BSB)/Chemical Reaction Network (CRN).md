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
Una **Chemical Reaction Network (CRN)** è una rappresentazione formale di un sistema biochimico come insieme finito di reazioni elementari tra specie molecolari interagenti.

Un pathway è formalmente una [[Chemical Reaction Network (CRN)|Chemical Reaction Network]], cioè un insieme di reazioni del tipo $$\ell_1 S_1 + \dots + \ell_\rho S_\rho \xrightarrow{k} \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$ dove $S_i$ sono reagenti, $P_i$ prodotti, $\ell_i,\ell'_i\in\mathbb{N}$ coefficienti stechiometrici e $k\in\mathbb{R}_{\ge0}$ costante cinetica. Le reazioni possono essere reversibili $$\ell_1 S_1 + \dots + \ell_\rho S_\rho \;\xrightleftharpoons[k_{-1}]{k}\; \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$

Le specie sono immerse in una soluzione ben mescolata (well-stirred); la quantità è espressa come concentrazione $[S]$ (mol/L). Lo stato del sistema è il vettore delle concentrazioni $$x(t)=([S_1](t),\dots,[S_m](t))$$

![[IMG - Tipi di reazioni per CRN.png]]
Tipi elementari di reazione:
- Sintesi: $\varnothing \xrightarrow{k} S$
- Degradazione: $S \xrightarrow{k} \varnothing$
- Trasformazione: $S \xrightarrow{k} P$
- Binding: $S_1+S_2 \xrightarrow{k} P$
- Unbinding: $S \xrightarrow{k} P_1+P_2$
- Catalisi: $E+S \xrightarrow{k} E+P$
Reazioni complesse possono essere decomposte in combinazioni di queste; anche la catalisi può essere scomposta (binding/unbinding/trasformazione) ma è abbastanza comune da essere trattata come “tipo” a sé in molte CRN.
![[IMG - scomposizione della catalisi.png]]

La **legge di azione di massa (mass-action)** è l’assunzione cinetica standard: in una soluzione ben mescolata la frequenza di collisione tra reagenti è proporzionale al prodotto delle loro concentrazioni. Per $$\ell_1 S_1 + \dots + \ell_\rho S_\rho \xrightarrow{k} \dots$$ la velocità è $$v = k\,[S_1]^{\ell_1}\dots [S_\rho]^{\ell_\rho}$$ Per una reazione reversibile: $$v_f=k[S_1]^{\ell_1}\dots[S_\rho]^{\ell_\rho},\quad v_b=k_{-1}[P_1]^{\ell'_1}\dots[P_\gamma]^{\ell'_\gamma}$$

Modello ODE esplicito per una reazione reversibile $$\ell_1 S_1 + \dots + \ell_\rho S_\rho \;\xrightleftharpoons[k_{-1}]{k}\; \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$:
$$\frac{d[S_i]}{dt}=-\ell_i\,k[S_1]^{\ell_1}\dots[S_\rho]^{\ell_\rho}+\ell_i\,k_{-1}[P_1]^{\ell'_1}\dots[P_\gamma]^{\ell'_\gamma}$$
$$\frac{d[P_j]}{dt}=\ell'_j\,k[S_1]^{\ell_1}\dots[S_\rho]^{\ell_\rho}-\ell'_j\,k_{-1}[P_1]^{\ell'_1}\dots[P_\gamma]^{\ell'_\gamma}$$

Nel caso generale con $R$ reazioni la dinamica è descritta tramite [[Ordinary Differential Equation (ODE)|Ordinary Differential Equation (ODE)]] accoppiate $$\frac{d[S_i]}{dt}=\sum_{r=1}^{R}\nu_{ir}v_r(x)$$ dove $v_r(x)$ è la velocità della reazione $r$ e $\nu_{ir}=\ell'_{ir}-\ell_{ir}$ è il coefficiente stechiometrico netto della specie $S_i$ nella reazione $r$; la matrice stechiometrica $\nu\in\mathbb{R}^{m\times R}$ codifica la struttura della rete. In forma vettoriale: $$\frac{dx}{dt}=\nu\, v(x)$$ con $v(x)=(v_1(x),\dots,v_R(x))^T$.

Proprietà rilevanti per l’analisi ODE:
- Conservazione: se esiste $c\in\mathbb{R}^m$ con $c^T\nu=0$, allora $c^Tx(t)$ è costante.
- Steady state: $\nu\,v(x^*)=0$.
- Dipendenza dai parametri: la dinamica dipende dalle costanti cinetiche $k_r$.
- Stiffness: possibili scale temporali molto diverse tra reazioni lente e veloci.

Unità di misura e ordine: la rate ha unità $mol/(L\cdot sec)$; l’unità di $k$ dipende dal numero totale di reagenti nel termine mass-action. Per $S\xrightarrow{k}P$ vale $sec^{-1}$, per $S_1+S_2\xrightarrow{k}P$ vale $L/(mol\cdot sec)$, per $2S_1+S_2\xrightarrow{k}P$ vale $L^2/(mol^2\cdot sec)$.

Una reazione reversibile è in **equilibrio dinamico** quando $v_f=v_b$, cioè $$k[S_1]^{\ell_1}\dots[S_\rho]^{\ell_\rho}=k_{-1}[P_1]^{\ell'_1}\dots[P_\gamma]^{\ell'_\gamma}$$ all’equilibrio le concentrazioni sono costanti ma le reazioni continuano a verificarsi compensandosi.

Oltre al modello deterministico esistono modelli stocastici (es. algoritmo di Gillespie) quando il numero di molecole è basso e cinetiche non-Mass-Action (es. Michaelis–Menten, Hill) quando il meccanismo elementare non è esplicitamente modellato. Le CRN costituiscono il formalismo quantitativo per descrivere la dinamica dei [[Cell pathways]].