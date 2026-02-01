---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Force Field - Amber ff94
---
l **force field Amber ff94** è un force field classico usato in [[meccanica molecolare|meccanica molecolare]] per descrivere l’energia interna di una molecola a partire dalle coordinate tridimensionali. L’energia potenziale totale associata a una conformazione molecolare è espressa come somma di contributi legati e non-legati:$$
E_{tot}=E_{bond}+E_{angle}+E_{dihedral}+E_{nonbond}.
$$Il termine di **stretching dei legami** descrive la variazione dell’energia quando una distanza di legame si discosta dal valore di equilibrio. È modellato con un potenziale armonico:$$
E_{bond}=\sum k(L)(L-L_0)^2.
$$Il termine di **bending angolare** rappresenta la deformazione degli angoli di legame rispetto al valore ottimale, anch’esso tramite un’espressione armonica:$$
E_{angle}=\sum k(\theta)(\theta-\theta_0)^2.
$$Questi termini sono detti **armonici** perché simmetrici rispetto all’equilibrio, e **diagonali** perché ogni contributo dipende solo dalla singola coordinata considerata.

Le **torsioni diedrali** descrivono la rotazione intorno ai legami e sono modellate con termini periodici:$$
E_{dihedral}=\sum V_i[1+\cos(n|\phi|+t)].
$$I parametri torsionali sono spesso assegnati principalmente ai due atomi centrali e ottimizzati su energie QM relative di rotameri alternativi.

Le interazioni **non-legame** includono contributi tra coppie di atomi non connessi direttamente, comprendendo van der Waals e interazioni elettrostatiche:$$
E_{nonbond}=\sum_{i<j}\left[\frac{A_{ij}}{R_{ij}^{12}}-\frac{B_{ij}}{R_{ij}^{6}}+\frac{q_i q_j}{\varepsilon R_{ij}}\right].
$$In questa espressione:
- il termine $\cfrac{A_{ij}}{R_{ij}^{12}}$ rappresenta la repulsione a corta distanza,
- il termine $-\cfrac{B_{ij}}{R_{ij}^{6}}$ descrive l’attrazione dispersiva (van der Waals),
- il termine $\cfrac{q_i q_j}{\varepsilon R_{ij}}$ corrisponde all’interazione Coulombiana fra cariche parziali atom-centered.
Amber ff94 non richiede un termine esplicito per i legami a idrogeno, poiché tali interazioni sono descritte implicitamente attraverso un modello di cariche più accurato e parametri **van der Waals** ottimizzati da simulazioni in fase liquida, insieme all’introduzione di nuovi tipi di H che includono gli effetti geminali (sullo stesso atomo) di atomi elettronegativi. 

![[IMG - ForceField Amber ff94 calcolo.png]]



I calcoli mediante force field permettono quindi di determinare l’energia associata a una geometria molecolare e di analizzare la stabilità conformazionale.  
![[IMG - calcolo Force filed.png]]

Un aspetto centrale di Amber è l’uso dei **tipi di atomo**, che classificano gli atomi in base ad ambiente chimico, ibridazione e carica, non solo all’elemento.  

Ossigeni distinti in:
  - **O** carbonilico  
  - **OW** acqua  
  - **OH** ossidrilico  
  - **OS** eteri/esteri  
  - **O2** carbossilati e fosfati  
Carboni principali:
  - **CT** carbonio sp3  
  - **C** carbonile sp2  
  - **CA** aromatico sp2  
Azoti:
  - **N** ammidico sp2  
  - **NA/NB/NC** aromatici con lone pair  
  - **N3** azoto sp3  
Zolfo e fosforo:
  - **S** metionina e cisteina  
  - **SH** tiolico  
  - **P** fosfati  
Idrogeni differenziati:
  - **HC** alifatico senza sostituenti attrattori  
  - **HI/H2/H3** con 1,2,3 sostituenti elettronegativi  
  - **HP** vicino a centri positivi  
![[IMG - esempio tipi di atomo.png]]
**Amber ff94** include inoltre i residui [[Proteine|proteici]] standard (ALA, ARG, GLU, TRP, ecc.), rendendolo adatto alla simulazione di biomolecole in [[dinamica molecolare|dinamica molecolare]]. 
