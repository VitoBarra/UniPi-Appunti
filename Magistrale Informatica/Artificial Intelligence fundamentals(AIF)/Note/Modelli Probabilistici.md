---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area:
topic:
SubTopic:
---

# Agire in domini incerti
---
Gli [[Agenti Razionali|agenti]] operanti in ambienti reali devono affrontare incertezze derivanti da [[Definizione di Problemi-Ambienti|osservazioni parziali, nondeterminismo o presenza di avversari]]. Essi possono non conoscere con certezza lo stato attuale del mondo né prevedere con assoluta sicurezza l'esito di una sequenza di azioni. La [[Logica|logica]] risulta insufficiente per catturare tale incertezza, poiché non permette di rappresentare situazioni in cui una **proposizione** non è né **completamente vera né completamente falsa** mentre invece la [[Definizione di Probabilita|probabilità]] fornisce un metodo sistematico per riassumere l'incertezza derivante da **incompletezza informativa** o **ignoranza teorica**, risolvendo in parte il problema della qualificazione.  
Per gestire **questa incertezza**, un agente mantiene uno **degree of belief**, una misura numerica della fiducia rispetto a una **proposizione**, compresa tra $0$ e $1$. Questa misura non riflette l'incertezza intrinseca del mondo, ma l'incertezza dovuta allo **stato di conoscenza** dell'agente. Nuove informazioni possono aggiornare il grado di credenza senza generare contraddizioni, permettendo di rappresentare formalmente la probabilità condizionata degli eventi.  

L'incertezza ha implicazioni dirette sulle decisioni razionali. La scelta di un'azione dipende sia dalle probabilità associate ai possibili esiti sia dalle **preferenze dell'agente**, rappresentate tramite la **teoria dell'utilità**. La combinazione di probabilità e utilità definisce la **teoria delle decisioni**, secondo la quale un agente è razionale se seleziona l'azione che **massimizza l'utilità attesa** ($MEU$) Un agente decisionale mantiene uno stato di credenza probabilistico e, per ciascuna azione possibile, calcola la probabilità dei possibili esiti. Sulla base di queste informazioni e delle valutazioni di utilità, seleziona l'azione con il massimo $MEU$. Il funzionamento concettuale può essere rappresentato come segue:  
```pseudo
\begin{algorithm}
\caption{Decision-Theoretic Agent}
\begin{algorithmic}
\Function{DT-AGENT}{percept}
    \State \textbf{returns} an action
    \State \textbf{persistent:} $belief\_state$, probabilistic beliefs about the current state of the world
    \State  $action$, the agent's action
    \State
    \State update $belief\_state$ based on $action$ and $percept$
    \State calculate outcome probabilities for actions,
    \State  given action descriptions and current $belief\_state$
    \State select $action$ with highest expected utility
    \State  given probabilities of outcomes and utility information
    \State
    \Return $action$
\EndFunction
\end{algorithmic}
\end{algorithm}
```