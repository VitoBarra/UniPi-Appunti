---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Latent Dirichlet Allocation (LDA)
---
Latent Dirichlet Allocation (LDA) è u---n modello probabilistico generativo a variabili latenti che estende la rappresentazione [[Bag of words|Bag of Words]] introducendo una struttura nascosta in cui ogni documento è modellato come una miscela di topic.

Nel contesto di un corpus rappresentato come matrice termine-documento $X \in \mathbb{N}^{N \times M}$, LDA assume che ogni documento $d$ sia generato da una distribuzione latente sui topic, e che ogni parola sia associata a un topic specifico :contentReference[oaicite:0]{index=0}

Struttura del modello:
- $K$ topic latenti
- $\theta_d \in \Delta^{K-1}$ distribuzione dei topic per documento
- $z_{dn} \in \{1,\dots,K\}$ assegnamento del topic per la $n$-esima parola
- $w_{dn} \in \{1,\dots,N\}$ parola osservata
- $\beta \in \mathbb{R}^{K \times N}$ distribuzioni parola-topic con $$\beta_{k j} = P(w_j|z=k)$$

Distribuzioni:
- $$\theta_d \sim \text{Dirichlet}(\alpha)$$
- $$z_{dn} \sim \text{Multinomial}(\theta_d)$$
- $$w_{dn} \sim \text{Multinomial}(\beta_{z_{dn}})$$

Processo generativo per ogni documento $d$:
- campiona $$\theta_d \sim \text{Dirichlet}(\alpha)$$
- per ogni posizione $n = 1,\dots,N_d$:
  - campiona $$z_{dn} \sim \text{Multinomial}(\theta_d)$$
  - campiona $$w_{dn} \sim \text{Multinomial}(\beta_{z_{dn}})$$

La distribuzione congiunta è $$P(\theta_d, \mathbf{z}_d, \mathbf{w}_d|\alpha,\beta) = P(\theta_d|\alpha)\prod_{n=1}^{N_d} P(z_{dn}|\theta_d)P(w_{dn}|z_{dn},\beta)$$ 


Marginalizzando le variabili latenti si ottiene la likelihood del documento $$P(\mathbf{w}_d|\alpha,\beta) = \int P(\theta_d|\alpha)\prod_{n=1}^{N_d} \sum_{z_{dn}} P(z_{dn}|\theta_d)P(w_{dn}|z_{dn},\beta)\, d\theta_d$$

Interpretazione:
- ogni documento è una combinazione convessa di topic
- ogni topic è una distribuzione multinomiale sulle parole
- la variabile latente $z_{dn}$ assegna un topic a ciascuna parola
- il modello cattura co-occorrenze statistiche tra parole

Ruolo della Dirichlet:
- $\alpha$ controlla la sparsità di $\theta_d$
- $\theta_d$ è una variabile aleatoria su simplex $$\sum_{k=1}^K \theta_{dk}=1$$
- prior coniugato alla multinomiale ⇒ aggiornamenti analitici in inferenza

Apprendimento:
- massimizzazione della log-likelihood $$\mathcal{L}(\alpha,\beta) = \sum_{d=1}^M \log P(\mathbf{w}_d|\alpha,\beta)$$
- inferenza non trattabile esattamente per accoppiamento tra $\theta$ e $z$
- uso di [[Calcolo variazionle|Variational]] Inference o EM approssimato per stimare:
  - parametri $\beta$
  - distribuzioni latenti $\theta_d$ e $z_{dn}$

Proprietà:
- estende [[Bag of words|Bag of Words]] introducendo struttura latente
- rappresentazione compatta in spazio di dimensione $K \ll N$
- modello generativo interpretabile basato su variabili latenti