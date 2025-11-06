---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza logica - Backard chaining con FOL
---
L’algoritmo di inferenza **Backward Chaining (FOL-BC-ASK)** applicato alla [[Logica del primo ordine (FOL)|logica del primo ordine]] costituisce un [[Sistema di inferenza per FOL|sistema deduttivo]] basato sulla strategia **goal-driven**, volto a verificare se un obiettivo $goal$ è [[Conseguenza Logica (Deduzione)|conseguenza logica]] di una base di conoscenza $KB$ di [[Forma a clausole definite per FOL|insieme di clausole definite]] e di **fatti noti**.  

Si vuole decidere se $KB \models goal$, ovvero se la **frase atomica** $goal$ può essere dimostrata a partire da $KB$. Per fare ciò, l'[[Algoritmi|algoritmo]] esplora la base di conoscenza alla ricerca di regole della forma $lhs \Rightarrow goal$, verificando se le **premesse** $lhs$ sono soddisfatte dai fatti noti o possono essere a loro volta dimostrate ricorsivamente. Quando un fatto atomico corrisponde direttamente a una clausola di $KB$ è considerato come se $lhs=\{\}$. L’algoritmo termina quando l’obiettivo è dimostrato oppure quando nessuna regola può supportarne ulteriormente la dimostrazione.

L'algoritmo è progettato come **generatore**, in quanto le interrogazioni contenenti variabili possono produrre molteplici sostituzioni, fornendo quindi più risultati. Questo meccanismo rende il **backward chaining** un tipo di **[[Alberi di ricerca AND-OR|ricerca AND/OR]]**, dove la componente OR corrisponde alla possibilità di provare il goal tramite diverse regole della base di conoscenza, mentre la componente AND richiede la dimostrazione simultanea di tutti i congiunti del $lhs$.

Il funzionamento interno può essere schematizzato con tre procedure principali. FOL-BC-OR individua tutte le clausole compatibili con il goal, standardizzando le variabili per evitare conflitti, e verifica l'unificazione tra il lato destro della regola e il goal. Successivamente, FOL-BC-AND dimostra ogni congiunto del $lhs$, accumulando le sostituzioni necessarie:
```pseudo
\begin{algorithm}
\caption{backward chining per FOL con generatori}
\begin{algorithmic}
\Function{FOL-BC-ASK}{$KB, query$}
    \Return \Call{FOL-BC-OR}{$KB, query, \{\}$}
\EndFunction

\State

\Function{FOL-BC-OR}{$KB, goal, \theta$}
    \For{each $rule$ in \Call{FETCH-RULES-FOR-GOAL}{$KB, goal$}}
        \State $(lhs \Rightarrow rhs) \gets$ \Call{STANDARDIZE-VARIABLES}{$rule$}
        \For{each $\theta'$ in \Call{FOL-BC-AND}{$KB, lhs, $ \Call{UNIFY}{$rhs, goal, \theta$}}}
            \State \textbf{yield} $\theta'$
        \EndFor
    \EndFor
\EndFunction

\State

\Function{FOL-BC-AND}{$KB, goals, \theta$}
    \If{$\theta =$ failure}
        \Return
    \ElsIf{\Call{LENGTH}{$goals$} $= 0$}
        \State \textbf{yield} $\theta$
    \Else
        \State $first, rest \gets$ \Call{FIRST}{$goals$}, \Call{REST}{$goals$}
        \For{each $\theta'$ in \Call{FOL-BC-OR}{$KB, $ \Call{SUBST}{$\theta, first$}, $\theta$}}
            \For{each $\theta''$ in \Call{FOL-BC-AND}{$KB, rest, \theta'$}}
                \State \textbf{yield} $\theta''$
            \EndFor
        \EndFor
    \EndIf
\EndFunction

\end{algorithmic}
\end{algorithm}
```
o alternativamente in modo imperativo 
```pseudo
	\begin{algorithm}
	\caption{backward chainin imperativo}
	\begin{algorithmic}
\Function{FOL-BC-Ask}{$KB, goals, \theta$}
    \State \textbf{returns} a set of substitutions
    \State \textbf{inputs:} $KB$, a knowledge base  
    \State  $goals$, a list of conjuncts forming a query ($\theta$ already applied)  
    \State  $\theta$, the current substitution, initially the empty substitution $\{\}$
    \State \textbf{local variables:} $answers$, a set of substitutions, initially empty
    \If{$goals$ is empty}
        \Return $\{\theta\}$
    \EndIf
    \State $q' \gets$ \Call{Subst}{$\theta$, \Call{First}{$goals$}}
    \For{each sentence $r$ in $KB$}
        \State \textbf{where} \Call{Standardize-Apart}{$r$} = $(p_1 \land \cdots \land p_n \Rightarrow q)$
        \State \textbf{and} $\theta' \gets$ \Call{Unify}{$q, q'$} succeeds
        \State $new\_goals \gets [p_1, \cdots, p_n |$ \Call{Rest}{$goals$}]        \State $answers \gets$ \Call{FOL-BC-Ask}{$KB, new\_goals, $ \Call{Compose}{$\theta', \theta$}} $\cup$ $answers$
    \EndFor
    \Return $answers$
\EndFunction
\end{algorithmic}
\end{algorithm}
```
L'algoritmo, essendo una ricerca **[[Ricerca in profondita (DF)|depth-first]]**, richiede uno spazio proporzionale alla dimensione della prova, ma può incontrare difficoltà legate a stati ripetuti e incompletezza. Nonostante questi limiti, il **backward chaining** si usa molto in [[Programmazione logica|logic programming]]