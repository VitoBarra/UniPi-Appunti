---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area: 
topic: 
SubTopic:
---

# Clausola definita e Clausola di Horn
---
le **Clausola definita e le Clausola di Horn** sono una forma più restrittiva della [[Forma normale congiuntiva (CNF)]] che hanno la stessa struttura ma hanno delle restrizioni in più sulle clausole:  
***clausola definita***: ovvero una *disgiunzione* ($\lor$) di letterali in cui **esattamente uno** è positivo.
***clausola di Horn***: generalizzazione della ***clausola definita***, che consente **al massimo** un letterale positivo.

Le clausole di Horn risultano [[Operazioni chiuse|chiuse]] rispetto all'[[Inferenza logica per dimostrazione di teoremi|operazione di risoluzione]]: la combinazione di due clausole di Horn tramite risoluzione produce nuovamente una clausola di Horn. Inoltre, 

ogni **clausola definita** può essere riscritta come [[Logica proposizionale|implicazione]] con un corpo (***body***) costituito da una congiunzione di letterali positivi e una testa (***head***) rappresentata da un singolo letterale positivo. Formalmente, una clausola come $(\neg P_1 \lor \neg P_2 \lor P_3)$, dove $P_3$ è l unico letterale positivo, si traduce nell'[[Logica proposizionale|implicazione]] $(P_1 \land P_2) \Rightarrow P_3$ e questa formulazione è generalmente più semplice da interpretare.

le **clausole** composte da un singolo letterale positivo, sono detti *fatti* (*facts*).





