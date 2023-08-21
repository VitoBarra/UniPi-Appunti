---
type: nota
course: Elementi di calcolabilita e complessita
topic: 
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Funzioni Ricorsive Primitive
---
la classe delle funzioni ricorsive primitive è un formalismo per esprimere un [[Nozione di Calcolabilità|Modello di calcolo]] ed è la minima classe di [[Funzioni]] $\mathcal{C}: \mathbb{N}^n \rightarrow \mathbb{N}$ con $n\geq 0$ in cui appartengono

$$
\begin{matrix}
I & Zero & \lambda x_1,\dots,x_k.0 & k\geq 0 \\
II & Successore & \lambda x.x+1 \\
III & Identita & \lambda x_1,\dots,x_k.x_i & 1\leq i\leq k \\
\end{matrix}
$$
dette anche schemi primitivi di base, e che è chiusa per:
$$

\begin{matrix}
IV & Composizione \\
V & \text{Ricorsione primitva}  \\
\end{matrix}
$$
![[Pasted image 20221014022815.png]]

--- 
in generale una [[Funzioni|funzione]] si può dire che appartenga alla classe delle funzioni ricorsive primitive se esiste una successione (o derivazione) finita della forma :
$$f_1,f_2,\dots,f_n$$
dove $f=f_n, \forall i| 1\leq i\leq n$ vale uno dei due casi seguenti:
- $f_i \in \mathcal{C}$ per $I-III$ 
	-  ovvero $f_i$ è definita secondo gli schemi di base
- $f_i$ è con le regole $IV-V$ da $f_j,j <i$ 
	- ovvero $f_i$ è definita da funzioni già definite in precedenza.

### Espressività
la calasse delle funzioni ricorsive primitive possono esprime solo un sotto insieme delle [[Funzioni]] e [[Nozione di Calcolabilità|calcolabili]] ed è espressivo esattamente come [[Linguaggi FOR e WHILE | Linguaggio FOR]]. un esempio di [[Funzioni]], calcolabili ma non esprimibile dalle funzioni ricorsive primitive  è [[Funzione di Ackermann]]



 ## Computazione
la computazione di questo formalismo si basa sulla [[Valutazione Redex]] _in questo formalismo è sempre vero che la regola esterna è più efficiente_$^\text{da verificare}$ in termini di passi e che le valutazioni di uno stessa espressione convergono ad0 un unico risultato a prescindere dalla regola di redex applicata, questo è dato dal espressività di questo formalismo che siccome son solo funzioni totali non capita mai che un redex mandi la valutazione in stato di non terminazione cosa che fosse altrimenti sarebbe potuta accadere con alcune regole