---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
Area: "[[Ottimizzazione matematica]]"
topic: 
SubTopic: 
---

# Problemi di ottimizzazione vincolata (COP)
---
I **problemi di ottimizzazione vincolata** costituiscono una classe fondamentale nell’ambito dell’ottimizzazione matematica, in cui l’obiettivo consiste nel determinare il minimo o il massimo di una funzione reale soggetta a una **collezione di vincoli** che restringono l’insieme delle soluzioni ammissibili. A differenza del caso non vincolato, in cui la funzione obiettivo è definita sull’intero spazio $\mathbb{R}^n$, qui si cerca una soluzione all’interno di una regione ammissibile definita in modo esplicito.

La forma generale di un problema di ottimizzazione vincolata si esprime come:

$$
\min_{x \in \mathbb{R}^n} f(x)
$$

soggetto a:

$$
\begin{cases}
g_i(x) \leq 0 & \text{per } i = 1, \dots, m \\
h_j(x) = 0 & \text{per } j = 1, \dots, p
\end{cases}
$$

dove $f : \mathbb{R}^n \to \mathbb{R}$ è la funzione obiettivo da minimizzare, $g_i : \mathbb{R}^n \to \mathbb{R}$ rappresentano i vincoli di disuguaglianza e $h_j : \mathbb{R}^n \to \mathbb{R}$ i vincoli di uguaglianza. L’insieme ammissibile è dato da:

$$
\mathcal{F} = \left\{ x \in \mathbb{R}^n \mid g_i(x) \leq 0, \, h_j(x) = 0 \right\}
$$

Un punto $x^\ast \in \mathcal{F}$ è detto **soluzione ottima locale** se esiste un intorno $U$ di $x^\ast$ tale che $f(x^\ast) \leq f(x)$ per ogni $x \in U \cap \mathcal{F}$. Se la disuguaglianza vale per tutti gli $x \in \mathcal{F}$, allora $x^\ast$ è **ottimo globale**.

L’analisi di questi problemi richiede condizioni di ottimalità più articolate rispetto al caso non vincolato. Quando le funzioni sono differenziabili e i vincoli soddisfano certe ipotesi regolari, si applicano le **condizioni di Karush-Kuhn-Tucker (KKT)**. Esse forniscono criteri necessari per l’ottimalità di un punto $x^\ast$ e introducono i moltiplicatori lagrangiani $\lambda_j$ e $\mu_i$ tali che:

$$
\nabla f(x^\ast) + \sum_{i=1}^m \mu_i \nabla g_i(x^\ast) + \sum_{j=1}^p \lambda_j \nabla h_j(x^\ast) = 0
$$

accompagnati dalle condizioni:

$$
\begin{cases}
g_i(x^\ast) \leq 0 \\
h_j(x^\ast) = 0 \\
\mu_i \geq 0 \\
\mu_i \cdot g_i(x^\ast) = 0
\end{cases}
$$

Le ultime due relazioni costituiscono le **condizioni di complementarità**, che impongono che ogni vincolo di disuguaglianza attivo (cioè tale che $g_i(x^\ast) = 0$) abbia un moltiplicatore non nullo, mentre quelli inattivi ($g_i(x^\ast) < 0$) abbiano $\mu_i = 0$.

Il caso particolare in cui sono presenti solo vincoli di uguaglianza è trattato mediante il **metodo dei moltiplicatori di Lagrange**, in cui si considera la lagrangiana:

$$
\mathcal{L}(x, \lambda) = f(x) + \sum_{j=1}^p \lambda_j h_j(x)
$$

e si studiano i punti stazionari della funzione $\mathcal{L}$ rispetto a tutte le variabili.

Dal punto di vista geometrico, la soluzione ottima corrisponde a un punto della regione ammissibile in cui il gradiente della funzione obiettivo è combinazione lineare dei gradienti dei vincoli attivi. Questo principio guida l’analisi locale e consente la formulazione di algoritmi iterativi, come i metodi basati sulla penalizzazione, le barriere interne o gli approcci sequenziali (SQP).

I problemi vincolati possono essere anche di natura intera o combinatoria, oppure dinamici, con vincoli espressi in termini di evoluzione temporale. In ciascun caso, la struttura del problema influisce sulla scelta degli strumenti teorici e computazionali adottabili, rendendo l’ottimizzazione vincolata un campo estremamente ampio e articolato all’interno della matematica applicata.




altri tipi di problemi di ottimizazione sono:

__[[Programmazione lineare|programmazione lineare]]__: __funzione obiettivo__ e __vincoli__ sono [[Applicazioni Lineari|funzione lineare]]

__Non lineari__: __funzione obiettivo__ o __vincoli__ sono [[Funzioni|funzione NON lineari]]. 
In generale, tali problemi possono essere più complessi da risolvere e richiedere tecniche avanzate come:
- **Programmazione quadratica** (se la funzione obiettivo è quadratica e i vincoli sono lineari)
- **Ottimizzazione convessa** (se la funzione obiettivo e i vincoli soddisfano condizioni di [[Convessita|convessità]])



