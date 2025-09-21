---
Course: "[[Fondamenti Del Informatica (FDI)]]"
Course 1: "[[Artificial Intelligence Fundamentals (AIF)]]"
Course 2: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
tags:
  - FDI
  - IIA
  - AIF
Area:
topic:
SubTopic:
---
# Inferenza logica per Model cheeking
il **model checking** è una classe di [[Algoritmi|algoritmi]] per l' [[Sistemi di inferenza logica|inferenza logica]] che si basano sul un implementazione diretta della definizione di [[Conseguenza Logica (Deduzione)|conseguenza logica]].

infatti generalmente seguono una linea del tipo:
 Data una **base di conoscenza** $KB$ è un **enunciato** $\alpha$ e si vuole decidere se $KB \models \alpha$ ovvero se è  [[Conseguenza Logica (Deduzione)|conseguenza logica]] di $KB$ **allora** l'algoritmo controlla che in ciascun modello che soddisfa $KB$ soddisfi anche $\alpha$, confermando così che $M(KB) \subseteq M(\alpha)$. 

