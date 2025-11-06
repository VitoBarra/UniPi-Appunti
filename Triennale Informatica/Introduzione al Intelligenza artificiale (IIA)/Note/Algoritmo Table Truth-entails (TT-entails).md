---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Artificial Intelligence Fundamentals (AIF)]]"
topic: nota
tags:
  - IIA
  - AIF
---


# Algoritmo Table Truth-entails (TT-entails)  
---
l [[Algoritmi|algoritmo]] **Table Truth - ENTAILS** (**TT-ENTAILS**) è un algoritmo di [[Sistemi di inferenza logica|deduzione]], quindi si vuole decidere se dato **enunciato**  $\alpha$ questo è [[Conseguenza Logica (Deduzione)|conseguenza logica]] della base di conoscenza $KB$.

**TT-Entails** è un approccio [[Inferenza logica per Model cheeking|Model cheeking]] utilizza quindi direttamente la definizione di [[Conseguenza Logica (Deduzione)|conseguenza logica]], Infatti enumera tutti i [[Logica|modelli]] possibili, costruendo un **tabelle di verità**e controlla che tutti i modelli che soddisfano $KB$  soddisfano anche $\alpha$, questo 

Più in dettaglio l'algoritmo è simile a quello della [[Ricerca in profondita BackTracking (BDF)|ricerca con backtracking]] quindi è [[Ricorsione|ricorsivo]], percorrendo in profondità lo spazio delle assegnazioni di verità. Segue queste linee
- Per _ogni_ **modello** si ha che
	- Se il **modello soddisfa** $KB$ **allora** si controlla che **soddisfi** alche $\alpha$
		- Se **non** soddisfa $\alpha$ allora $\alpha$ non è conseguenza logica
		- se soddisfa $\alpha$ si va avanti
	- se non soddisfa $KB$ si va avanti
- una volta controllati tutti i modelli se non ci si è fermati prima allora $\alpha$ è conseguenza logica


Lo pseudo codice che ritorna $True$ o $False$ è il seguente:
```pseudo
\begin{algorithm}
\caption{TT-ENTAILS?}
\begin{algorithmic}
\Function{TT-ENTAILS?}{$KB, \alpha$} 
    \State \textbf{inputs:} $KB$, the knowledge base, a sentence in propositional logic
    \State $\alpha$, the query, a sentence in propositional logic
    \State symbols $\gets$ a list of the proposition symbols in $KB$ and $\alpha$
    \Return \call{TT-CHECK-ALL}{$KB, \alpha, \text{symbols}, \{\}$}
\EndFunction

\State 

\Function{TT-CHECK-ALL}{$KB, \alpha, \text{symbols}, \text{model}$} 
    \If{$\text{EMPTY?}(\text{symbols})$}
        \If{\Call{PL-TRUE?}{$KB, \text{model}$}}
            \Return \Call{PL-TRUE?}{$\alpha, \text{model}$}
        \Else
            \Return true \Comment{when $KB$ is false, always return true}
        \EndIf
    \Else
        \State $P \gets$ \Call{FIRST}{symbols}
        \State rest $\gets$ \Call{REST}{symbols}
        \Return \Call{TT-CHECK-ALL}{$KB, \alpha, \text{rest}, \text{model} \cup \{P = true\}$} \textbf{and}
        \State \Call{TT-CHECK-ALL}{$KB, \alpha, \text{rest}, \text{model} \cup \{P = false\}$}
    \EndIf
\EndFunction

\end{algorithmic}
\end{algorithm}
```

questo algoritmo ha le seguenti proprietà: 
- **Correttezza** (**soundness**): in quanto l'algoritmo aderisce alla definizione di implicazione logica
- **Completezza** (**completness**) in **spazi finiti**:  l'esplorazione esaustiva dello spazio dei modelli assicura che tutte le possibilità vengano considerate.
- **NON Completezza** (**completness**) in **spazi infiniti**: si puo bloccare in discese infinte

mentre dal punti di vista computazionale, indicando con  $n$ rappresenta il numero totale di simboli proposizionali coinvolti in $KB$ e $\alpha$ si ha che:
 - **[[Complessita|complessità temporale]]**:  $O(2^n)$ al caso pessimo vanno enumerate tutte le $2^n$ [[Combinatoria|Disposizioni]]
 - **[[Complessita|complessità spaziale]]**:  si mantiene entro $O(n)$ grazie all'adozione di un'esplorazione in profondità, che limita il numero di informazioni simultaneamente memorizzate.


>[!tip] 
>l approccio è formalmente **corretto** e applicabile a qualsiasi **scenario finito** ma non è ben scalabile



