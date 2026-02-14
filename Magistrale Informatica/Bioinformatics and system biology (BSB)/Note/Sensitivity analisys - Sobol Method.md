---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Sensitivity analisys - Sobol Method
---
Il **Sobol method** è un metodo di **[[Sensitivity analisys|Sensitivity analisys]] globale** basato sulla decomposizione della varianza dell’output del modello nei contributi attribuibili ai singoli parametri e alle loro interazioni.

Sia un modello scalare:
$$
Y = f(p_1, \dots, p_k)
$$
dove i parametri $p_i$ sono trattati come variabili casuali indipendenti definite su intervalli assegnati.

L’idea fondamentale è decomporre la varianza totale dell’output:
$$
V(Y) = Var(Y)
$$
nella somma dei contributi dovuti ai singoli parametri e alle loro interazioni:

$$
V(Y) = \sum_i V_i + \sum_{i<j} V_{ij} + \dots + V_{1\dots k}
$$

dove:
- $V_i$ è il contributo alla varianza dovuto esclusivamente al parametro $p_i$,
- $V_{ij}$ è il contributo dovuto all’interazione tra $p_i$ e $p_j$,
- i termini di ordine superiore rappresentano interazioni multiple.

Da questa decomposizione si definiscono gli **indici di Sobol**.

Indice di primo ordine:
$$
S_i = \frac{V_i}{V(Y)}
$$
misura la frazione della varianza spiegata dal solo parametro $p_i$.

Indice totale:
$$
S_{T_i} = \frac{V_i + \text{tutte le interazioni che coinvolgono } p_i}{V(Y)}
$$
misura il contributo complessivo del parametro, includendo tutte le interazioni con altri parametri.

Interpretazione:
- $S_i$ grande ⇒ forte effetto individuale del parametro.
- $S_{T_i}$ grande ⇒ parametro globalmente influente.
- Differenza $S_{T_i} - S_i$ grande ⇒ presenza di forti interazioni con altri parametri.
- $S_{T_i} \approx 0$ ⇒ parametro trascurabile.

Dal punto di vista concettuale:
- $S_i$ rappresenta la quota di varianza spiegata dal parametro isolatamente.
- $S_{T_i}$ rappresenta il contributo totale del parametro nel sistema.

Il metodo richiede campionamento Monte Carlo o quasi-Monte Carlo e un numero elevato di simulazioni, risultando computazionalmente più costoso rispetto al Morris method, ma fornisce una quantificazione completa e rigorosa degli effetti globali.

Workflow tipico:
1. Screening preliminare con Morris per identificare parametri potenzialmente rilevanti.
2. Analisi dettagliata con Sobol per quantificare precisamente contributi individuali e interazioni.

![[IMG - Sensitivity analisys - Sobol Method.png]]
![[IMG - Sensitivity analisys - Sobol Method.png]]