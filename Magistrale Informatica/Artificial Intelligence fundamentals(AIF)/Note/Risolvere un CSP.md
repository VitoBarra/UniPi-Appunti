---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Risolvere un CSP
---
Per la risoluzione dei **[[Problemi di soddisfacibilita vincolata (CSP)|Constraint Satisfaction Problems(CSP)]]** si utilizza il principio della **propagazione dei vincoli**, tecnica che sfrutta i vincoli definiti dal problema per ridurre i **domini delle variabili**. La riduzione di un dominio può propagarsi, inducendo ulteriori riduzioni nei domini di altre variabili collegate da vincoli, semplificando la ricerca o, in alcuni casi, portando direttamente alla soluzione. Tale approccio può essere impiegato sia in fase di ricerca sia come operazione preliminare di **preprocessing**.

La propagazione dei vincoli si fonda sul concetto di **consistenza locale**. Rappresentando il CSP come un [[Grafi|grafo]], in cui i nodi corrispondono alle **variabili** e gli archi ai **vincoli binari**, si procede progressivamente all'eliminazione dei valori incompatibili dai domini, seguendo diversi livelli di **consistenza locale**.

i livelli di consistenza sono: 
- **consistenza del nodo** (**node consistency**): Una variabile è detta **nodo-consistente** se tutti i valori del suo dominio rispettano i vincoli unari associati. 
- **consistenza del arco**: (**arc consistency**):  una variabile $X_i$ è detta **arco-consistente** rispetto a una variabile $X_j$ se, per ogni valore $v_i$ appartenente al dominio $D_i$, esiste almeno un valore $v_j$ nel dominio $D_j$ tale che la coppia $(v_i, v_j)$ soddisfi il vincolo binario tra $X_i$ e $X_j$. Formalmente riassumibile come $$\forall v_i \in D_i, \exists v_j \in D_j : (v_i, v_j) \in C_{ij}$$ per ridurre i domini in modo che siano **arco consistenti** si spesso usa L'[[Algoritmi|algoritmo]] **[[Algoritmo per consistenza archi AC-3|AC-3]]**
- **consistenza di percorso** (**path consistency**):  un [[Insiemi Matematici|insieme]] di due **variabili** $\{X_i, X_j\}$ sono dette **path-consistent** rispetto a una terza variabile $X_m$ se, per ogni assegnamento $\{X_i = a, X_j = b\}$ che soddisfa i vincoli binari, se presenti, tra $X_i$ e $X_j$, esiste almeno un valore per $X_m$ tale che siano soddisfatti i vincoli sia tra $\{X_i, X_m\}$ che tra $\{X_m, X_j\}$.formalmente la relazione si riassume come:$$
\begin{array}{}

\forall \, a \in D_i, \, \forall \, b \in D_j \mid (a, b) \in C_{ij}  \\
\implies \exists \, c \in D_m \, : \, (a, c) \in C_{im} \land (c, b) \in C_{mj}
\end{array}
$$il nome viene dal fatto che i domini sono consistenti sul percorso che collega $X_i,X_j$ e passa per $X_m$ Ci sono casi in cui i vincoli 
- **$k$-Consistenza** (**$k$-consistency**): la **$k$-consistenza** è la definizione di consistenza più generale. Un insieme di $k$ variabili $\{X_i,\dots ,X_k\}$  è detto $k$-consistente se, per ogni sottoinsieme di $k - 1$ variabili esiste un **assegnamento consistente** ed esiste un valore per la $k$-esima variabile che mantiene la **consistenza** rispetto a tutti i vincoli coinvolti. **la consistenza di nodo** corrisponde al $k=1$, **la consistenza di arco** corrisponde al caso $k = 2$, **la consistenza di percorso** se si hanno solo vincoli binari, corrisponde al caso $k = 3$. 
- **strong $k$-consistency** è una condizione più  forte della $k$-consistenza in quanto implica la $j$-consistenza  $\forall j \leq k$. 

con $n$ il numero di variabili e con $d$ il numero di valori consistenti per ogni variabile, la $k=n$-consistenza permette di cercare un **assegnamento soluzione** in $O(n^2d)$ che è molto meno di esponenziale nel numero di variabili $n$. Trovare questo tipo di consistenza in se pero ha [[Complessita|complessità]] esponenziale in $n$ sia in tempo che in spazio.


Per alcuni tipi di __vincoli globali__ si possono costruire algoritmi ad hoc per garantire la consistenza. Questi algoritmi sono spesso più efficienti rispetto alla trasformazione del vincolo in un insieme equivalente di vincoli binari.

**Alldiff** $alldiff(X_1,\dots, X_i)$: impone che tutte le variabili coinvolte assumano valori distinti. per questo vincolo vale che se $m$ variabili sono coinvolte e i loro domini contengono in totale $n$ valori distinti **allora**  **se** $m > n$, il vincolo non può essere soddisfatto $\Rightarrow$ **inconsistenza**.
da questo l algoritmo segue:
1. Eliminare le variabili con dominio singoletone e rimuovere il valore singoletto dai domini delle altre variabili.
2. Ripetere fino a esaurimento dei singoletoni.
3. Se ad un qualsiasi step un dominio si svuota o $m > n$ allora il vincolo non puo essere sodisfatto $\Rightarrow$ inconsistenza.



**Vincoli di risorse** o **Atmost** $Atmost(n, X_1, \dots, X_i)$: impone che la somma complessiva non superi $n$ unità.
Controllo di consistenza: Se la somma dei minimi dei domini $> n$ $\Rightarrow$ inconsistenza. se non è questo i caso si possono rendere i domini consistenti eliminano dai domini i valori massimi incompatibili con il vincolo, ovveroquelli  $>n$

Nei problemi di grandi dimensioni (es. logistici) si usano rappresentazioni con estremi, in questo caso si fa:
Si applica la __bounds propagation__:
- I domini sono intervalli $[min, max]$.
- Si aggiornano i limiti inferiori e superiori in base ai vincoli.
Un CSP è __bounds-consistent__ se per ogni variabile $X$, esistono valori minimi e massimi nel dominio tali che: È possibile estendere l’assegnazione in modo consistente rispetto ai vincoli tra $X$ e ogni altra variabile $Y$.




