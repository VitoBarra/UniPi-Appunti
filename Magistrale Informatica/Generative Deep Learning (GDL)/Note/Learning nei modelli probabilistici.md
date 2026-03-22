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
Il **learning nei modelli probabilistici** consiste nell'inferire i parametri $\theta$ di una distribuzione parametrica $p(\cdot\mid \theta)$ a partire da un insieme di dati osservati $\mathcal{D}$. In questo senso l'apprendimento e un problema di inferenza: si tratta di decidere quali valori dei parametri rendano il modello compatibile con i dati osservati.

Dato un modello parametrico, l'apprendimento richiede due scelte:
- la famiglia di distribuzioni che definisce il modello
- il criterio inferenziale con cui stimare i parametri

I tre approcci classici sono:
- [[Bayesian learning]]: mantiene una distribuzione sui parametri e predice integrando su tutte le ipotesi possibili
- [[Maximum a posteriori (MAP) learning]]: seleziona il valore dei parametri che massimizza la distribuzione a posteriori
- [[Maximum likelihood learning]]: seleziona il valore dei parametri che massimizza la likelihood dei dati

Nel formalismo bayesiano si introducono:
- il **prior** $p(\theta)$
- la **likelihood** $p(\mathcal{D}\mid \theta)$
- la **posterior** $p(\theta\mid \mathcal{D})$
legate da [[Formula di Bayes|formula di Bayes]]:$$p(\theta\mid \mathcal{D})=\frac{p(\mathcal{D}\mid \theta)p(\theta)}{p(\mathcal{D})}$$
I tre approcci differiscono per il modo in cui trattano la posterior:
- l'approccio bayesiano usa l'intera distribuzione $p(\theta\mid \mathcal{D})$
- il MAP usa soltanto il punto di massimo della posterior
- il ML ignora il prior e usa solo la likelihood
