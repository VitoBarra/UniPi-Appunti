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
Latent Dirichlet Allocation (LDA) e un [[Latent or hidden Model|modello a variabili latenti]] che estende la rappresentazione [[Bag of words|Bag of Words]] introducendo una struttura nascosta in cui ogni documento e modellato come una miscela di topic.

Nel contesto di un corpus rappresentato come matrice termine-documento $X \in \mathbb{N}^{N \times M}$, LDA assume che ogni documento $d$ sia generato da una distribuzione latente sui topic e che ogni parola osservata sia associata a un topic specifico.

Struttura del modello:
- $K$ topic latenti
- $\theta_d \in \Delta^{K-1}$ distribuzione dei topic per il documento $d$
- $z_{dn} \in \{1,\dots,K\}$ assegnamento del topic per la parola in posizione $n$
- $w_{dn} \in \{1,\dots,N\}$ parola osservata
- $\beta \in \mathbb{R}^{K \times N}$ distribuzioni parola-topic con $\beta_{kj}=P(w_j\mid z=k)$

Distribuzioni:
- $\theta_d \sim \text{Dirichlet}(\alpha)$
- $z_{dn} \sim \text{Multinomial}(\theta_d)$
- $w_{dn} \sim \text{Multinomial}(\beta_{z_{dn}})$

Processo generativo per ogni documento $d$:
- campiona $\theta_d \sim \text{Dirichlet}(\alpha)$
- per ogni posizione $n=1,\dots,N_d$:
- campiona $z_{dn} \sim \text{Multinomial}(\theta_d)$
- campiona $w_{dn} \sim \text{Multinomial}(\beta_{z_{dn}})$

La distribuzione congiunta e $$P(\theta_d,\mathbf{z}_d,\mathbf{w}_d\mid \alpha,\beta)=P(\theta_d\mid \alpha)\prod_{n=1}^{N_d}P(z_{dn}\mid \theta_d)P(w_{dn}\mid z_{dn},\beta)$$

Marginalizzando le variabili latenti si ottiene la likelihood del documento $$P(\mathbf{w}_d\mid \alpha,\beta)=\int P(\theta_d\mid \alpha)\prod_{n=1}^{N_d}\sum_{z_{dn}}P(z_{dn}\mid \theta_d)P(w_{dn}\mid z_{dn},\beta)\,d\theta_d$$

Interpretazione:
- ogni documento e una combinazione convessa di topic
- ogni topic e una distribuzione multinomiale sulle parole
- la variabile latente $z_{dn}$ assegna un topic a ciascuna parola
- il modello cattura struttura semantica non osservabile direttamente nel vettore bag-of-words

Ruolo della Dirichlet:
- $\alpha$ controlla la sparsita di $\theta_d$
- $\theta_d$ e una variabile aleatoria sul simplesso con $\sum_{k=1}^K \theta_{dk}=1$
- la [[Variabili aleatorie Notevoli - Dirichlet|Dirichlet]] e prior coniugato della distribuzione multinomiale

Apprendimento:
- si massimizza la log-likelihood $\mathcal{L}(\alpha,\beta)=\sum_{d=1}^M \log P(\mathbf{w}_d\mid \alpha,\beta)$
- l'inferenza esatta non e trattabile per l'accoppiamento tra $\theta_d$ e $z_{dn}$
- si usano tipicamente metodi di inferenza approssimata come EM variazionale o [[Calcolo variazionle|Variational]] Inference

Proprieta:
- estende [[Bag of words|Bag of Words]] introducendo struttura latente
- fornisce una rappresentazione compatta in uno spazio di dimensione $K \ll N$
- e un modello generativo interpretabile basato su variabili latenti
