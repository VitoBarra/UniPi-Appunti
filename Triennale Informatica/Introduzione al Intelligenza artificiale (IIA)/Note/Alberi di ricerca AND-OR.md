---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - IIA
  - AIF
topic: nota
---

# Alberi di ricerca AND-OR
---
gli **Alberi di ricerca AND-OR** sono alberi usati per rappresentare lo spazio degli stati durante la [[Problemi di Ricerca in spazi non deterministici|ricerca]] in [[Definizione di Problemi-Ambienti|ambienti non deterministici]]. 

è un [[Alberi|albero]] composti da due tipi di nodi: 
- I nodi **_OR_** rappresentano le scelte dell’agente, ovvero la selezione di una singola azione da eseguire.
- I nodi **_AND_** rappresentano le contingenze introdotte dall’ambiente: a seguito dell’esecuzione di un'azione, possono verificarsi più risultati possibili, tutti da considerare nel piano.
questi due tipi di nodi si alternano rappresentando le risposte del ambiente alle possibili azioni del agente

Una **soluzione** a un problema di ricerca **_AND-OR_** ovvero un **piano condizionale** è un sottoalbero che soddisfa tre condizioni fondamentali:
- ogni foglia corrisponde a un nodo **obiettivo**
- in ogni nodo **OR** viene specificata una sola azione
- da ogni nodo **AND** vengono inclusi tutti gli archi che rappresentano i possibili risultati dell’azione eseguita.

un **albero AND-OR**, puo essere esplorato usando gli algoritmi di ricerca classici come la[[Ricerca in profondita (DF)|Ricerca in profondita]] o la [[Ricerca in ampiezza (BF)|ricerca in ampieza]].

l algoritmo pseudo codice che ritorna un piano condizionale o fallimento è il seguente:
```pseudo
	\begin{algorithm}
	\caption{AND-OR-SEARCH}
	\begin{algorithmic}

\Function{AND-OR-SEARCH}{problem}  
    \Return \Call{OR-SEARCH}{problem, problem.\textsc{Initial}, []}
\EndFunction

\State

\Function{OR-SEARCH}{problem, state, path}   
    \If{problem.\Call{Is-Goal}{state}}
	     \Return the empty plan
	 \EndIf  
     \If{\Call{Is-Cycle}{path}}
	    \Return failure
     \EndIf  
    \ForAll{$action$ in problem.\Call{Actions}{state}}  
        \State plan $\gets$ \Call{AND-SEARCH}{problem, \Call{Results}{state, action}, $[state] + path$}  
        \If{$plan \neq$ failure} 
	        \Return $[action] + plan$
        \EndIf  
    \EndFor  
    \Return failure  
\EndFunction  

\State

\Function{AND-SEARCH}{problem, states, path}  
	\State palans $\gets$ []
    \ForAll{$s_i \in states$}  
        \State $plan_i \gets$ \Call{OR-SEARCH}{problem, $s_i$, $path$}  
        \If{$plan_i = failure$}
	        \Return failure  
        \EndIf 
    \EndFor  
	\Return plans[$s_i$]
\EndFunction
\end{algorithmic}
\end{algorithm}
```

Durante la ricerca va verificata la presenza di cicli per garantire la terminazione in spazi di **stato finiti** infatti se viene rilevata la ripetizione di uno stato **lungo il cammino attuale**, l’algoritmo ritorna fallimento per evitare di restare incastrato in un ciclo.
**Non** si esclude la possibilità che esista una soluzione **non ciclica** accessibile da una precedente occorrenza di quello stato.

alcune **soluzioni cicliche** possono essere **valide** purché la natura del **non determinismo** del ciclo permette un uscita, come ad esempio un azione che puo fallire con una certa probabilita ma che riprovando potrebbe portare allo stato aspettato, se invece riflette una condizione **persistente e non osservata**, come ad esempio un guasto, la ripetizione dell’azione non porta al raggiungimento dell’obiettivo. 