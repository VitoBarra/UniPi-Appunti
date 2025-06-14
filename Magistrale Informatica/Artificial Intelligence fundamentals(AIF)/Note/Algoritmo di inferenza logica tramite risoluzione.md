---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Algoritmo di inferenza logica tramite risoluzione
---
si definisce un algoritmo per fare [[Inferenza logica per dimostrazione di teoremi|dimostrazione di teoremi]] Il procedimento di risoluzione in logica proposizionale si basa sul principio della dimostrazione per contraddizione. 
Si usa il [[Inferenza logica per dimostrazione di teoremi|teorema di refutazoine]] e quindi per stabilire che $KB \models \alpha$, si assume la  $\lnot\alpha=true$ e si dimostra che $KB \land \neg \alpha$ è **insoddisfacibile**, ovvero questa assunzione porta.

Questo approccio richiede innanzitutto la conversione della formula combinata $(KB \land \neg \alpha)$ nella [[forma normale congiuntiva (CNF)|forma normale congiuntiva (CNF)]]

Il meccanismo di risoluzione agisce selezionando coppie di clausole che contengono letterali complementari, cioè letterali nella forma $P$ e $\neg P$. La loro combinazione tramite la [[Inferenza logica per dimostrazione di teoremi|regola di risoluzione]] produce una nuova clausola, che viene aggiunta all'insieme delle clausole se non è già presente. Questo processo si ripete fino a che:
- non si generano più nuove clausole, condizione che implica che $KB \nvDash \alpha$, oppure
- si ottiene la clausola vuota, rappresentata come $\{\}$, equivalente a $False$, il che implica che $KB \models \alpha$.

La clausola vuota corrisponde a una disgiunzione priva di letterali. Poiché una disgiunzione è vera se almeno uno dei letterali è vero, una disgiunzione vuota è necessariamente falsa. Questa clausola emerge esclusivamente dalla risoluzione di due clausole unitarie contraddittorie, come $P$ e $\neg P$.

lo pseudo codice del algoritmo è il seguente:
```pseudo
\begin{algorithm}
\caption{PL-RESOLUTION}
\begin{algorithmic}
\REQUIRE $KB$: base di conoscenza in logica proposizionale \\
\REQUIRE $\alpha$: query, una formula in logica proposizionale
\ENSURE \texttt{true} se $KB \models \alpha$, \texttt{false} altrimenti

\Function{PL-RESOLUTION}{$KB, \alpha$}

\STATE $clauses \leftarrow$ insieme di clausole nella forma CNF di $KB \land \neg \alpha$
\STATE $new \leftarrow \{\}$

\WHILE{true}
    \FORALL{coppie di clausole $C_i, C_j$ in $clauses$}
        \STATE $resolvents \leftarrow \text{PL-RESOLVE}(C_i, C_j)$
        \IF{$resolvents$ contiene la clausola vuota}
            \RETURN \texttt{true}
        \ENDIF
        \STATE $new \leftarrow new \cup resolvents$
    \ENDFOR
    \IF{$new \subseteq clauses$}
        \RETURN \texttt{false}
    \ENDIF
    \STATE $clauses \leftarrow clauses \cup new$
\ENDWHILE
\EndFunction

\end{algorithmic}
\end{algorithm}
```
Durante l'applicazione della **procedura di risoluzione** è possibile che vengano generate clausole inutili dove sono presenti casi del tipo $P \lor \neg P$ che è **tautologia** e possono essere eliminate senza compromettere il processo inferenziale.



La **completezza** della risoluzione viene formalizzata nel **teorema di completezza per la logica proposizionale**, noto come **teorema ground resolution**. 

definendo $RC(S)$ come **chiusura per risoluzione** questa rappresenta l'insieme di tutte le **clausole derivabili** da $S$ tramite applicazioni ripetute della **[[Inferenza logica per dimostrazione di teoremi|regola di risoluzione]]**

Tale teorema afferma che 
**se** un insieme di clausole $S$ è **[[Logica|insoddisfacibile]]**
**allora** la chiusura per risoluzione $RC(S)$ di quell'insieme conterrà la clausola vuota.

Essendo $RC(S)$ finito, grazie al passo di fattorizzazione che evita la creazione ridondante di clausole con gli stessi simboli proposizionali $P_1, \dots, P_k$, il procedimento termina sempre.

Il teorema si dimostra considerando il suo contronominale: se $RC(S)$ non contiene la clausola vuota, allora $S$ è soddisfacibile

La dimostrazione prevede la costruzione esplicita di un modello, assegnando valori di verità ai simboli proposizionali secondo il seguente schema:
- Per ogni simbolo $P_i$, si assegna $False$ se esiste una clausola in $RC(S)$ che contiene $\neg P_i$ e i cui altri letterali sono tutti $True$ rispetto alle assegnazioni già fatte per $P_1, \dots, P_{i-1}$.
- In caso contrario, si assegna $True$ a $P_i$.
Questo procedimento assicura che ogni clausola in $RC(S)$ sia soddisfatta. Infatti Supponendo per assurdo che, al passo $i$, l'assegnazione a $P_i$ renda falsa una clausola $C$, si deduce che tutti gli altri letterali di $C$ risultano già falsi per le assegnazioni precedenti. La clausola $C$ assume quindi la forma $(False \lor \dots \lor False \lor P_i)$ oppure $(False \lor \dots \lor False \lor \neg P_i)$. Il metodo costruttivo assegna proprio il valore necessario a $P_i$ affinché $C$ risulti vera, evitando che la clausola venga falsificata. Se entrambi i casi sono presenti in $RC(S)$, il loro risolvente, contenuto anch'esso in $RC(S)$ per chiusura, risulterebbe interamente falsificato dalle precedenti assegnazioni, contraddicendo l'ipotesi che $C$ sia la prima clausola falsificata. Pertanto, il modello costruito soddisfa $RC(S)$, e, dato che $S \subseteq RC(S)$, soddisfa anche $S$.








