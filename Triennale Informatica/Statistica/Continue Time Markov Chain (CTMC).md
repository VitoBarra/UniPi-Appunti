---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Continue Time Markov Chain (CTMC)
---
Una **Continue Time Markov Chain (CTMC)** è un processo stocastico $\{X_t\}_{t \ge 0}$ a **tempo continuo** con spazio degli stati finito o numerabile che soddisfa la **proprietà di Markov**:$$
\mathcal{P}(X_{t+h}=j \mid X_t=i,\text{ passato fino al tempo }t)
=
\mathcal{P}(X_{t+h}=j \mid X_t=i)
$$per ogni $h>0$ sufficientemente piccolo.

L'idea è la stessa di [[Markov chains]], ma qui il tempo non evolve a passi discreti $n=0,1,2,\dots$; il sistema può invece cambiare stato in un qualunque istante reale $t \ge 0$.

Una **CTMC** resta in uno stato per un certo **tempo di permanenza** casuale, poi salta in un altro stato, poi resta di nuovo ferma, e così via. Quindi una CTMC è descritta da due ingredienti:
1. **quanto tempo resta** in uno stato;
2. **in quale stato va** quando avviene il salto.
Il punto fondamentale è che, se il processo si trova nello stato $i$, il tempo rimanente prima del prossimo salto dipende solo da $i$ e non da quanto tempo il processo ci è già rimasto. Questa è una manifestazione della proprietà [[Variabili aleatorie senza memoria|senza memoria]].

## Matrice dei tassi o generatore

L'oggetto principale di una **CTMC** è la **matrice generatrice** o **matrice dei tassi**$$Q = (q_{ij})$$con le proprietà:
- $q_{ij} \ge 0$ per $i \ne j$;
- $q_{ii} = -\sum_{j \ne i} q_{ij}$;
- quindi ogni riga somma a $0$.
Per $i \ne j$, il coefficiente $q_{ij}$ rappresenta il **tasso istantaneo** di transizione da $i$ a $j$:$$q_{ij} = \lim_{h \to 0^+} \frac{\mathcal{P}(X_{t+h}=j \mid X_t=i)}{h}$$In un intervallo molto piccolo $h$ vale quindi, in prima approssimazione,$$
\begin{align}
\mathcal{P}(X_{t+h}=j \mid X_t=i) &\approx q_{ij} h, \qquad j \ne i \\
\mathcal{P}(X_{t+h}=i \mid X_t=i) &\approx 1 + q_{ii} h \\
&= 1 - \left(\sum_{j \ne i} q_{ij}\right)h
\end{align}
$$

Se il processo si trova nello stato $i$, il tempo $T_i$ che trascorre prima di lasciare lo stato $i$ ha distribuzione [[Variabili Aleatorie Notevoli - Esponenziale|esponenziale]] con parametro$$\lambda_i = -q_{ii} = \sum_{j \ne i} q_{ij}$$Quindi$$\mathcal{P}(T_i > t) = e^{-\lambda_i t}$$e$$\mathbb{E}[T_i] = \frac{1}{\lambda_i}.$$Questo spiega perché la distribuzione esponenziale compare naturalmente nelle CTMC: è l'unica distribuzione continua con proprietà di assenza di memoria.

Una volta terminato il tempo di permanenza nello stato $i$, il prossimo stato non viene scelto uniformemente, ma secondo le probabilità$$
\mathcal{P}(\text{prossimo stato}=j \mid \text{si lascia } i)
=
\frac{q_{ij}}{\lambda_i},
\qquad j \ne i$$Quindi una CTMC può essere vista come:
- una catena di salti tra stati;
- con tempi di attesa esponenziali tra un salto e il successivo.

## Matrice di transizione nel tempo

Per ogni $t \ge 0$ si definisce la matrice di transizione $$P(t) = (p_{ij}(t)),\qquad p_{ij}(t)=\mathcal{P}(X_t=j \mid X_0=i)$$Vale:$$P(0)=I$$e la famiglia $\{P(t)\}_{t \ge 0}$ soddisfa la proprietà di [[Semigruppi|semigruppo]] $$P(s+t)=P(s)P(t)$$

## Equazioni di Kolmogorov

Le probabilità di transizione evolvono secondo le **equazioni di Kolmogorov**:$$\frac{d}{dt}P(t)=P(t)Q$$oppure, equivalentemente,$$\frac{d}{dt}P(t)=Q P(t),$$a seconda che si guardi la forma backward o forward.

Qui $P(t)$ non è altro che la matrice che descrive come evolve la probabilità nel tempo: il coefficiente $p_{ij}(t)$ rappresenta la probabilità di trovarsi nello stato $j$ al tempo $t$ sapendo che al tempo iniziale il processo era nello stato $i$.

Il punto concettuale piu importante e che questa equazione non descrive direttamente una singola traiettoria del processo, ma l'evoluzione della **distribuzione di probabilità** sugli stati. Una traiettoria individuale della CTMC salta in istanti casuali; la Kolmogorov equation descrive invece come cambia nel tempo la legge complessiva del processo.

Nel caso finito e omogeneo nel tempo, la soluzione si scrive in forma compatta come$$P(t)=e^{tQ}$$dove $e^{tQ}$ è l'**esponenziale di matrice** del generatore $Q$. Questa formula è l'analogo continuo di $P^n$ nelle [[Discrete Time Markov Chain (DTMC)]]: lì si evolve per passi discreti, qui si evolve rispetto a un tempo reale $t$.

Se $\mu(0)$ è la distribuzione iniziale scritta come vettore riga, allora la distribuzione al tempo $t$ è$$\mu(t)=\mu(0)P(t)$$

Questa formula dice che, per conoscere la legge del processo al tempo $t$, basta prendere la distribuzione iniziale e propagarla tramite la matrice di transizione continua $P(t)$.

La distribuzione $\mu(t)$ soddisfa inoltre l'equazione differenziale$$\frac{d}{dt}\mu(t)=\mu(t)Q$$

che esprime un **bilancio di flusso di probabilità** tra gli stati: una parte della probabilità esce da uno stato verso gli altri, e un'altra parte entra dagli altri stati.

Questa e quindi la legge dinamica fondamentale delle CTMC: se si conosce il generatore $Q$, allora si conosce come la distribuzione del processo evolve nel tempo.

Se scriviamo $\mu(t)=(\mu_1(t),\dots,\mu_n(t))$, allora per ogni stato $j$ vale

$$
\frac{d}{dt}\mu_j(t)
=
\sum_{i \ne j}\mu_i(t)q_{ij} + \mu_j(t)q_{jj}.
$$

Poiché $q_{jj}<0$, il termine $\mu_j(t)q_{jj}$ rappresenta la probabilità che **lascia** lo stato $j$, mentre i termini $\mu_i(t)q_{ij}$ con $i \ne j$ rappresentano la probabilità che **entra** in $j$ dagli altri stati.
## Distribuzione stazionaria

Una distribuzione $\pi$ è **stazionaria** se, una volta inizializzato il processo con quella distribuzione, la legge non cambia nel tempo. Formalmente:$$
\pi Q = 0,
\qquad
\sum_i \pi_i = 1,
\qquad
\pi_i \ge 0.
$$Questa è l'analoga a tempo continuo della condizione $\pi P = \pi$ vista per [[Markov chains]].

## Esempio minimo a due stati

Consideriamo due stati $0$ e $1$:
- da $0$ a $1$ con tasso $\alpha$;
- da $1$ a $0$ con tasso $\beta$.
Allora$$Q=
\begin{pmatrix}
-\alpha & \alpha \\
\beta & -\beta
\end{pmatrix}
$$I tempi di permanenza sono:
- in $0$: esponenziale di parametro $\alpha$;
- in $1$: esponenziale di parametro $\beta$.
La distribuzione stazionaria si ottiene da $\pi Q = 0$ e vale
$$
\pi_0 = \frac{\beta}{\alpha+\beta},
\qquad
\pi_1 = \frac{\alpha}{\alpha+\beta}
$$Quindi il processo passa più tempo nello stato che si lascia più lentamente.

## Riassunto operativo

Per specificare una CTMC basta assegnare la matrice $Q$.

Da $Q$ si ricavano subito:
- il tasso totale di uscita dallo stato $i$: $\lambda_i=-q_{ii}$;
- il tempo di permanenza nello stato $i$: $T_i \sim \mathrm{Exp}(\lambda_i)$;
- la probabilità di saltare da $i$ a $j$ dopo l'attesa: $\frac{q_{ij}}{\lambda_i}$.
