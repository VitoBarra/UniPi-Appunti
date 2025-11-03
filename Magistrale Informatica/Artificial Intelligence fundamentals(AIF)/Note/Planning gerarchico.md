---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning gerarchico
---
Il **planning gerarchico** è una strategia per il [[Planning|Planning]], esso si basa sulla **decomposizione gerarchia** ovvero si divide un piano in più attività ad alto livello. il formalismo usato per descrivere questi piani sono **hierarchical task networks** (**HTN**), l’agente opera attraverso due categorie fondamentali di azioni:
- **Azioni primitive**, dotate di **precondizioni** ed **effetti** direttamente applicabili all’ambiente 
- **azioni di alto livello** (HLA), che rappresentano **compiti astratti** e possono essere **raffinati** in sequenze di altre azioni, primitive o ulteriormente astratte.
Una **HLA** può avere più possibili **raffinamenti**, ciascuno dei quali descrive una modalità alternativa per raggiungere lo stesso **obiettivo operativo** sono dette
- **implementazioni**:  se sono composte solo da **azioni ground**
- **azioni di alto livello** (HLA) se contengono almeno un altra zione ad **alto livello** 
La concatenazione delle **implementazioni** di ogni **HLA** definisce un’**implementazione completa** del piano. Un piano di alto livello è considerato valido se almeno una delle sue **implementazioni complete** conduce allo **stato obiettivo** a partire dallo **stato iniziale**.

un esempio di raffinamento
$$
\begin{align*}
&\text{Refinement}\Big(\text{Go}(\text{Home}, \text{SFO}), \\
&\quad \text{STEPS: } \big[\text{Drive}(\text{Home}, \text{SFOLongTermParking}), \\
&\quad \quad \text{Shuttle}(\text{SFOLongTermParking}, \text{SFO})\big] \Big) \\
&\text{Refinement}\Big(\text{Go}(\text{Home}, \text{SFO}), \\
&\quad \text{STEPS: } \big[\text{Taxi}(\text{Home}, \text{SFO})\big] \Big) \\
\\
&\text{Refinement}\Big(\text{Navigate}([a, b], [x, y]), \\
&\quad \text{PRECOND: } a = x \wedge b = y \\
&\quad \text{STEPS: } \big[ \big] \Big) \\
&\text{Refinement}\Big(\text{Navigate}([a, b], [x, y]), \\
&\quad \text{PRECOND: } \text{Connected}([a, b], [a - 1, b]) \\
&\quad \text{STEPS: } \big[\text{Left}, \text{Navigate}([a - 1, b], [x, y])\big] \Big) \\
&\text{Refinement}\Big(\text{Navigate}([a, b], [x, y]), \\
&\quad \text{PRECOND: } \text{Connected}([a, b], [a + 1, b]) \\
&\quad \text{STEPS: } \big[\text{Right}, \text{Navigate}([a + 1, b], [x, y])\big] \Big)
\end{align*}
$$

Per costruire un **implementazione completa** c è possiamo usare il fatto che quando una **HLA** dispone di una sola implementazione, è possibile dedurre direttamente le sue **precondizioni** ed **effetti** a partire dalle azioni primitive, trattandola come un’**azione atomica**, Se invece esistono più implementazioni, la pianificazione può essere affrontata in due modi: 

Attraverso una **ricerca sui raffinamenti primitivi**, ovvero si fa una ricerca [[Ricerca in ampiezza (BF)|BF]] su tutte le possibili implementazioni e quindi discendendo quando un implementazione contiene un altra **HLA**. uno pseudo codice è il seguente:
```pseudo
\begin{algorithm}
\caption{Hierarchical Search}
\begin{algorithmic}
\Function{HIERARCHICAL-SEARCH}{problem, hierarchy}
    \State \textbf{returns} una soluzione o failure
    \State $frontier \gets$ una coda FIFO con $[Act]$ come unico elemento
    \While{true}
        \If{\Call{Is-Empty}{$frontier$}}
            \Return failure
        \EndIf
        \State $plan \gets$ \Call{Pop}{$frontier$} \Comment{sceglie il piano meno profondo nella frontier}
        \State $hla \gets$ la prima HLA in $plan$, o null se nessuna
        \State $prefix, suffix \gets$ le sottosequenze di azioni prima e dopo $hla$ in $plan$
        \State $outcome \gets$ \Call{RESULT}{$problem.INITIAL, prefix$}
        \If{$hla$ is null} \Comment{piano primitivo e outcome è il suo risultato}
            \If{\Call{problem.Is-Goal}{$outcome$}}
                \Return $plan$
            \EndIf
        \Else
            \ForAll{$sequence$ \textbf{in} \Call{Refinements}{$hla, outcome, hierarchy$}}
            \State \Call{add}{\Call{APPEND}{$prefix, sequence, suffix$} to $frontier$}
            \EndFor
        \EndIf
    \EndWhile
\EndFunction
\end{algorithmic}
\end{algorithm}
```

//------Extra to review------//

oppure mediante un **ragionamento astratto** basato sulle HLAs stesse. Quest’ultimo approccio consente di costruire piani corretti a un livello di astrazione alto, senza la necessità di espandere tutte le sequenze di dettaglio.



Dal punto di vista formale, si considera un modello di raffinamento regolare, in cui ogni azione non primitiva ha $r$ possibili raffinamenti, ciascuno composto da $k$ sotto-azioni al livello inferiore. Se la profondità totale del piano (in termini di azioni primitive) è $d$, il numero di nodi interni della gerarchia risulta $(d - 1)/(k - 1)$, e il numero totale di alberi di decomposizione possibili è $r^{(d-1)/(k-1)}$. Questa relazione mostra che mantenendo $r$ ridotto e $k$ elevato si ottiene una diminuzione del costo combinatorio rispetto ai metodi di [[Problem-Solving Agent|problem solving]] classici basati su ricerca esaustiva, come la [[Ricerca in ampiezza (BF)|ricerca in ampiezza]] o la [[Ricerca di costo uniforme o Dijkstra algorithm (UC)|ricerca di costo uniforme]].

La rappresentazione formale delle HLAs utilizza il concetto di **insieme raggiungibile**, indicato come $REACH(s, h)$, ossia l’insieme degli stati ottenibili a partire da uno stato $s$ mediante una qualunque implementazione di un’azione $h$. Per una sequenza di azioni $[h_1, h_2]$, si ha:
$$
REACH(s, [h_1, h_2]) = \bigcup_{s' \in REACH(s, h_1)} REACH(s', h_2)
$$
Un piano di alto livello raggiunge il suo obiettivo se l’intersezione tra il suo insieme raggiungibile e l’insieme degli stati obiettivo non è vuota. Questo criterio è coerente con la prospettiva degli [[Agenti Razionali|agenti razionali]], nei quali una sequenza di azioni è ritenuta valida se conduce a uno stato in cui la funzione di utilità è soddisfatta.

![[IMG - Planning gerarchico reachable set.png]]

Dal punto di vista semantico, la pianificazione gerarchica distingue tra **semantica demoniaca** e **semantica angelica**. Nella prima, la scelta dell’implementazione è affidata a un agente avversario, come nei contesti di [[Ricerca in ambienti competitivi|ricerca competitiva]]; nella seconda, detta angelica, la scelta è controllata dall’agente stesso, che può selezionare il percorso più favorevole. La semantica angelica consente di considerare un’azione astratta come una scelta deliberata tra più possibilità disponibili.

Gli effetti delle HLAs sono espressi tramite **liste di aggiunta e cancellazione** con l’uso del simbolo $\tilde{}$, che rappresenta possibilità controllate. Si ha così $\tilde{+}A$ per “possibilmente aggiungere $A$”, $\tilde{-}A$ per “possibilmente eliminare $A$” e $\tilde{\pm}A$ per “possibilmente aggiungere o eliminare $A$”. Questa rappresentazione consente di descrivere formalmente l’insieme delle conseguenze di un’azione astratta, coerente con il modello logico degli [[Agenti Knowledge Based|agenti basati sulla conoscenza]].

Poiché le HLAs possono avere infiniti raffinamenti e produrre insiemi raggiungibili complessi, si introducono **descrizioni approssimate**. Una descrizione **ottimistica**, indicata con $REACH^+(s, h)$, può sovrastimare l’insieme raggiungibile, mentre una descrizione **pessimistica**, $REACH^-(s, h)$, lo sottostima, con la relazione:
$$
REACH^-(s, h) \subseteq REACH(s, h) \subseteq REACH^+(s, h)
$$
Se l’intersezione dell’insieme ottimistico con l’obiettivo è vuota, il piano è considerato non valido; se invece l’insieme pessimistico interseca l’obiettivo, il piano è valido. Nei casi intermedi, la pianificazione procede raffinando il piano astratto fino a chiarire le azioni necessarie.

L’approccio angelico con descrizioni approssimate consente di ridurre lo spazio di ricerca rispetto ai metodi tradizionali, come le ricerche non informate o euristiche descritte in [[Algoritmi di ricerca informata|ricerca informata]]. Il processo di ricerca gerarchica si sviluppa come un perfezionamento progressivo dei piani astratti: una volta individuato un piano la cui descrizione ottimistica interseca lo stato obiettivo, l’agente può decomporlo in sottoproblemi, ciascuno con stato iniziale e obiettivo derivati per regressione. Questo meccanismo è simile a quello dei [[Planning Agent|pianificatori multilivello]].

Gli algoritmi principali che incarnano queste strategie di ricerca gerarchica e angelica sono i seguenti:

```pseudo

\begin{algorithm}
\caption{Angelic Search}
\begin{algorithmic}
\Function{ANGELIC-SEARCH}{problem, hierarchy, initialPlan}
    \State \textbf{returns} a solution or fail
    \State $frontier \gets$ a FIFO queue with $initialPlan$ as the only element
    \While{true}
        \If{\Call{Is-Empty?}{$frontier$}}
            \Return fail
        \EndIf
        \State $plan \gets$ \Call{Pop}{$frontier$} \Comment{chooses the shallowest node in frontier}
        \If{\Call{Reach^+}{$problem.Initial, plan$} intersects $problem.Goal$}
            \If{$plan$ is primitive}
                \Return $plan$ \Comment{Reach$^+$ is exact for primitive plans}
            \EndIf
            \State $guaranteed \gets$ \Call{Reach^-}{$problem.Initial, plan$} $\cap$ $problem.Goal$
            \If{$guaranteed \neq \{\}$ and \Call{Making-Progress}{$plan, initialPlan$}}
                \State $finalState \gets$ any element of $guaranteed$
                \Return \Call{Decompose}{$hierarchy, problem.Initial, plan, finalState$}
            \EndIf
        \EndIf
        \State $hla \gets$ some HLA in $plan$
        \State $prefix, suffix \gets$ the action subsequences before e dopo $hla$ in $plan$
        \State $outcome \gets$ \Call{Result}{$problem.Initial, prefix$}
        \For{each $sequence$ in \Call{Refinements}{$hla, outcome, hierarchy$}}
            \State \Call{Add}{\Call{Append}{$prefix, sequence, suffix$} to $frontier$}
        \EndFor
    \EndWhile
\EndFunction

\Function{DECOMPOSE}{hierarchy, $s_0$, plan, $s_f$}
    \State \textbf{returns} a solution
    \State $solution \gets$ an empty plan
    \While{$plan$ is not empty}
        \State $action \gets$ \Call{Remove-Last}{$plan$}
        \State $s_i \gets$ a state in \Call{Reach^-}{$s_0$, $plan$} such that $s_f \in$ \Call{Reach^-}{$s_i$, $action$}
        \State $problem \gets$ un problema con $Initial = s_i$ e $Goal = s_f$
        \State $solution \gets$ \Call{Append}{\Call{Angelic-Search}{$problem, hierarchy, action$}, $solution$}
        \State $s_f \gets s_i$
    \EndWhile
    \Return $solution$
\EndFunction
\end{algorithmic}
\end{algorithm}
```
