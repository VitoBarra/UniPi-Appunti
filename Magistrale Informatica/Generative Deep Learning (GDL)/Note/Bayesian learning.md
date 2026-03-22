---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Bayesian learning
---
Il **Bayesian learning** stima i parametri di un modello probabilistico mantenendo una distribuzione a posteriori sui parametri invece di selezionare un singolo valore. Dati prior $p(\theta)$ e likelihood $p(\mathcal{D}\mid \theta)$, la posterior e
$$
p(\theta\mid \mathcal{D})=\frac{p(\mathcal{D}\mid \theta)p(\theta)}{p(\mathcal{D})}
$$
L'idea centrale e che la previsione non venga fatta usando una sola ipotesi parametrica, ma integrando tutte le ipotesi possibili pesate secondo la loro posterior. Per una nuova osservazione $x$ si ottiene quindi
$$
p(x\mid \mathcal{D})=\int p(x\mid \theta)p(\theta\mid \mathcal{D})\,d\theta
$$

Nel caso discreto, l'integrale e sostituito da una somma.

Questo approccio:
- tiene conto esplicitamente dell'incertezza sui parametri
- combina informazione a priori e dati osservati
- produce una predizione ottenuta mediando su tutte le ipotesi compatibili

Il limite principale e computazionale, perche il calcolo della posterior e della predizione bayesiana richiede spesso integrali non trattabili in forma chiusa. Per questo motivo il Bayesian learning e l'approccio piu completo dal punto di vista teorico, ma anche il piu difficile da usare in modelli complessi.
