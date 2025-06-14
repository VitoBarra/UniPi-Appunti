---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Teoria dei giochi - Giochi cooperativi
---
La **[[Teoria dei giochi (Game theory)|teoria dei giochi]] cooperativi** analizza scenari decisionali in cui gli [[Agenti Razionali|agenti]] possono **stipulare accordi vincolanti** e **cooperare** per ottenere un valore collettivo superiore rispetto a quello **conseguibile individualmente**. 
Formalmente, un gioco cooperativo con utilità trasferibile (**TU-game**) in forma di **funzione caratteristica** è definito come $G = (N, \nu)$, dove $N = \{1, \dots, n\}$ è l’insieme dei giocatori e $\nu$ è la **funzione caratteristica** che assegna a ciascuna una **coalizione**, ovvero un sottoinsieme non vuoto di giocatori $C \subseteq N$, il valore $\nu(C)$ ottenibile dalla cooperazione dei membri di $C$. Si assume che $\nu(\emptyset) = 0$ e che $\nu(C) \ge 0$ e In alcuni casi si impone anche $\nu(\{i\}) = 0$, indicando che i singoli giocatori non generano valore autonomamente.

l’**insieme di tutte le coalizioni** di $N$ è il **[[Insiemi - Power Set|power set]]**  di $N$ la coalizione di tutti i membri è chiamata  ***grand coalition***.
Una ***struttura di coalizione*** è una **[[Partizione di un insieme|partizione]]** di $N$ in coalizioni disgiunte $\{C_1, \dots, C_k\}$ tali che $C_i \cap C_j = \emptyset$

L’esito di un **gioco cooperativo** è definito da una coppia $(CS, x)$, dove $CS$ è la struttura di coalizione e $x = (x_1, \dots, x_n)$ è il vettore dei **payoff individuali**, con la condizione che ciascuna coalizione $C \in CS$ ripartisca l’intero valore $\nu(C)$ tra i propri membri, cioè $\forall C \in CS . \sum_{i \in C} x_i = \nu(C)$. 
Ad esempio, dato il gioco $(\{1,2,3\}, \nu)$ con $\nu(\{1\}) = 4$ e $\nu(\{2,3\}) = 10$, un possibile esito è $(\{\{1\},\{2,3\}\}, (4,5,5))$.

Un gioco è detto ***superadditivo*** se l unione di due **coalizioni** non fa peggio di se le coalizioni fossero state separate. ovvero vale che $\nu(C \cup D) \ge \nu(C) + \nu(D)$ per ogni $C, D \subseteq N$. In tal caso, la **grande coalizione** $N$ possiede un valore almeno pari a quello ottenibile da **coalizioni separate**. Tuttavia, la **superadditività** non garantisce che la grande coalizione si formi effettivamente


l' ***imputazione*** in un gioco cooperativo $G(N,\nu)$ è un vettore $x$ che soddisfa le due condizioni:
1. $\sum_{i \in N} x_i = \nu(N)$ (**efficienza collettiva**): la somma di tutti i valori generati da tutti i player è uguale al valore della **grand coalition**, che viene quindi distribuita ai player
2. $x_i \ge \nu(\{i\})$ per ogni $i \in N$ (**razionalità individuale**). ogni player deve fare meglio nella coalizione do come avrebbe se fosse statoda solo.

Dato un’**imputazione** $x$, si definisce $x(C) = \sum_{i \in C} x_i$ come il totale ricevuto dalla coalizione $C$.
Il ***nucleo* (core)** del gioco è l’**[[Insiemi Matematici|insieme]] delle imputazioni** tali che $x(C) \ge \nu(C)$ per ogni coalizione $C \subset N$. Un’**imputazione esterna** al **nucleo** implica che esiste almeno una coalizione che **preferirebbe separarsi** dalla **grand coalition** perché potrebbe ottenere un **valore maggiore**. 
Il **nucleo**, quindi, rappresenta l’insieme delle allocazioni stabili da cui nessuna coalizione ha incentivo a deviare. Se il nucleo è vuoto, la grande coalizione non può formarsi stabilmente.

Dalla definizione di **nucleo** emergono le seguenti disequazioni per permettere di calcolarlo:

$$
\begin{array}{rcl}
x_i & \geq & v(\{i\}) \quad \forall i \in N \\
\sum_{i \in N} x_i & = & v(N) \\
\sum_{i \in C} x_i & \geq & v(C) \quad \forall C \subseteq N
\end{array}
$$

Qualsiasi soluzione a questo sistema darà un'**imputazione** nel **core**.  
Possiamo formulare queste disequazioni come un **[[Programmazione lineare|programma lineare]]** usando una funzione obiettivo fittizia (ad esempio massimizzando $\sum_{i \in N} x_i$), permettendo di calcolare le imputazioni in tempo polinomiale rispetto al numero di disequazioni.  La difficoltà sta nel fatto che questo genera un numero esponenziale di disequazioni (una per ciascuna delle $2^n$ possibili coalizioni). Di conseguenza, questo approccio fornisce un algoritmo per verificare la non-vuotezza del core che funziona in tempo esponenziale.  
Se sia possibile fare meglio dipende dal gioco studiato: per molte classi di giochi cooperativi, il problema di verificare la non-vuotezza del core è **[[Classi di complessita- co-NP-completo|co-NP-completo]]**.


Il nucleo fornisce condizioni di **stabilità** per la **grand coalition** ma non di **equità**. Ad esempio, per $N = \{1,2\}$ con $\nu(\{1\}) = \nu(\{2\}) = 5$ e $\nu(\{1,2\}) = 20$, l’imputazione $(6,14)$ appartiene al nucleo, ma appare iniqua poiché il giocatore 2 ottiene la quasi totalità del surplus cooperativo. 
Per affrontare il problema dell’equità si utilizza il ***valore di Shapley*** che assegna a ciascun giocatore $i$ una quota del valore $\nu(N)$ proporzionale al **contributo marginale** $mc_i(C) = \nu(C \cup \{i\}) - \nu(C)$ che egli fornisce alle **coalizioni** . Poiché l’ordine di ingresso dei giocatori influenza il **contributo**, Shapley calcola la media su tutte le possibili permutazioni $p \in P$ dell’insieme $N$. Indichiamo con $p_i$ l’insieme dei giocatori che precedono $i$ in una permutazione $p$. Allora il valore di Shapley è definito da:
$$
\phi_i(G) = \frac{1}{n!} \sum_{p \in P} mc_i(p_i).
$$
Il vettore $\phi(G) = (\phi_1, \dots, \phi_n)$ costituisce un’**imputazione** che rispetta quattro assiomi di equità:
- **Efficienza:** $\sum_i \phi_i(G) = \nu(N)$.
- **Giocatore nullo:** se $i$ non contribuisce mai ($mc_i(C)=0$ per ogni $C$), allora $\phi_i(G) = 0$
- **Simmetria:** se due giocatori hanno contributi identici, ricevono la stessa quota.
- **Additività:** per giochi $G$ e $G'$, vale $\phi_i(G+G') = \phi_i(G) + \phi_i(G')$.
Il **valore di Shapley** è l’unica allocazione che soddisfa simultaneamente questi assiomi, e per questo rappresenta una soluzione equa e stabile per la distribuzione dei benefici cooperativi.




#### (extra)
Dal punto di vista computazionale, rappresentare esplicitamente la funzione caratteristica $\nu$ è impraticabile, poiché richiede la valutazione di $2^n$ coalizioni. Per superare questa limitazione si usano rappresentazioni compatte, come le *marginal contribution nets* (MC-nets), che esprimono $\nu$ come insieme di regole $(C_i, x_i)$, ciascuna associando un valore $x_i$ a una coalizione $C_i$. Il valore di una coalizione $C$ è la somma dei $x_i$ per tutte le regole i cui antecedenti $C_i$ sono contenuti in $C$, cioè $\nu(C) = \sum_{(C_i,x_i) \in R, C_i \subseteq C} x_i$. Per esempio, con le regole $\{({1,2},5), ({2},2), ({3},4)\}$ si ottiene $\nu({1,2,3}) = 11$. In questo schema, il valore di Shapley può essere calcolato in tempo polinomiale come $\phi_i(R) = \sum_{(C,x) \in R} \frac{x}{|C|}$ se $i \in C$, altrimenti $0$.

Infine, un problema centrale nella teoria cooperativa è la ricerca della *struttura di coalizione socialmente ottima*, ossia quella che massimizza il benessere collettivo definito come $sw(CS) = \sum_{C \in CS} \nu(C)$. La struttura ottima $CS^*$ massimizza tale somma, ma la ricerca esaustiva è computazionalmente intrattabile, poiché il numero di strutture cresce esponenzialmente con $|N|$. Questo problema, noto come *set partitioning problem*, è NP-hard. Approcci algoritmici cercano soluzioni approssimate esplorando solo sottoinsiemi del grafo delle strutture di coalizione: ad esempio, limitandosi ai primi due livelli (coalizioni singole e coppie), si ottiene una soluzione con valore almeno $\frac{1}{n}$ di quello ottimo. Tale approssimazione, pur non garantendo l’ottimalità, risulta spesso soddisfacente in applicazioni pratiche.
