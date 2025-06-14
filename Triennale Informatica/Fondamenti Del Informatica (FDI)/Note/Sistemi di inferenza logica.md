---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - FDI
  - AIF
  - IIA
Area: 
topic: nota
SubTopic:
---
# Sistemi di inferenza logica
---
Nel contesto della [[Logica|logica]] un **sistema di inferenza** o **di deduzione** è una classe di [[Algoritmi|algoritmi]] per generare **nuova conoscenza** a partire un **insieme di conoscenze** (**knowledge base**) indicato con $KB$, ovvero si vuole capire quali enunciato sono [[Conseguenza Logica (Deduzione)|conseguenza logica]] di $KB$. Per fare ciò si combinano le conoscenze pregresse con delle regole definite tramite [[Linguaggi formali|Linguaggi formali]].

indicando con $i$  un generico **sistema di inferenza** allora si denota il fatto che l'**enunciato** $\alpha$ è **derivabile** (**deducibile**) da $KB$ con $$KB \vdash_i \alpha$$ letto $\alpha$ è derivabile da $KB$ tramite $i$

Un **sistema di inferenza** ha due proprietà fondamentali:
1. **_Correttezza_** (**soundness**): tutti gli enunciati $\alpha$ derivabili sono **conseguenza logica** di $KB$ ovvero le regole **preservano la verità**. vale quindi che $KB \vdash_i \alpha\implies KB \models_i \alpha$
2. **_Completezza_** (**Completeness**): tutto ciò che è [[Conseguenza Logica (Deduzione)|conseguenza logica]] è ottenibile tramite in **sistema inferenziale** ovvero vale  che  $KB \models \alpha \implies KB \vdash_i \alpha$





>[!warning]
>il problema di fare inferenza logica ha classe di complessità [[Classi di complessita- co-NP-completo|co-NP-completo]] quindi è difficile almeno come un problema [[Classi di complessita - NP-Completo|NP-Completo]] e ogni algoritmo conosciuto per ha complessità esponenziale nel caso peggiore rispetto alla dimensione dell'input.

