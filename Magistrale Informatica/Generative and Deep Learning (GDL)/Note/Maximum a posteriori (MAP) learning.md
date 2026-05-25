---
Course: "[[Generative and Deep Learning (GDL)]]"
Course 2: "[[Statistica (STAT)]]"
tags:
  - GDL
  - STAT
Area:
topic:
SubTopic:
---

# Maximum a posteriori (MAP) learning
---
Il **maximum a posteriori learning** e una strategia di [[Learning nei modelli probabilistici]] che sostituisce la posterior con una singola stima puntuale: il valore $\theta$ che massimizza la distribuzione a posteriori. $$\theta_{MAP}=\arg\max_{\theta} p(\theta\mid \mathcal{D})$$Usando la [[Formula di Bayes|formula di Bayes]] si ottiene$$\theta_{MAP}=\arg\max_{\theta} p(\mathcal{D}\mid \theta)p(\theta)$$poiche il termine $p(\mathcal{D})$ non dipende da $\theta$.

Il MAP e quindi una stima della posterior: invece di integrare su tutte le ipotesi come in [[Bayesian learning]], ne seleziona una sola, cioe la piu plausibile dopo aver osservato i dati.

Il ruolo del prior e essenziale:
- se il prior favorisce certi valori di $\theta$, la stima viene spinta in quella direzione
- il prior agisce quindi come forma di regolarizzazione rispetto a [[Maximum Liklehood learning|Maximum Liklehood]]

Nel quadro di [[Learning nei modelli probabilistici]], il MAP e quindi un compromesso tra completezza bayesiana e semplicita computazionale:
- usa sia dati sia conoscenza a priori
- produce una sola stima parametrica
- evita l'integrazione sulla posterior richiesta dal Bayesian learning
