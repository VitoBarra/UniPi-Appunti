---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza logica - Regola Modus Ponens generalizata
---
Il **Generalized Modus Ponens (GMP)** estende il concetto di **[[Inferenza logica per dimostrazione di teoremi|Modus Ponens]]** della [[Logica proposizionale|logica proposizionale]] alla [[Logica del primo ordine (FOL)|logica del primo oridne]]. Il **GMP** può essere considerato una forma di **Modus Ponens sollevato ([[Inferenza logica - regole di inferenza lifted|lifted]])**, poiché lavora direttamente su formule con variabili senza necessità di proposizionalizzare completamente la base di conoscenza. Questo evita la creazione di istanze ridondanti, mantenendo l'inferenza più compatta e mirata.

**Sia**
- $p_1', \dots, p_n',p_1, \dots, p_n$ atomi presenti nella base di conoscenza $KB_{FOL}$ e si assume abbiano solo qualificatori universali.
- $\theta$ una sostituzione tale che $SUBST(\theta, p_i') = SUBST(\theta, p_i), \forall i$
**allora**$$\frac{p_1', \dots, p_n', (p_1 \land \dots \land p_n \implies q)}{\text{SUBST}(\theta, q)} $$Il meccanismo consiste nel determinare $\theta$ in modo che ciascun $p_i$ corrisponda a $p_i'$ nella base di conoscenza. Applicando $\theta$ all'implicazione si ottiene l'istanza del conseguente $q$, ovvero $\text{SUBST}(\theta, q)$.

Dalla validità universale di ogni formula $p$ segue che, per qualunque sostituzione , vale $p \models \text{SUBST}(\theta, p)$ secondo il principio di [[Riduzione da FOL ad logica proposizionale|Universal Instantiation]]. In particolare, da $$p_1', \dots, p_n' \iff SUBST(\theta, p_1') \land \dots \land SUBST(\theta, p_n')$$, mentre dall’implicazione $$(p_1 \land \dots \land p_n \implies q) \iff (SUBST(\theta, p_1) \land \dots \land SUBST(\theta, p_n) \implies SUBST(\theta, q))$$ e poiché $\theta$ è definita in modo tale che $SUBST(\theta, p_i') = SUBST(\theta, p_i)$ per ogni $i$, le due congiunzioni coincidono perfettamente. Di conseguenza, il conseguente $\text{SUBST}(\theta, q)$ segue logicamente per applicazione diretta del **Modus Ponens**, garantendo la **soundness** del meccanismo di inferenza.


