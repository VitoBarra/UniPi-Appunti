---
Course: "[[Ricerca Operativa (RO)]]"
tags: 
Area: 
topic: 
SubTopic:
---

# Ottimizzazione matematica
---
L'ottimizzazione matematica rappresenta una delle aree fondamentali dell'analisi applicata e teorica, finalizzata a determinare le condizioni in cui una funzione, detta funzione obiettivo, raggiunge un valore massimo o minimo rispetto a un insieme di possibili soluzioni. Questo insieme, noto come dominio ammissibile, può essere definito da vincoli specifici o coincidere con l'intero spazio delle variabili.

Un problema di ottimizzazione si formalizza generalmente nxella ricerca di un elemento $x^\ast$ appartenente a un insieme $S \subseteq \mathbb{R}^n$, tale che:

$$
f(x^\ast) = \min_{x \in S} f(x)
$$

dove $f: \mathbb{R}^n \to \mathbb{R}$ è la funzione obiettivo, $S$ rappresenta l'insieme delle soluzioni ammissibili e $x^\ast$ è detto punto ottimo o soluzione ottima.

Si distinguono problemi di ottimizzazione non vincolata, in cui $S = \mathbb{R}^n$, da problemi vincolati, dove l'insieme $S$ è definito attraverso condizioni esplicite, come:

$$
g_i(x) \leq 0 \quad \text{per} \quad i = 1, \dots, m \\
h_j(x) = 0 \quad \text{per} \quad j = 1, \dots, p
$$

In tali casi, le funzioni $g_i$ rappresentano i vincoli di disuguaglianza e le funzioni $h_j$ i vincoli di uguaglianza. La presenza di vincoli rende la ricerca della soluzione ottima più complessa, richiedendo l'uso di metodi specifici come le condizioni di Karush-Kuhn-Tucker (KKT) o l'analisi dei moltiplicatori di Lagrange.

All'interno della teoria si considerano anche problemi di ottimizzazione più generali, come quelli definiti su spazi astratti o su insiemi discreti. In tali contesti, la variabile $x$ può appartenere a spazi funzionali, spazi topologici o insiemi combinatori. Un esempio emblematico si ritrova nei problemi di programmazione lineare, in cui sia la funzione obiettivo che i vincoli sono espressi da relazioni lineari:

$$
\min c^T x \\
Ax \leq b
$$

dove $c \in \mathbb{R}^n$, $A \in \mathbb{R}^{m \times n}$ e $b \in \mathbb{R}^m$.

Esistono inoltre problemi in cui l'ottimizzazione coinvolge più funzioni obiettivo simultaneamente, detti problemi multi-obiettivo. In questi, la soluzione non è un singolo punto ottimo assoluto, bensì un insieme di soluzioni efficienti o Pareto-ottime, tali che non sia possibile migliorare una componente della funzione obiettivo senza peggiorarne almeno un'altra:

$$
\mathbf{f}(x) = (f_1(x), f_2(x), \dots, f_k(x))
$$

Il concetto di ottimizzazione si estende anche ai problemi continui su spazi di funzioni, come nel calcolo delle variazioni o nel controllo ottimo, dove l'obiettivo è minimizzare un funzionale definito su traiettorie o funzioni di stato. Un esempio classico è la minimizzazione di un integrale:

$$
J[u] = \int_{t_0}^{t_1} L(x(t), u(t), t) \, dt
$$

soggetto a vincoli dinamici dati da equazioni differenziali:

$$
\dot{x}(t) = f(x(t), u(t), t)
$$

Le metodologie per affrontare tali problemi spaziano dall'analisi matematica classica alle tecniche numeriche iterative, dai metodi deterministici ai procedimenti stocastici, con numerose applicazioni in economia, ingegneria, fisica e scienze computazionali.
