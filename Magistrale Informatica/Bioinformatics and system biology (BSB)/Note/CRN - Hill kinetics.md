---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# CRN - Hill kinetics
---
La **Hill kinetics** descrive una generalizzazione [[CRN - Modello mass-action|non–mass-action]] della [[CRN - Michaelis-menten kinetics|Michaelis–Menten kinetics]] utilizzata per modellare fenomeni di **cooperatività** nel binding o nella regolazione enzimatica all’interno di una [[Chemical Reaction Network (CRN)|CRN]].

La **cooperatività** si verifica quando il legame di una molecola di substrato a un **[[Enzimi|enzima]] multimerico** (ovvero con piu binding site) modifica l’affinità degli altri siti di legame della stessa proteina, alterando la probabilità che ulteriori molecole si leghino. Dal punto di vista meccanicistico, tale effetto deriva spesso da [[Energia Molecolare e conformazioni|cambiamenti conformazionali]] tra stati strutturali distinti che si propagano tra le subunità e modulano l’assetto energetico dei siti rimanenti.

La **Hill kinetics** deriva dalla [[CRN - Michaelis-menten kinetics|Michaelis–Menten kinetics]] ed è la velocità di una trasformazione $S \to P$ è espressa come: $$v=\frac{V_{max}[S]^h}{K_M^h+[S]^h}$$dove:
- $V_{max}$ è la velocità massima;
- $K$ è la concentrazione caratteristica, anche detta costante di mezza saturazione;
- $h>0$ è il **coefficiente di Hill**.
Il coefficiente $h$ modula la forma della risposta:
- $h=1$: si ottiene la [[CRN - Michaelis-menten kinetics|cinetica di Michaelis-Menten]];
- $h>1$: **cooperatività positiva** (risposta più ripida, comportamento “switch-like”);
- $0<h<1$: cooperatività negativa (risposta più graduale).
L’esponente $h$ consente di modellare sistemi in cui il legame di una molecola di substrato aumenta (o diminuisce) l’affinità per le successive, Il valore di $h$ non coincide necessariamente con il numero reale di siti di legame, ma rappresenta un parametro efficace che quantifica l’intensità della cooperatività osservata sperimentalmente.
![[IMG - Hill kinetics.png]]

All’aumentare di $h$ la risposta diventa più “switch-like”, con una transizione più brusca tra regime a bassa attività e regime saturo. In tutti i casi le curve tendono allo stesso asintoto orizzontale $$v=V_{max}$$ ma differiscono nella ripidità della regione intermedia.

Il coefficiente di Hill $h$ viene tipicamente stimato tramite fitting dei dati sperimentali e rappresenta un parametro aggiuntivo che consente di adattare la forma della curva alla risposta osservata.




**Esempio: Emoglobina**
L’emoglobina è una proteina tetramerica che trasporta ossigeno nel sangue. Il legame di una molecola di $O_2$ induce una transizione conformazionale che aumenta l’affinità degli altri siti per l’ossigeno, producendo **cooperatività positiva** con coefficiente di Hill tipicamente $h \approx 2.8$.![[IMG - CRN - Hill kinetics emoglobina.png]]
Dal punto di vista dinamico, la Hill kinetics introduce una non linearità più marcata rispetto al [[CRN - Modello mass-action|Modello mass-action]] e alla [[CRN - Michaelis-menten kinetics|Michaelis–Menten kinetics]], permettendo di descrivere risposte sigmoidi e fenomeni di ultrasensibilità.
