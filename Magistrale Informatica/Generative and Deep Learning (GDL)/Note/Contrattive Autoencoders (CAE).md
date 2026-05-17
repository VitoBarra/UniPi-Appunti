---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Autoencoders
SubTopic:
---

# Contrattive Autoencoders (CAE)
---
I **Contractive Autoencoders** (**CAE**) sono una variante degli [[Autoencoders (AE)|autoencoders]] che aggiunge una penalità sulla sensibilità dell'encoder rispetto a piccole perturbazioni dell'input.

L'idea è che la rappresentazione latente non debba cambiare molto se l'input viene modificato leggermente. In questo modo l'encoder impara una rappresentazione più stabile e meno sensibile al rumore locale.

## Obiettivo

Un autoencoder standard minimizza una reconstruction loss:
$$
\mathcal{L}(x, \tilde{x})
$$

dove:
$$
z = f_{\theta}(x)
$$

$$
\tilde{x} = g_{\phi}(z)
$$

Il **contractive autoencoder** aggiunge una penalità sulla norma del jacobiano dell'encoder rispetto all'input:
$$
J_{\text{CAE}}(\theta,\phi)
=
\sum_{x \in \mathcal{D}}
\left[
\mathcal{L}(x, \tilde{x})
+ \lambda
\left\|
\frac{\partial f_{\theta}(x)}{\partial x}
\right\|_F^2
\right]
$$

dove:
- $\frac{\partial f_{\theta}(x)}{\partial x}$ è il jacobiano dell'encoder;
- $\left\|\cdot\right\|_F^2$ è la norma di Frobenius;
- $\lambda$ controlla il peso della penalità contractive.

## Interpretazione

La penalità forza l'encoder a essere localmente **contractive**: input molto vicini devono produrre rappresentazioni latenti simili.

In termini intuitivi, il modello vuole:
- ricostruire bene il dato;
- evitare che piccole perturbazioni dell'input producano grandi variazioni in $z$;
- mantenere sensibili solo le direzioni utili alla ricostruzione.

Questa proprietà è collegata alla [[Manifold Hypothesis|Manifold Hypothesis]]: il modello dovrebbe essere stabile nelle direzioni non significative, cioè fuori dalla manifold, e preservare invece le direzioni che descrivono variazioni reali dei dati.

## Differenza rispetto ai Denoising Autoencoders

I [[Denoising Autoencoders (DAE)]] imparano stabilità corrompendo esplicitamente l'input e chiedendo di ricostruire il dato pulito.

I **Contractive Autoencoders**, invece, impongono stabilità tramite una penalità differenziale sul jacobiano dell'encoder. La regolarizzazione è quindi locale e analitica: non richiede necessariamente di generare esempi rumorosi, ma misura direttamente quanto l'encoder cambia intorno ai punti di training.
