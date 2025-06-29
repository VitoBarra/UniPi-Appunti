---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IA
  - AIF
---
# Agenti Knowledge Based
---
- una [[Agenti Razionali|agente]] basato sulla conoscenza mantiene una _[[Base di conoscenza (KB)|Base di conoscenza]]_ detta _knowledg base_ o _KB_: un insieme di enunciati espressi in un linguaggio di rappresentazione
- interagisce con la KB mediante una interfaccia funzionale tell-ask
	- _tell_: per aggiungere nuovi enunciati da KB
	- _ask_: per interrogare la knowledge base
	- _react_: per eliminare enunciati
- gli enunciati nella _KB_ rappresentano le opinioni/credenze del agente
- la e risposte $\alpha$ devono essere tali che $\alpha$ discende necessariamente da _KB_


## Trade-off fondamentale dell R.C
il problema _fondamentale_ in R.C. è trovare il giusto compromesso tra:
- _Espressivita_ del linguaggio di rapresentazione
- _Complessita_ del meccanismo inferenziale
queste due caratteristiche sono in contrasto tra loro siccome un linguaggio piu _espressivo_ rende meno efficente il meccanismo inferenziale 



### Formalismi per la rappresentazione della conoscenza
una formalismo per la rappresentazione della conoscenza ha tre componenti:
1. _sintassi_: un linguaggio composto d un vocabolario e regole per la formazione delle frasi (_enunciati_)
2. _semantica_: stabilisce una corrispondenza tra gli enunciati e i fatti del mondo; se una agente ha un enunciato $\alpha$ nella sua KB crede che il fatto corrispondente sia vero nel mondo
3.  _[[Sistemi di deduzione (o di Inferenza)|meccanismo inferenziale]]_: codificato tramite delle regole che ci consente di inferire nuovi fatti dai fatti presenti nella KB
 

### Rappresentazione del mondo
![[IMG - rappresentazione sentence e mondo reale.png]]

#### Problemi di questo tipo di agente
1. complessità di $KB \models \alpha$
2. quali sono gli algoritmi di decisione e le strategie di ottimizzazione?
3. i Linguaggi logici:
	1. [[ Calcolo proposizionale (PROP)|calcolo proposizionale]]
	2. [[Logica del primo ordine (FOL)|Logica del predicati del prim ordine]]
4. questi linguaggio sono adatti per la rappresentazione della conoscenza?




```pseudo
\begin{algorithm}
\caption{KB-AGENT}
\begin{algorithmic}
\Function{KB-AGENT}{percept} \textbf{returns} an action
\State persistent: $KB$, a knowledge base
\State persistent: $t$, a counter, initially 0, indicating time

\State \call{TELL}{$KB$, \call{MAKE-PERCEPT-SENTENCE}{percept, $t$}}
\State $action \gets \textproc{ASK}($KB$, \textproc{MAKE-ACTION-QUERY}($t$))$
\State \textproc{TELL}($KB$, \textproc{MAKE-ACTION-SENTENCE}(action, $t$))
\State $t \gets t + 1$
\Return $action$
\EndFunction
\end{algorithmic}
\end{algorithm}
```