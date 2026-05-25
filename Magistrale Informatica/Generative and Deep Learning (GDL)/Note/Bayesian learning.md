---
Course: "[[Generative and Deep Learning (GDL)]]"
Corse 1: "[[Statistica (STAT)]]"
tags:
  - GDL
  - STAT
Area:
topic:
SubTopic:
---

# Bayesian learning
---
Il **Bayesian learning** e l'approccio piu completo a [[Learning nei modelli probabilistici]], perche non seleziona un singolo valore dei parametri ma mantiene l'intera distribuzione a posteriori sulle ipotesi parametriche. Dati prior $p(\theta)$ e likelihood $p(\mathcal{D}\mid \theta)$, la posterior e$$p(\theta\mid \mathcal{D})=\frac{p(\mathcal{D}\mid \theta)p(\theta)}{p(\mathcal{D})}$$ la [[Formula di Bayes|formula di byes]]

L'idea centrale e che la previsione non venga fatta usando una sola ipotesi parametrica, ma mediando tutte le ipotesi possibili pesate secondo la loro posterior. Per una nuova osservazione $x$ si ottiene quindi
$$
p(x\mid \mathcal{D})=\int p(x\mid \theta)p(\theta\mid \mathcal{D})\,d\theta
$$

Nel caso discreto, l'integrale è sostituito da una somma.

Questo approccio:
- Tiene conto esplicitamente dell'incertezza sui parametri
- Combina informazione a priori e dati osservati
- Produce una predizione ottenuta mediando su tutte le ipotesi compatibili
Rispetto agli altri criteri di [[Learning nei modelli probabilistici]]:
- E piu ricco di [[Maximum a posteriori (MAP) learning]], perche non riduce la posterior a una sola stima puntuale
- E piu generale di [[z]], perche include esplicitamente anche il prior
Il limite principale e computazionale, perche il calcolo della posterior e della predizione bayesiana richiede spesso integrali non trattabili in forma chiusa. Per questo motivo il Bayesian learning e l'approccio piu completo dal punto di vista teorico, ma anche il piu difficile da usare in modelli complessi.
