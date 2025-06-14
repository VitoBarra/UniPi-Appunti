---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Bayesian network con variabili continue
---
i **[[Bayesian network|Bayesian network]]** può includere anche [[Variabili Aleatorie (Casuali)|variabili]] **continue**. Poiché le variabili continue hanno un numero infinito di valori possibili, non è possibile specificare esplicitamente tutte le tabelle CSP. per gestirle quindi alcuni approcci comuni sono:
- **Discretizzazione**: suddividere i valori possibili in intervalli discreti. Ad esempio, la temperatura può essere divisa in tre categorie: (<0°C), (0°C−100°C), (>100°C). La scelta del numero di intervalli comporta un compromesso tra accuratezza e dimensione della CPT.
- **Distribuzioni standard**: usare funzioni di densità note, come la **Gaussiana** $N(x; \mu, \sigma^2)$, specificata da media $\mu$ e varianza $\sigma^2$.
- **Rappresentazioni non parametriche**: definire la distribuzione condizionata implicitamente tramite un insieme di istanze osservate
Una rete che contiene sia variabili discrete sia continue è detta **hybrid Bayesian network**. Per specificare una rete ibrida, si devono definire:
- la distribuzione condizionata di una variabile continua dati genitori discreti o continui;
- la distribuzione condizionata di una variabile discreta dati genitori continui.
Un caso tipico è il **linear–Gaussian conditional distribution** per variabili continue: il figlio ha distribuzione gaussiana, la cui media $\mu$ varia linearmente con i valori dei genitori e la deviazione standard $\sigma$ è fissa. Se il nodo ha genitori discreti, si definiscono distribuzioni separate per ciascun valore discreto.
Per variabili discrete con genitori continui, si possono usare funzioni di **soglia morbida** come:
- **Probit model**: $$
P(buys \mid Cost = c) = 1 - \Phi\left(\frac{c - \mu}{\sigma}\right)
$$dove $\Phi(x) = \int_{-\infty}^{x} N(s; 0, 1) ds$ è la funzione di distribuzione cumulativa normale standard.
- **Logistic (expit) model**:$$
P(buys | Cost = c) = 1 - \frac{1}{1 + \exp\left(-\frac{4}{\sqrt{2\pi}} \frac{c-\mu}{\sigma}\right)}
$$
Entrambi i modelli possono essere generalizzati a più genitori continui o discreti con valori numerici, combinando linearmente gli input, ottenendo una struttura simile al modello **noisy-OR** per variabili discrete.

Le reti ibride consentono di rappresentare sia la dipendenza lineare di variabili continue dai genitori sia la probabilità condizionata delle variabili discrete, mantenendo coerenza probabilistica e possibilità di inferenza efficiente.
