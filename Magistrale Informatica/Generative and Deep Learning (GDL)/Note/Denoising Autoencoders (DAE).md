---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Autoencoders
SubTopic:
---

# Denoising Autoencoders (DAE)
---
I **Denoising Autoencoders** sono una variante degli [[Autoencoders (AE)|autoencoders]] in cui il modello riceve in input una versione corrotta del dato, ma deve ricostruire il dato pulito.

L'idea è usare la corruzione dell'input come vincolo: il modello non può limitarsi a copiare ciò che riceve, perché l'input contiene rumore. Deve invece imparare la struttura stabile dei dati.

Dato un esempio pulito $x$, si costruisce una versione corrotta:$$\hat{x} = x + \epsilon  \quad\epsilon \sim \mathcal{N}(0, \sigma^2 I)$$L'**encoder** $f_\theta$ riceve $\hat{x}$ e costruisce una rappresentazione latente $z$: $$z = f_{\theta}(\hat{x})$$il **decoder** $g_\theta$ produce una **ricostruzione**:$$\tilde{x} = g_{\phi}(z)$$Il target della ricostruzione resta il dato pulito $x$, non il dato corrotto $\hat{x}$:$$
\min_{\theta,\phi}\mathcal{L}\left(x,g_{\phi}(f_{\theta}(\hat{x}))\right)$$In questo modo il modello impara a rimuovere perturbazioni casuali e a riportare l'input verso una configurazione più **plausibile**.
![[IMG - Denoising autoencoders.png]]

Secondo la [[Manifold Hypothesis|manifold hypothesis]], i dati ad alta dimensionalità si trovano vicino a una manifold di dimensione più bassa. Un punto corrotto $\hat{x}$ può essere visto come un punto spostato fuori dalla manifold.

Il **denoising autoencoder** impara quindi una [[Campo vettoriale|campo vettoriale]] che riporta $\hat{x}$ verso una regione più probabile dei dati:$$\hat{x} \rightarrow \tilde{x}$$con $\tilde{x} \approx x$ La differenza:$$g_{\phi}(f_{\theta}(\hat{x})) - \hat{x}$$può essere interpretata come una direzione locale di ritorno verso la manifold.


## Collegamento con lo score

Il collegamento probabilistico passa attraverso la [[Score Function]], cioè il gradiente della log-densità dei dati:
$$
s(x) = \nabla_x \log p(x)
$$

Per rumore gaussiano piccolo, il campo di denoising appreso è collegato allo score della distribuzione: $$g_{\phi}(f_{\theta}(\hat{x}))=\mathbb{E}[x \mid \hat{x}]$$e:$$
\mathbb{E}[x \mid \hat{x}]=\hat{x}+\sigma^2\nabla_{\hat{x}} \log p(\hat{x})$$Quindi:$$\frac{g_{\phi}(f_{\theta}(\hat{x})) - \hat{x}}{\sigma^2}=\nabla_{\hat{x}} \log p(\hat{x})$$In forma intuitiva, lo spostamento prodotto dalla ricostruzione punta verso zone a maggiore densità di probabilità.

## Limite

Questa stima dello score è locale: viene imparata intorno ai punti di training e alle loro perturbazioni rumorose. Non definisce necessariamente una densità globale affidabile su tutto lo spazio.

Questo limite motiva modelli generativi latenti più regolarizzati, come i [[Variational Autoencoder (VAE)|Variational Autoencoders]], e modelli generativi basati direttamente su score e denoising.



### Interpretazione come modello probabilistico

Un **Denoising Autoencoder** può essere interpretato come un modello probabilistico che impara una distribuzione condizionata di denoising:
$$
P(x \mid \hat{x})
$$

dove $\hat{x}$ è il dato corrotto e $x$ è il dato pulito da ricostruire.

Dal punto di vista deterministico, il training minimizza il **Mean Squared Error** tra il dato pulito e la ricostruzione:
$$
\mathbb{E}_{x,\hat{x}}
\left[
\left\|
x - g_{\phi}(f_{\theta}(\hat{x}))
\right\|_2^2
\right]
$$

Sotto ipotesi gaussiane sulla distribuzione di ricostruzione, minimizzare l'MSE è equivalente a massimizzare una log-likelihood condizionata. Infatti, se il decoder definisce una distribuzione:
$$
P_{\phi}(x \mid z)
$$

con:
$$
z = f_{\theta}(\hat{x})
$$

allora l'obiettivo può essere scritto come:
$$
\max_{\theta,\phi}
\mathbb{E}_{x,\hat{x}}
\left[
\log P_{\phi}(x \mid z = f_{\theta}(\hat{x}))
\right]
$$

Quindi il DAE non impara solo una funzione di ricostruzione, ma può essere letto come un modello che assegna alta probabilità al dato pulito $x$ dato il corrispondente input rumoroso $\hat{x}$.

disegnata come [[Bayesian network|Bayesian network]]
![[IMG - Denoising Autoencoders Bayesian network.png]]
