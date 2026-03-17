---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# kullback-Leibler (KL) Divergence
---
La [[Kullback–Leibler divergence]] misura quanto una distribuzione di probabilità $Q$ differisce da una distribuzione di riferimento $P$. È una quantità fondamentale della [[Teoria dell'informazione]] e della [[Inferenza statistica]] e quantifica la perdita di informazione quando $Q$ viene usata per approssimare $P$.

[[Definiizone di divergenza]]

Per distribuzioni discrete è definita come

$D_{KL}(P \parallel Q) = \sum_x P(x)\,\log \frac{P(x)}{Q(x)}$

mentre per distribuzioni continue

$D_{KL}(P \parallel Q) = \int P(x)\,\log \frac{P(x)}{Q(x)}\,dx$

La divergenza KL è sempre **non negativa**

$D_{KL}(P \parallel Q) \ge 0$

e vale zero se e solo se $P(x)=Q(x)$ quasi ovunque. Questa proprietà deriva dalla **disuguaglianza di Gibbs**.

Nonostante il nome, non è una distanza: non è simmetrica e non soddisfa la disuguaglianza triangolare

$D_{KL}(P \parallel Q) \neq D_{KL}(Q \parallel P)$

Per questo motivo viene interpretata come una **misura direzionale di divergenza informativa**.

La divergenza KL può essere espressa tramite l'[[Entropia]] e la [[Cross-entropy]]

$D_{KL}(P \parallel Q) = H(P,Q) - H(P)$

dove

$H(P) = -\sum_x P(x)\log P(x)$

è l'entropia di Shannon e

$H(P,Q) = -\sum_x P(x)\log Q(x)$

è la cross-entropy.

Nell'[[Apprendimento automatico]] la divergenza KL compare frequentemente nei problemi di ottimizzazione probabilistica, dove minimizzare $D_{KL}(P\parallel Q)$ equivale a trovare una distribuzione $Q$ che approssima al meglio la distribuzione vera $P$ in termini di informazione.