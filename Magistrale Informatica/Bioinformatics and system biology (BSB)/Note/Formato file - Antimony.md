---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Formato file - Antimony
---
Il formato **Antimony** è un linguaggio testuale compatto per la definizione di modelli di [[Chemical Reaction Network (CRN)|CRNs]] e sistemi dinamici in biologia dei sistemi. **Antimony** è progettato per essere leggibile dall’uomo e facilmente modificabile, mantenendo la possibilità di conversione automatica verso [[Formato file - System biology markup Language (SBML)|SBML]].

Antimony rappresenta quindi un livello ad alto livello di astrazione che viene tradotto in [[Formato file - System biology markup Language (SBML)|SBML]] per simulazione, condivisione e interoperabilità.
Antimony si colloca tra descrizione concettuale e simulazione numerica:
$$CRN → Antimony → SBML → simulazione (\text{ODE o stocastica})$$
Fornisce quindi uno strumento pratico per passare rapidamente da un modello formale di [[Chemical Reaction Network (CRN)|CRN]] alla sua analisi computazionale.

la Struttura generale di un modello Antimony Un modello è definito tramite:
- dichiarazione del modello  
- definizione delle specie  
- definizione delle reazioni  
- definizione dei parametri  
- eventuali regole, funzioni o eventi  

Esempio minimale di struttura:
```
model nome_modello()  
    J1: A + B -> C; k*A*B  
    k = 0.1  
    A = 10  
    B = 5  
    C = 0  
end  
```

Elementi chiave:
- `J1` identificatore della reazione  
- `A + B -> C` stechiometria  
- `k*A*B` legge cinetica  
- assegnazioni finali condizioni iniziali o parametri  

Relazione con la legge di [[CRN - Modello mass-action|azione di massa]]

Per una reazione:$$\ell_1 S_1 + \dots + \ell_\rho S_\rho \xrightarrow{k} \ell'_1 P_1 + \dots + \ell'_\gamma P_\gamma$$la legge cinetica in Antimony è espressa direttamente come formula algebrica, ad esempio:
J: S1 + S2 -> P; k*S1*S2  
La dinamica risultante è derivata automaticamente come sistema di ODE:$$\frac{d[S]}{dt} = \sum_{\text{prod}} \ell r - \sum_{\text{react}} \ell r$$
Caratteristiche principali
- Sintassi compatta e leggibile  
- Conversione bidirezionale Antimony ↔ SBML  
- Supporto per:
  - reazioni reversibili  
  - compartimenti  
  - regole algebriche  
  - eventi  
  - funzioni personalizzate  
- Modularità e riuso di sottosistemi  

---

Modularità

Antimony consente:

- definizione di modelli riutilizzabili  
- istanziazione multipla di sottosistemi  
- composizione gerarchica  

Questo è utile nella costruzione modulare di modelli complessi di [[Gene Regulatory Networks (GRN)|Gene Regulatory Networks (GRNs)]] o pathway multi-livello.

---

Librerie e strumenti disponibili

libAntimony  
- Libreria ufficiale in C/C++  
- Conversione Antimony ↔ SBML  
- Integrabile in applicazioni custom  
Tellurium  
- Ambiente Python per modellazione e simulazione  
- Integra Antimony per la definizione dei modelli  
- Include libSBML e libRoadRunner  
- Permette simulazioni deterministiche e stocastiche  
libRoadRunner  
- Motore ad alte prestazioni per modelli SBML  
- Supporta:
  - integrazione ODE  
  - simulazione stocastica (Gillespie)  
  - analisi steady-state  
- Utilizzabile direttamente da Python  


