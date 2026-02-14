---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GRN - Probabilistic Boolean Networks
---
**Probabilistic Boolean Networks** sono una variante delle [[GRN - Boolean Networks|Boolean Networks]] progettata per modellare la **stocasticità** e l’incertezza presenti nella [[Gene Regulatory Networks (GRN)|GRN]]. In questo modello l’evoluzione della rete non è completamente deterministica: ogni gene può avere **più funzioni di aggiornamento**, ciascuna associata a una certa probabilità.

In una rete probabilistica ogni gene $x_i$ possiede un insieme di possibili funzioni di aggiornamento$$F_i=\{f_i^{(1)},f_i^{(2)},\dots,f_i^{(m)}\}$$e a ciascuna funzione è associata una probabilità $$P_i=\{p_i^{(1)},p_i^{(2)},\dots,p_i^{(m)}\}$$con$\sum_{k=1}^{m} p_i^{(k)} = 1$

Durante l’evoluzione del sistema, per ogni gene viene selezionata **stocasticamente** una delle funzioni di aggiornamento secondo la distribuzione di probabilità definita.

La dinamica della rete può quindi essere descritta come$$\mathbf{x}_i(t+1)=f_i^{(k)}(\mathbf{x}(t)) \quad \text{con probabilità } p_i^{(k)}$$dove $x(t)$ rappresenta lo stato globale della rete al tempo $t$.

Questo approccio permette di modellare diversi fenomeni biologici:
- **rumore molecolare** nei processi cellulari
- **variabilità tra cellule**l
- **incertezza nelle interazioni regolatorie**
- **regolazioni alternative** dello stesso gene.

A differenza delle [[GRN - Boolean Networks|Boolean Networks]] classiche, l’evoluzione del sistema non è più deterministica ma definisce una **[[Markov chains|catena di Markov]]** sullo spazio degli stati$$S=\{0,1\}^n$$in cui ogni stato può avere più possibili successori associati a probabilità.

Analogamente agli altri modelli di [[Gene Regulatory Networks (GRN)|GRN]]:
- lo stato della rete è un vettore booleano
- la dinamica può essere analizzata tramite **attrattori probabilistici**
- l’analisi si concentra sulle **distribuzioni stazionarie** degli stati.

Dal punto di vista formale le probabilistic Boolean networks non aumentano la capacità espressiva delle [[GRN - Boolean Networks|Boolean Networks]], ma introducono un livello di **modellazione probabilistica** che permette di rappresentare meglio la natura stocastica dei sistemi biologici

Nella modellazione delle [[Gene Regulatory Networks (GRN)|GRN]] le **Probabilistic Boolean Networks** permettono di rappresentare **ipotesi alternative di regolazione** inferite dai dati sperimentali. Più funzioni di aggiornamento per lo stesso gene possono infatti rappresentare diversi possibili schemi di interazione tra geni.

Questo modello consente inoltre di catturare:
- **variabilità tra cellule**
- **regolazione dipendente dal contesto biologico**

Il comportamento a lungo termine della rete può essere interpretato in termini di:
- **destini cellulari predominanti**
- **probabilità di transizione tra diversi fenotipi**

Le PBNs sono quindi utilizzate per:
- modellare **profili di espressione genica rumorosi**
- studiare la **robustezza degli attrattori** sotto perturbazioni stocastiche
- progettare **strategie di intervento** per guidare la rete verso attrattori desiderati.