---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Latent or hidden Model
---
Il **latent or hidden model** e una classe di [[modelli probabilistici|modelli probabilistici]] in cui il processo generativo dipende da una o piu variabili non osservabili direttamente, dette **variabili latenti** o **variabili nascoste**. In questi modelli le osservazioni disponibili non descrivono completamente il meccanismo generativo, ma ne rappresentano una versione marginalizzata.

## Struttura probabilistica

Si distinguono:
- variabili osservate $\mathbf{x}$
- variabili latenti $\mathbf{z}$
- parametri del modello $\theta$
In plate notation ![[IMG - Latent or hidden Model.png]]
La distribuzione [[Full Joint Distribution (FJD)|congiunta]] assume tipicamente la forma $$p(\mathbf{x},\mathbf{z}\mid \theta)=p(\mathbf{z}\mid \theta)p(\mathbf{x}\mid \mathbf{z},\theta)$$ottenuta tramite [[Chain rule|indipendenza condizionata]] la distribuzione osservata si ottiene per [[FJD - Marginalizzazione|marginalizzazione]] delle variabili latenti: $$p(\mathbf{x}\mid \theta)=\sum_{\mathbf{z}} p(\mathbf{x},\mathbf{z}\mid \theta)$$ nel caso discreto, oppure $$p(\mathbf{x}\mid \theta)=\int p(\mathbf{x},\mathbf{z}\mid \theta)\,d\mathbf{z}$$ nel caso continuo.
In forma compatta, la stessa quantita si puo esprimere come valore atteso rispetto a $p(\mathbf{z}\mid \theta)$: $$p(\mathbf{x}\mid \theta)=\mathbb{E}_{p(\mathbf{z}\mid \theta)}\left[p(\mathbf{x}\mid \mathbf{z},\theta)\right]$$

La variabile latente introduce quindi una struttura nascosta che consente di rappresentare dipendenze, sottopopolazioni o fattori generativi non direttamente accessibili dai dati osservati.

## Ruolo delle variabili latenti

Le variabili latenti possono rappresentare:
- classi non osservate
- cluster o componenti di miscela
- topic semantici
- fattori continui di variazione
- rappresentazioni compresse dei dati

Un latent model permette spesso di descrivere dati complessi tramite una decomposizione in elementi piu semplici e interpretabili.

## Inferenza

Dato un dato osservato $\mathbf{x}$, una quantita centrale e la distribuzione a posteriori della variabile latente $$p(\mathbf{z}\mid \mathbf{x},\theta)=\frac{p(\mathbf{x},\mathbf{z}\mid \theta)}{p(\mathbf{x}\mid \theta)}$$ ottenuta tramite [[Formula di Bayes|formula di Bayes]]. Questa distribuzione misura quali configurazioni latenti siano compatibili con l'osservazione.

In molti modelli la posterior non ha forma chiusa o richiede il calcolo di una marginalizzazione costosa, quindi l'inferenza diventa il problema principale del modello.

## Apprendimento

L'apprendimento dei parametri richiede la massimizzazione della likelihood osservata $$p(\mathcal{D}\mid \theta)=\prod_{n=1}^N p(\mathbf{x}_n\mid \theta)=\prod_{n=1}^N \sum_{\mathbf{z}_n} p(\mathbf{x}_n,\mathbf{z}_n\mid \theta)$$ oppure della corrispondente log-likelihood $$\log p(\mathcal{D}\mid \theta)=\sum_{n=1}^N \log \sum_{\mathbf{z}_n} p(\mathbf{x}_n,\mathbf{z}_n\mid \theta)$$

La presenza della marginalizzazione interna rende il problema piu difficile rispetto ai modelli senza variabili nascoste. Per questo motivo si usano spesso metodi dedicati come:
- Expectation-Maximization
- inferenza variazionale
- campionamento Monte Carlo

## Interpretazione

Un latent model separa cio che viene osservato da cio che viene ipotizzato come causa o struttura interna dei dati. Dal punto di vista statistico, il modello osservato e una distribuzione marginale, mentre dal punto di vista generativo il dato nasce da un processo in due stadi: prima si genera $\mathbf{z}$, poi si genera $\mathbf{x}$ condizionatamente a $\mathbf{z}$.

## Modelli collegati

- [[Mixture Models|Mixture Models]]: la variabile latente seleziona la componente generatrice.
- [[Mixture of Gaussian model (GMM)|Mixture of Gaussian model]]: la variabile latente identifica la gaussiana responsabile del campione.
- [[Latent Dirichlet Allocation (LDA)|Latent Dirichlet Allocation (LDA)]]: le variabili latenti rappresentano topic documentali e assegnamenti topic-parola.
