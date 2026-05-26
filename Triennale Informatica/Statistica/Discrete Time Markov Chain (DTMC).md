---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Discrete Time Markov Chain (DTMC)
---
Una **Discrete Time Markov Chain (DTMC)** è un processo stocastico $\{X_n\}_{n \in \mathbb{N}}$ a **tempo discreto** che soddisfa la **proprietà di Markov**:

$$
\mathcal{P}(X_{n+1}=j \mid X_n=i, X_{n-1}, \dots, X_0)
=
\mathcal{P}(X_{n+1}=j \mid X_n=i).
$$

Quindi, conosciuto lo stato attuale, il futuro non dipende più dal passato. Per questo si dice che il processo ha **assenza di memoria** rispetto alla storia precedente.

## Intuizione

In una DTMC il tempo evolve per passi:

$$
n = 0,1,2,\dots
$$

e ad ogni passo il processo può restare nello stesso stato oppure passare in un altro.

Una DTMC descrive quindi:

- in quale stato si trova il sistema al passo $n$;
- con quale probabilità passa da uno stato a un altro in un solo passo.

## Matrice di transizione

Il comportamento del processo è descritto dalla **matrice di transizione**

$$
P=(p_{ij})
$$

dove

$$
p_{ij} = \mathcal{P}(X_{n+1}=j \mid X_n=i).
$$

Le proprietà fondamentali di $P$ sono:

- $p_{ij} \ge 0$;
- $\sum_j p_{ij}=1$ per ogni stato $i$.

Quindi ogni riga di $P$ è una distribuzione di probabilità.

## Evoluzione nel tempo

La probabilità di passare da $i$ a $j$ in $n$ passi è

$$
p_{ij}^{(n)} = \mathcal{P}(X_n=j \mid X_0=i).
$$

La matrice delle transizioni in $n$ passi è

$$
P^n.
$$

Se $\mu_0$ è la distribuzione iniziale scritta come vettore riga, allora dopo $n$ passi la distribuzione è

$$
\mu_n = \mu_0 P^n.
$$

Equivalentemente, vale la ricorrenza

$$
\mu_{n+1} = \mu_n P.
$$

## Esempio minimo a due stati

Supponiamo di avere due stati $0$ e $1$ e matrice

$$
P=
\begin{pmatrix}
1-\alpha & \alpha \\
\beta & 1-\beta
\end{pmatrix}
$$

con $0 \le \alpha,\beta \le 1$.

Questo significa:

- se il processo è in $0$, al passo successivo va in $1$ con probabilità $\alpha$;
- se il processo è in $1$, al passo successivo va in $0$ con probabilità $\beta$.

Le probabilità sulla diagonale rappresentano invece la probabilità di rimanere nello stesso stato per un altro passo.

## Distribuzione stazionaria

Una distribuzione $\pi$ è **stazionaria** se non cambia dopo un passo della catena:

$$
\pi P = \pi.
$$

con inoltre

$$
\sum_i \pi_i = 1,
\qquad
\pi_i \ge 0.
$$

Se la catena è sufficientemente ben connessa, la distribuzione di $X_n$ tende a $\pi$ per $n \to \infty$.

Nel caso a due stati precedente si ottiene

$$
\pi_0 = \frac{\beta}{\alpha+\beta},
\qquad
\pi_1 = \frac{\alpha}{\alpha+\beta}.
$$

## Classificazione degli stati

Alcune proprietà importanti delle DTMC sono:

- **accessibilità**: lo stato $j$ è accessibile da $i$ se esiste un numero di passi $n$ tale che $p_{ij}^{(n)} > 0$;
- **irriducibilità**: ogni stato è accessibile da ogni altro;
- **periodicità**: uno stato ha periodo $d$ se si può ritornare ad esso solo in tempi multipli di $d$;
- **ricorrenza** e **transienza**: uno stato è ricorrente se, partendo da esso, vi si ritorna con probabilità $1$.

Queste proprietà determinano il comportamento a lungo termine della catena.

## Collegamento con le CTMC

La relazione con [[Continue Time Markov Chain (CTMC)]] è molto stretta.

Una CTMC può essere vista come:

- una **DTMC dei salti** che decide la sequenza degli stati visitati;
- più dei **tempi di permanenza esponenziali** tra un salto e il successivo.

Se una CTMC ha generatore $Q=(q_{ij})$, allora per ogni stato $i$ si definisce

$$
\lambda_i = -q_{ii} = \sum_{j \ne i} q_{ij}.
$$

Quando il processo lascia lo stato $i$, il prossimo stato $j$ viene scelto con probabilità

$$
p_{ij} = \frac{q_{ij}}{\lambda_i},
\qquad j \ne i.
$$

La matrice $P=(p_{ij})$ così ottenuta definisce una DTMC chiamata **jump chain** o **embedded chain** della CTMC.

Quindi:

$$
\text{CTMC} = \text{DTMC dei salti} + \text{tempi di attesa continui}.
$$

## Differenza essenziale tra DTMC e CTMC

Una DTMC dice solo cosa succede **a ogni passo**:

$$
X_0, X_1, X_2, \dots
$$

ma non specifica quanto tempo reale passa tra un passo e il successivo.

Una [[Continue Time Markov Chain (CTMC)]] invece descrive l'evoluzione rispetto a un tempo reale $t \ge 0$, quindi include anche l'informazione su **quando** avvengono i salti.

## Collegamenti utili

- [[Markov chains]] per una panoramica generale;
- [[Continue Time Markov Chain (CTMC)]] per il caso a tempo continuo.
