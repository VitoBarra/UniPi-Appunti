---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area:
topic:
SubTopic:
---

# Inferenza logica - Algoritmo di risoluzione per FOL
---
l'**algoritmo di risoluzione** per la [[Logica del primo ordine (FOL)|logica del primo ordine]] è un [[Sistema di inferenza per FOL|sistema di inferenza]] che opera su un $KB$ con enunciati in[[Forma normale congiuntiva (CNF) per FOL| CNF per FOL]].

con L'**algoritmo di risoluzione** si vuole decidere se $KB \models \alpha$ ovvero se $\alpha$ è [[Conseguenza Logica (Deduzione)|conseguenza logica]] di $KB$  per fare ciò l'algoritmo dimostra che $KB \land \lnot\alpha$ è insoddisfacibile derivando la **clausola vuota** $\{\}$. Per fare ciò applica la regola di [[Inferenza logica - Regola risoluzione per FOL|risoluzione binaria]] a la $(KB \land \lnot\alpha)$ e poi applica il **factoring**, che rimuove letterali ridondanti riducendo due letterali ad uno a se sono unificabili e applicando l'[[FOL - Algoritmo di unificazione|unificatore]] all'intera clausola. 

Durante l'unificazione può essere necessario **standardizzare le variabili** per evitare conflitti di nomi tra le clausole. Il procedimento di risoluzione basato sull'unificazione è **corretto** e diventa **completo** grazie che la procedura è completa per il [[Sistemi di inferenza logica#Teorema di refutazione|Teorema di refutazione]] ovvero genera $\{\}$ se l input non è [[Logica|soddisfacibile]].
