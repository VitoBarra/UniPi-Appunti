---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# FOL - Algoritmo di unificazione
---
L'**unificazione** nella [[Logica del primo ordine (FOL)|logica del primo ordine]] è un'operazione che consente di rendere due **enunciati** identici tramite una [[FOL - Sostituzione|sostituzione]] di variabili con termini, ovvero si vuole trovare
$UNIFY (p,q)= \theta$, tale che $SUBST(\theta,p)=SUBST(\theta,q)$ ovvero li rende identici, $\theta$ è detto **unificatore**, oppure un fallimento se le espressioni non possono essere unificate.  

per poter troavare un unificatore $p,q$ devono essere **standardizati** ovvero vanno rinominate le variabili duplicate per evitare ambiguità,  es: $\{x/g(y), y/z\}$, che deve essere standardizata in $\{x/g(z), y/z\}$.

per ogni coppia di espressioni $p,q$ esistono piu **unificatori** egualmente validi ma ne esiste uno solo che è il **Most General Unifier (MGU)**, l'unificatore più generale ovvero che impone il minor numero di vincoli possibile

L'**algoritmo di unificazione (UNIFY)** ricerca il **MGU** e  può essere descritto come segue:
```pseudo
\begin{algorithm}
\caption{Unify}
\begin{algorithmic}
\Function{Unify}{$x, y, \theta=\text{empty}$}
    \If{$\theta = \text{failure}$}
        \Return failure
    \ElsIf{$x = y$}
        \Return $\theta$
    \ElsIf{Variable?($x$)}
        \Return \textsc{Unify-Var}($x, y, \theta$)
    \ElsIf{Variable?($y$)}
        \Return \textsc{Unify-Var}($y, x, \theta$)
    \ElsIf{Compound?($x$) \textbf{and} Compound?($y$)}
        \Return \textsc{Unify}(\textsc{Args}($x$), \textsc{Args}($y$), \textsc{Unify}(\textsc{Op}($x$), \textsc{Op}($y$), $\theta$))
    \ElsIf{List?($x$) \textbf{and} List?($y$)}
        \Return \textsc{Unify}(\textsc{Rest}($x$), \textsc{Rest}($y$), \textsc{Unify}(\textsc{First}($x$), \textsc{First}($y$), $\theta$))
    \Else
        \Return failure
    \EndIf
\EndFunction
\end{algorithmic}
\end{algorithm}
```
L’algoritmo di unificazione esplora ricorsivamente le due espressioni "fianco a fianco", costruendo passo passo un unificatore. Se due corrispondenze non combaciano, l’unificazione fallisce. Durante questo processo viene eseguito l’**occur check**, che verifica che una variabile non compaia all’interno del termine con cui si tenta di unificarla. Se ciò avviene, l’unificazione fallisce poiché non può esistere un unificatore coerente; ad esempio, $S(x)$ non può unificarsi con $S(S(x))$. Tale controllo previene sostituzioni circolari e garantisce la consistenza logica, ma comporta un aumento della complessità dell’algoritmo fino a un ordine quadratico rispetto alla dimensione delle espressioni. Per ottimizzare le prestazioni, alcuni sistemi omettono l’**occur check**, delegando all’utente il compito di evitare inferenze non valide, mentre altri adottano versioni dell’algoritmo più efficienti, con complessità lineare.

