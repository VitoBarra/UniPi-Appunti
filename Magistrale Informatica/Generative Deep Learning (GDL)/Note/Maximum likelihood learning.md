---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Maximum likelihood learning
---
Il **maximum likelihood learning** stima i parametri scegliendo il valore $\theta$ che rende i dati osservati il piu probabili possibile sotto il modello:
$$
\theta_{ML}=\arg\max_{\theta} p(\mathcal{D}\mid \theta)
$$

Se i dati sono iid, la likelihood si fattorizza come
$$
p(\mathcal{D}\mid \theta)=\prod_{n=1}^N p(x_n\mid \theta)
$$
e si lavora spesso sulla log-likelihood
$$
\log p(\mathcal{D}\mid \theta)=\sum_{n=1}^N \log p(x_n\mid \theta)
$$
perche trasforma prodotti in somme e semplifica l'ottimizzazione.

Il maximum likelihood learning:
- dipende solo dai dati osservati
- non usa un prior esplicito sui parametri
- produce una stima puntuale interamente data-driven

Questo approccio e spesso il piu semplice da implementare e il piu usato nei modelli probabilistici di base. Tuttavia, in regime di pochi dati, la stima puo essere instabile o troppo sensibile al campione osservato. In questo senso [[Maximum a posteriori (MAP) learning]] puo essere visto come una versione regolarizzata del **maximum likelihood**.
