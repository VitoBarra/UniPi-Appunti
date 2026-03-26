---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Learning nei modelli probabilistici
---
Il **learning nei modelli probabilistici** consiste nell'inferire i parametri $\theta$ di una distribuzione parametrica $p(\cdot\mid \theta)$ a partire da un insieme di dati osservati $\mathcal{D}$. Nella prospettiva del corso, il learning e quindi un problema di inferenza: bisogna capire quali ipotesi parametriche siano piu compatibili con i dati osservati.

Dato un modello parametrico, l'apprendimento richiede due scelte:
- la famiglia di distribuzioni che definisce il modello
- il criterio inferenziale con cui stimare i parametri

Applicando la [[Formula di Bayes|formula di Bayes]] ai parametri del modello si ottiene
$$
p(\theta\mid \mathcal{D})=\frac{p(\mathcal{D}\mid \theta)p(\theta)}{p(\mathcal{D})}
$$

Da questa decomposizione emergono i tre approcci principali al learning:
- [[Bayesian learning]]: mantiene l'intera posterior sui parametri e predice mediando su tutte le ipotesi
- [[Maximum a posteriori (MAP) learning]]: sceglie la singola ipotesi parametrica che massimizza la posterior
- [[Maximum likelihood learning]]: sceglie la singola ipotesi parametrica che massimizza la likelihood dei dati

La differenza concettuale sta quindi in **come si usa la posterior**:
- nel Bayesian learning la si usa tutta
- nel MAP la si sintetizza nel suo massimo
- nel maximum likelihood si ignora il prior, che equivale al caso di prior uniforme o costante nella massimizzazione
