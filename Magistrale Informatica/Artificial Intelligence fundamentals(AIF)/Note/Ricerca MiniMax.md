---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Ricerca MiniMax
---
l **algoritmo di ricerca MINIMAX** è un [[Problemi di ricerca|algoritmo di ricerca]] per [[Ricerca in ambienti competitivi|ambienti competitivi]], in particolare si usano nel contesto dei [[Giochi a somma zero|Giochi a somma zero]]

l'algoritmo presuppone di usare un agente con utilità che usa il valore di **minimax** per guidare la scelta, in particolare si scegli sempre l'azione che massimizza l utilità e si assume che l altro [[Agenti Razionali|agente]] prenderà sempre l azione che minimizzerà  l utilità.

lo pseudo codice è il seguente:
```pseudo
\begin{algorithm}
\caption{Ricerca Minimax}
\begin{algorithmic}

\Function{MINIMAX-SEARCH}{game, state}
    \State player $\gets$ game.\call{To-MOVE}{state}
    \State value, move $\gets$ \call{MAX-VALUE}{game, state, player}
    \Return move
\EndFunction

\state 

\Function{MAX-VALUE}{game, state, player}
    \If{game.\call{Is-TERMINAL}{state}}
	\Return game.\call{UTILITY}{state, player}, null
    \EndIf
    \State v $\gets -\infty$
	\Forall{a in game.\call{ACTIONS}{state}}
        \State v2, a2 $\gets$ \call{MIN-VALUE}{game, game.\call{RESULT}{state, a}, player}
        \If{v2 > v}
            \State v, move $\gets$ v2, a
        \EndIf
    \EndFor
    \Return v, move
\EndFunction

\state 

\Function{MIN-VALUE}{game, state, player}
    \If{game.\call{Is-TERMINAL}{state}}
        \Return game.\call{UTILITY}{state, player}, null
    \EndIf
    \State v $\gets +\infty$
	    \Forall{a in game.\call{ACTIONS}{state}}
        \State v2, a2 $\gets$ \call{MAX-VALUE}{game, game.\call{RESULT}{state, a}, player}
        \If{v2 < v}
            \State v, move $\gets$ v2, a
        \EndIf
    \EndFor
    \Return v, move
\EndFunction

\end{algorithmic}
\end{algorithm}

```

Questo approccio presuppone che anche **MIN** giochi in modo ottimale. Se invece **MIN** adotta una strategia subottimale, **MAX** otterrà un risultato almeno pari a quello previsto contro un avversario perfetto. Tuttavia, ciò non implica che sia sempre vantaggioso seguire ciecamente la mossa ottimale **minimax** contro un avversario imperfetto, può succedere che prendere un masso più rischiosa (non ottimale) porti ad ottenere un valore **minimax** più alto in stati successivi, in pratica si spera in un "errore" del avversario.
![[IMG - albero MiniMax.png]]

### Analisi della complessità
Sia  
- $b=$ fattore di ramificazione (*B*ranching), ovvero il numero massimo di mosse legali per ciascuno stato  
- $m=$ profondità massima dell’albero di gioco (*M*ax)  

- **_[[Complessita|Complessità spazio]]_** (memoria):  
  - $O(bm)$ se tutte le azioni vengono generate contemporaneamente  
  - $O(m)$ se le azioni vengono generate una alla volta  
- **_[[Complessita|Complessità nel tempo]]_** (nodi generati):  
  - $O(b^m)$ crescita esponenziale con la profondità massima  


L’intrinseca complessità dell’approccio rende l’applicazione diretta dell’algoritmo minimax impraticabile per giochi complessi, Nonostante ciò, il valore teorico dell’algoritmo minimax rimane fondamentale per l’analisi matematica dei giochi, rappresentando una base di riferimento dalla quale derivano algoritmi più efficienti ottenuti tramite opportune approssimazioni del modello originale.
