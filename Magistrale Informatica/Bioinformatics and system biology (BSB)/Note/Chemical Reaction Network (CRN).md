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