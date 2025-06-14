---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza logica - Forward chaining con FOL
---
L’algoritmo di inferenza **Forward Chaining (FOL-FC-ASK)** applicato alla [[Logica del primo ordine (FOL)|logica del primo ordine]] costituisce un [[Sistema di inferenza per FOL|istema dettutivio]] sulla regola del **[[Inferenza logica - Regola Modus Ponens generalizata per FOL|Modus Ponens generalizzato]]**, volto a derivare nuove informazioni a partire da una base di conoscenza $KB$ di [[Forma a clausole definite per FOL|insieme di clausole definite]] e di **fatti noti**. 

si vuole decidere se $KB \models \alpha$ ovvero se la **frase atomica** $\alpha$ è [[Conseguenza Logica (Deduzione)|conseguenza logica]] di $KB$. per fare ciò l'[[Algoritmi|algoritmo]] applica le regole per cui le premesse sono soddisfatte dai fatti presenti in $KB$, fino a generare $\alpha$ o fino al raggiungimento di un **punto fisso**, in cui nessun **nuovo** fatto può essere aggiunto. Quando una conclusione risulta una **rinomina** di una variabile, ad esempio $\text{Likes}(x, IceCream)$ e $\text{Likes}(y, IceCream)$,  essa non viene considerata nuova, poiché rappresenta la stessa informazione.

lo pseudo codice del algoritmo è il seguente:
```pseudo
\begin{algorithm}
\caption{FOL-FC-ASK}
\begin{algorithmic}
\Require $KB \text{: Base di conoscenza: insieme di clausole definite di primo ordine}$
\Require $\alpha \text{: Query atomica}$
\Ensure Una sostituzione oppure \textbf{false}

\Function{FOL-FC-ASK}{$KB,\alpha$}
	\While{true}
	    \State $new \gets \{\}$ \Comment{Nuove frasi inferite nell’iterazione corrente}
	    \ForAll{rule in $KB$}
	        \State $(p_1 \land \dots \land p_n \Rightarrow q) \gets \text{STANDARDIZE-VARIABLES(rule)}$
	        \ForAll{$\theta$ tali che $\text{SUBST}(\theta, p_1 \land \dots \land p_n)$ unifichi con fatti in $KB$}
	            \State $q' \gets \text{SUBST}(\theta, q)$
	            \If{$q'$ non unifica con alcuna frase già in $KB$ o in $new$}
	                \State $new.ADD(q')$
	                \State $\phi \gets \text{UNIFY}(q', \alpha)$
	                \If{$\phi$ non è failure}
	                    \return $\phi$
	                \EndIf
	            \EndIf
	        \EndFor
	    \EndFor
	    \If{$new = \{\}$}
	        \return \textbf{false}
	    \EndIf
	    \State aggiungi $new$ a $KB$
	\EndWhile
\EndFunction
\end{algorithmic}
\end{algorithm}
```
l’algoritmo risulta **corretto (sound)**, poiché ogni inferenza deriva da applicazioni valide del [[Inferenza logica - Regola Modus Ponens generalizata per FOL|Modus Ponens generalizzato]] che a sua volta è una regola **corretta (sound)**.

l’algoritmo risulta **completo** per $KB$ fatto da [[Forma a clausole definite per FOL|clausole definite]].
Nel caso dei sistemi privi di simboli di funzione, la completezza è garantita dalla finitezza delle istanze possibili: se $p$ indica il numero di predicati, $n$ il numero di costanti e $k$ la massima arità dei predicati, il numero di fatti distinti possibili è limitato a $p n^k$, assicurando così la convergenza a un punto fisso dopo un numero finito di iterazioni. Quando invece sono presenti simboli di funzione, la procedura può generare un numero infinito di nuovi termini, rendendo il processo **[[Calcolabilità|semidecidibile]]**: se la query è **vera**, verrà eventualmente trovata una prova; in caso contrario, l’algoritmo potrebbe non terminare. La dimostrazione della correttezza in questi casi si basa sul [[Teorema di Herbrand|teorema di Herbrand]].

#### Efficentazione
L’efficienza del **forward chaining** dipende dalla gestione del **matching** tra **premesse** e **fatti noti**. Tale operazione consiste nel trovare tutte le sostituzioni $\theta$ che rendono vera la premessa di una regola rispetto ai fatti contenuti nella $KB$, ovvero nel determinare un **[[FOL - Algoritmo di unificazione|unificatore]]**.  La complessità di questa operazione è influenzata dal cosiddetto ***conjunct ordering problem***, ossia la scelta dell’ordine con cui eseguire le **unificazioni** tra i congiunti presenti nella premessa di una regola del tipo $$p_1 \land p_2 \land \dots \land p_n \Rightarrow q.$$Poiché ogni congiunto $p_i$ agisce come un filtro che restringe le possibili sostituzioni per le variabili, un ordinamento inefficiente può portare a verificare un gran numero di combinazioni inutili, ad esempio controllando per prime sostituzioni che sarebbero poi escluse da altri congiunti. Viceversa, valutare prima i congiunti più restrittivi riduce drasticamente lo spazio di ricerca e il costo computazionale complessivo. Determinare l’ordine ottimale è tuttavia un problema [[Calcolabilità|NP-hard]], motivo per cui si adottano **euristiche** ispirate ai [[Problemi di soddisfacibilita vincolata (CSP)|CSP]], come la **Minimum Remaining Values (MRV)**, che suggerisce di esaminare per primi i congiunti con il minor numero di istanze compatibili.

decidere se un set di **premesse** puo essere soddisfatto dalla $KB$  puo essere ridotto ad un problema di [[Problemi di soddisfacibilita vincolata (CSP)|soddisfacimento di vincoli (CSP)]] in cui ogni **congiunto** nella premessa di una regola può essere interpretato come un vincolo sul dominio delle variabili.
 - **Predicato unario** rappresenta un vincolo su una singola variabile, 
 - **Predicato ternario**: impone relazioni congiunte su più variabili.
la soluzione corrisponde alla **combinazione di valori** che rendono simultaneamente vere tutte le premesse della regola ovvero veri tutti i vincoli.

al contrario si puo [[Riducibilita dei problemi|ridurre]] un CSP al matching di una [[Forma a clausole definite per FOL|clausola definita]] dove tutti i vincoli sono le premesse della clausola e la soddisfacibilità è il conseguente. 

Per mitigare l’inefficienza dovuta alla ripetizione dei controlli, si adotta una versione **incrementale** del **forward chaining**, in cui vengono rivalutate solo le regole che coinvolgono **fatti appena generati**. L’idea è che ogni nuova inferenza al tempo $t$ deve necessariamente derivare da **almeno un fatto introdotto all’iterazione precedente ($t-1$)**: infatti, se una regola potesse essere applicata senza l’uso di nuovi fatti, essa sarebbe già stata attivata nell’iterazione precedente. Sfruttando questa osservazione, l’algoritmo incrementale limita il **matching** alle sole regole che contengono almeno un congiunto $p_i$ unificabile con un fatto $p'_i$ appena inferito al passo $t-1$. Durante il controllo, tale congiunto viene fissato per unificarsi con $p'_i$, mentre gli altri congiunti della regola possono continuare a essere confrontati con fatti derivati in qualsiasi iterazione precedente.  Questo algoritmo genera esattamente le stesse conclusioni che genera il forward Chaining normale ma è più efficiente.

Un ulteriore miglioramento è introdotto dal **Rete algorithm**, che memorizza e aggiorna i match parziali tra premesse e fatti mediante una rete di nodi collegati da vincoli di uguaglianza, riducendo la necessità di ripetere calcoli già eseguiti. Tale approccio è alla base dei **sistemi di produzione**, architetture in cui le regole vengono attivate dinamicamente in risposta all’aggiunta di nuovi fatti nella memoria di lavoro.

Infine, per evitare inferenze irrilevanti rispetto alla query, è possibile vincolare il processo mediante tecniche di **magic set**, riscrivendo le regole in modo da limitare la generazione di nuove istanze solo ai valori di variabili pertinenti all’obiettivo, ottenendo così un comportamento più mirato e ottimizzato dell’inferenza in avanti.