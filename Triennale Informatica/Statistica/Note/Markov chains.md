---
Course: "[[Statistica (STAT)]]"
Area: 
topic: "[[Intelligenza Artificiale (IA)|Reti neurali]]"
SubTopic: 
tags:
  - STAT
---
# Markov chains
---
Una **catena di Markov** è un processo stocastico a **tempo discreto** che soddisfa la **proprietà di Markov** anche detta **assenza di memoria**, secondo cui la probabilità di transizione allo stato successivo dipende unicamente dallo stato attuale e non dalla sequenza degli stati precedenti. Formalmente, se $\{X_n\}_{n \in \mathbb{N}}$ è una sequenza di variabili aleatorie che rappresentano gli stati visitati al tempo $n$, la proprietà di Markov si esprime come:

$$
\begin{array}{}

\mathcal{P}(X_{n+1} = x_{n+1} \mid X_n = x_n, X_{n-1} = x_{n-1}, \dots, X_0 = x_0)  \\
= \mathcal{P}(X_{n+1} = x_{n+1} \mid X_n = x_n)
\end{array}
$$

Il comportamento dinamico del processo è descritto dalla matrice di transizione $P = (p_{ij})$, dove ciascun elemento $p_{ij}$ rappresenta la probabilità di transizione dallo stato $i$ allo stato $j$ in un solo passo:

$$
p_{ij} = \mathcal{P}(X_{n+1} = j \mid X_n = i)
$$

La matrice $P$ è stocastica a destra: ogni riga somma a $1$, ovvero $\sum_j p_{ij} = 1$ per ogni $i$. Lo spazio degli stati può essere finito o numerabile, e la struttura della catena dipende dalla connettività degli stati. Uno stato $j$ è accessibile da uno stato $i$ se esiste $n \geq 0$ tale che $\mathbb{P}(X_n = j \mid X_0 = i) > 0$.

Una catena è detta irriducibile se ogni stato è accessibile da ogni altro. Uno stato $i$ ha periodo $d$ se $d$ è il massimo comun divisore dei tempi $n$ per cui $\mathbb{P}(X_n = i \mid X_0 = i) > 0$. Uno stato è aperiodico se il suo periodo è $1$.

Uno stato è ricorrente se la probabilità di ritornarvi in un tempo finito è $1$, transiente altrimenti. Una catena è positiva ricorrente se il tempo atteso di ritorno allo stato è finito. Esiste una distribuzione stazionaria $\pi$ se $\pi P = \pi$, cioè:

$$
\sum_i \pi_i p_{ij} = \pi_j
$$

Tale distribuzione rappresenta un equilibrio del sistema in cui la probabilità di essere in uno stato non cambia nel tempo. In presenza di irriducibilità, aperiodicità e positività ricorrente, la distribuzione stazionaria è unica e la catena converge verso di essa indipendentemente dalla distribuzione iniziale.



markov chains del primo (a) e secondo (b) ordine viste come [[Bayesian network|bayes net]]
![[IMG - frist e second order of Markov process with bayesian network.png]]