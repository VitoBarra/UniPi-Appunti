---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Hidden Markov chains
---
Hidden Markov chains (o Hidden Markov Models, HMM) sono [[latent variable models|modelli probabilistici con variabili latenti]] progettati per descrivere sequenze di osservazioni generate da uno stato nascosto che evolve nel tempo.

Il modello assume due tipi di variabili:
- una sequenza di **stati latenti** $Z_1,\dots,Z_T$
- una sequenza di **osservazioni** $X_1,\dots,X_T$

Gli stati latenti rappresentano il processo nascosto che evolve nel tempo mentre le osservazioni sono le variabili osservabili generate dagli stati.

La struttura probabilistica del modello è definita da due assunzioni principali:
- **Markov property** sugli stati nascosti  
- **conditional independence** delle osservazioni dato lo stato corrente

Formalmente:

- proprietà di Markov del primo ordine  
$P(Z_t \mid Z_{1:t-1}) = P(Z_t \mid Z_{t-1})$

- indipendenza condizionata delle osservazioni  
$P(X_t \mid Z_{1:t},X_{1:t-1}) = P(X_t \mid Z_t)$

Questo implica che lo stato corrente dipende solo dallo stato precedente e che ogni osservazione dipende solo dallo stato latente nello stesso tempo.

Il modello può essere rappresentato come un [[graphical model]] dinamico:

$$
Z_1 \rightarrow Z_2 \rightarrow Z_3 \rightarrow \dots \rightarrow Z_T
$$

$$
Z_t \rightarrow X_t
$$

Questa struttura induce una fattorizzazione della distribuzione congiunta della sequenza:

$$
P(X_{1:T}, Z_{1:T})
=
P(Z_1)
\prod_{t=2}^{T} P(Z_t \mid Z_{t-1})
\prod_{t=1}^{T} P(X_t \mid Z_t)
$$

dove:
- $P(Z_1)$ è la **distribuzione iniziale degli stati**
- $P(Z_t \mid Z_{t-1})$ è la **transition distribution**
- $P(X_t \mid Z_t)$ è la **emission distribution**

In forma parametrica il modello è definito da tre componenti:

- distribuzione iniziale  
$\pi_i = P(Z_1 = i)$

- matrice di transizione tra stati  
$A_{ij} = P(Z_t = j \mid Z_{t-1} = i)$

- distribuzione di emissione  
$B_j(x) = P(X_t = x \mid Z_t = j)$

Le Hidden Markov chains sono quindi [[latent variable models|modelli generativi]] per sequenze temporali in cui la dipendenza temporale è modellata tramite una catena di Markov sugli stati latenti mentre le osservazioni sono generate da tali stati. :contentReference[oaicite:0]{index=0}