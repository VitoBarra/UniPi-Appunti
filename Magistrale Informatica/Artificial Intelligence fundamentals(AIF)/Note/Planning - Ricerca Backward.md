---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning - Ricerca Backward
---
La **Ricerca Backward** per il [[planning|planning]] nota anche come **regression search**, parte dallo **stato obiettivo** e applica le azioni in senso inverso fino a trovare una sequenza di passi che conduca allo stato iniziale. 
Ad ogni passo vengono considerate solo le **azioni rilevanti**, riducendo in modo significativo il fattore di ramificazione rispetto alla [[Planning - Ricerca Forward|ricerca forward]]. Un'azione è considerata rilevante se possiede un **effetto** che [[FOL - Algoritmo di unificazione|unifica]] con uno dei letterali dell'**obiettivo** senza però negarne alcuna parte.  

Applicare un'azione in direzione inversa significa, dato un obiettivo $g$ e un'azione $a$, ottenere una descrizione dello stato regressa $g'$ i cui letterali positivi e negativi sono definiti come:  $$
\begin{array}{}
POS(g')  & = &  (POS(g) - ADD(a)) \cup POS(Precond(a))\\
NEG(g')  & = &  (NEG(g) - DEL(a)) \cup NEG(Precond(a)) \\
\end{array}
$$Le precondizioni devono essere soddisfatte prima dell'esecuzione dell'azione, mentre i letterali positivi o negativi introdotti o rimossi dall'azione non devono necessariamente essere veri precedentemente. Quando l'obiettivo o l'azione contengono variabili, è necessario un processo di [[FOL - Algoritmo di unificazione|unificazione]] per ottenere [[FOL - Sostituzione|sostituzioni]] appropriate, standardizzando eventualmente i nomi delle variabili per evitare conflitti.  

Formalmente, dato un obiettivo $g$ contenente un letterale $g_i$ e uno schema d'azione $A$, se $A$ possiede un letterale d'effetto $e'_j$ tale che $Unify(g_i, e'_j) = \theta$ e se si definisce $A' = SUBST(\theta, A)$, e se non vi è alcun effetto in $A'$ che sia la negazione di un letterale in $g$, allora $A'$ è un'azione rilevante rispetto a $g$.  

In generale, nei domini di problemi tipici la ricerca all'indietro mantiene un fattore di ramificazione più basso rispetto alla ricerca in avanti. Tuttavia, l'utilizzo di stati con variabili rende più difficile la definizione di euristiche efficaci, motivo per cui molti sistemi moderni preferiscono la [[Planning - Ricerca Forward|ricerca in avanti]].
