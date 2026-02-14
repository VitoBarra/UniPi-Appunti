---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GRN - Fuzzy Boolean Networks
---
**Fuzzy Boolean Networks** sono una variante delle [[GRN - Boolean Networks|Boolean Networks]] per modellare [[Gene Regulatory Networks (GRN)|GRN]] in cui gli stati dei geni non sono limitati ai valori booleani $\{0,1\}$ ma possono assumere **valori continui nell’intervallo** $[0,1]$. Questo permette di rappresentare in modo più realistico i **livelli graduali di espressione genica**.

In questo modello ogni gene $x_i$ assume un valore$$x_i(t) \in [0,1]$$dove:
- $0$ rappresenta **assenza di espressione**
- $1$ rappresenta **massima espressione**
- valori intermedi rappresentano **livelli parziali di attività** che catturano fenomeni di dose-base response o saturazione

Lo stato globale della rete è un vettore continuo$$x(t)=(x_1(t),\dots,x_n(t)) \in [0,1]^n$$e l’evoluzione della rete descrive una dinamica nello spazio continuo degli stati. mentre le funzioni di aggiornamento assumono la forma$$x_i(t+1)=\mu_i\big(f_i(x_1(t),\dots,x_n(t))\big)$$dove:
- $f_i$ è una **combinazione [[Logica Fuzzy|fuzzy]]** degli input provenienti dai geni regolatori
- $\mu_i$ è una **funzione di attivazione** (potenzialmente non lineare) che trasforma il segnale aggregato nel livello di espressione del gene.

Le interazioni tra geni sono descritte tramite **operatori della logica fuzzy**, che generalizzano gli operatori booleani classici. Ad esempio:
- AND logico $\rightarrow$ operatore fuzzy come $\min(x,y)$
- OR logico $\rightarrow$ operatore fuzzy come $\max(x,y)$
- NOT logico $\rightarrow$ $1-x$


Analogamente agli altri modelli di [[Gene Regulatory Networks (GRN)|GRN]]:
- la dinamica può convergere verso **attrattori**
- gli attrattori rappresentano **configurazioni stabili di attività genica**
- diverse regioni dello spazio degli stati possono corrispondere a **diversi fenotipi cellulari**.

Dal punto di vista della modellazione le fuzzy Boolean networks permettono di:
- rappresentare **livelli graduali di espressione**
- modellare **interazioni regolatorie non strettamente binarie**
- integrare più facilmente **dati quantitativi di espressione genica**.

Questo formalismo mantiene la struttura logica delle reti booleane ma introduce una rappresentazione più continua e flessibile delle dinamiche regolatorie.


**Vantaggi**:
  - dinamiche più **continue e graduali**
  - più vicine ai **modelli continui**
  - mantengono una struttura **relativamente semplice**
**Limiti**:
  - la scelta dei **parametri** e della forma delle funzioni fuzzy può essere **non banale**