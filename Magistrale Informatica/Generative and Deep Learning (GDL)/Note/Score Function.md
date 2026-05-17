---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Score-based models
SubTopic:
---
# Score Function
---

La **score function** di una distribuzione continua $p(x)$ è il gradiente della log-densità rispetto al dato $x$:
$$
s(x) = \nabla_x \log p(x)
$$

Intuitivamente, lo score indica la direzione locale in cui la log-densità cresce più rapidamente. Se $x$ si trova in una regione poco probabile ma vicina alla distribuzione dei dati, lo score punta verso regioni a maggiore probabilità.

## Interpretazione

La log-densità $\log p(x)$ è alta nelle zone in cui i dati sono più probabili. Il suo gradiente:
$$
\nabla_x \log p(x)
$$

descrive quindi un [[Campo vettoriale|campo vettoriale]] nello spazio dei dati: a ogni punto $x$ associa una direzione di salita della log-probabilità.

Questo è utile perché permette di ragionare sulla distribuzione senza dover conoscere necessariamente il valore normalizzato di $p(x)$ in modo esplicito. In molti modelli generativi è più accessibile imparare una direzione locale verso la densità alta che modellare direttamente tutta la densità.

## Collegamento con i Denoising Autoencoders

Nei [[Denoising Autoencoders (DAE)]], per rumore gaussiano piccolo, lo spostamento prodotto dalla ricostruzione è proporzionale allo score.

Se:
$$
\hat{x} = x + \epsilon
$$

con:
$$
\epsilon \sim \mathcal{N}(0, \sigma^2 I)
$$

allora il denoising appreso soddisfa, sotto opportune ipotesi:
$$
g_{\phi}(f_{\theta}(\hat{x}))
=
\mathbb{E}[x \mid \hat{x}]
$$

e:
$$
\mathbb{E}[x \mid \hat{x}]
=
\hat{x}
+
\sigma^2
\nabla_{\hat{x}} \log p(\hat{x})
$$

Quindi:
$$
\frac{
g_{\phi}(f_{\theta}(\hat{x})) - \hat{x}
}{
\sigma^2
}
=
\nabla_{\hat{x}} \log p(\hat{x})
$$

In questa lettura, il DAE impara un campo vettoriale che riporta punti rumorosi verso regioni più probabili della distribuzione dei dati.

## Limite

Nel caso dei DAE, la stima dello score è locale: viene imparata vicino ai punti di training e alle loro perturbazioni rumorose. Non definisce automaticamente una densità globale affidabile su tutto lo spazio.

Questo collegamento motiva i modelli generativi basati direttamente su score e denoising, come i diffusion models.
