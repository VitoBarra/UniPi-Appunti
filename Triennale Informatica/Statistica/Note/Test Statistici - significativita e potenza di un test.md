---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area: "[[Test Statistici]]"
topic:
SubTopic:
---

# Test Statistici - significatività e potenza di un test
---
I [[Test Statistici|test statistici]] sono caratterizzati da due metriche fondamentali: **significatività** e **potenza**, che descrivono l’affidabilità della procedura decisionale. Per valutarle è necessario formalizzare i possibili errori nell’esito del test (rifiutare o non rifiutare $\mathcal{H}_0$).

Sia $C \subset \Omega$ la [[Test Statistici|regione di rifiuto]] per l’ipotesi nulla $\mathcal{H}_0$.
- Errore di **prima specie** (falso positivo): si **rifiuta** $\mathcal{H}_0$ quando il parametro $\theta \in \Theta_0$, con [[Definizione di Probabilita|probabilità]]  $\mathcal{P}_\theta(C)$
- Errore di **seconda specie** (falso negativo): si **accetta** $\mathcal{H}_0$ quando il parametro $\theta \in \Theta_1$, con [[Definizione di Probabilita|probabilità]]  $\mathcal{P}_\theta(C^c)$
Sia $\alpha \in (0,1)$. Un test si dice di **livello di significatività** $\alpha$ se$$
\forall \theta \in \Theta_0 \qquad \mathcal{P}_\theta(C) \le \alpha
$$Il livello $\alpha$ rappresenta un limite superiore per la probabilità di errore di **prima specie** (**falso positivo**).   Più piccolo è $\alpha$, maggiore è l’evidenza richiesta per rifiutare $\mathcal{H}_0$.

La potenza del test è la [[Funzioni|funzione]] definita su $\Theta_1$:$$
\Theta_1 \ni \theta \longmapsto \mathcal{P}_\theta(C)$$Essa rappresenta la probabilità di rifiutare correttamente $\mathcal{H}_0$ quando è falsa.   Una potenza elevata indica alta capacità del test di rilevare effetti reali.



La **curva operativa** è una definizione alternativa che racchiude entrambi gli aspetti.
la funzione definita su tutto $\Theta$:
$$
\Theta \ni \theta \longmapsto \beta(\theta)=\mathcal{P}_\theta(C^c)
$$
Essa descrive la probabilità di non rifiutare $\mathcal{H}_0$ in funzione del parametro.
- Per $\theta \in \Theta_0$, $\mathcal{P}_\theta(C)$ è il tasso di falso positivo;  
- per $\theta \in \Theta_1$, $\beta(\theta)$ è il tasso di falso negativo e $1-\beta(\theta)$ coincide con la potenza.


Il compromesso tra livello e potenza è centrale nella progettazione di un test: ridurre $\alpha$ tende ad aumentare $\beta(\theta)$ per alcuni valori in $\Theta_1$