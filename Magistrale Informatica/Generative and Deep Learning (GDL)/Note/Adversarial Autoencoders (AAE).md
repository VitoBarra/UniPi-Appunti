---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Adversarial Autoencoders
SubTopic:
---

# Adversarial Autoencoders (AAE)
---
Gli **Adversarial Autoencoders** (**AAE**) combinano la struttura degli [[Variational Autoencoder (VAE)|autoencoder variazionali]] con un meccanismo avversariale simile a quello delle [[Generative Adversarial Networks (GAN)|GAN]].

L'idea di base e imparare una rappresentazione latente $z$ che sia utile per ricostruire il dato, ma che allo stesso tempo abbia una distribuzione controllata. In questo modo il modello puo essere usato anche come [[Modelli Generativi|modello generativo]]: dopo il training si campiona $z$ da un prior scelto e lo si passa al decoder per generare nuovi esempi.

Un autoencoder standard contiene:
- **encoder** $f_{\theta}(x)$: mappa il dato osservato nello spazio latente;
- **decoder** $g_{\phi}(z)$: ricostruisce il dato a partire dalla rappresentazione latente.
Formalmente:$$z = f_{\theta}(x)\quad \tilde{x} = g_{\phi}(z)$$L'obiettivo di ricostruzione forza $\tilde{x}$ a essere vicino a $x$:$$\mathcal{L}_{rec}(x, \tilde{x})= d(x, g_{\phi}(f_{\theta}(x)))$$dove $d$ puo essere, ad esempio, un errore quadratico medio o una cross-entropy, a seconda del tipo di dato.
![[IMG - Adversarial autoencoder (AAE).png]]

## Regolarizzazione avversariale dello spazio latente

Negli AAE non basta ricostruire bene i dati. Si vuole anche che le codifiche prodotte dall'encoder seguano un prior scelto $p(z)$, ad esempio una [[Variabili Aleatorie Notevoli - Gaussiana|gaussiana standard]], una mixture di gaussiane o una distribuzione categorica.

Indichiamo con $q_{\theta}(z)$ la **distribuzione aggregata** delle codifiche prodotte dall'encoder quando $x$ varia sui dati:
$$
q_{\theta}(z)
= \int q_{\theta}(z \mid x)p_{\text{data}}(x)dx
$$

L'obiettivo della regolarizzazione e:
$$
q_{\theta}(z) \approx p(z)
$$

In un [[Variational Autoencoder (VAE)|Variational Autoencoder]] questa vicinanza viene tipicamente imposta tramite un termine di [[kullback-Leibler (KL) Divergence|KL divergence]]. Negli **Adversarial Autoencoders**, invece, viene imparata con un discriminatore nello spazio latente.

Il discriminatore $D_{\psi}(z)$ riceve due tipi di campioni:
- campioni veri dal prior: $z \sim p(z)$;
- codifiche prodotte dall'encoder: $z = f_{\theta}(x)$ con $x \sim p_{\text{data}}(x)$.

Il suo compito e distinguere se un punto latente proviene dal prior oppure dall'encoder. L'encoder, nella fase avversariale, viene aggiornato per ingannare il discriminatore, cioe per produrre codifiche indistinguibili dai campioni del prior.

## Training

Il training alterna due fasi principali.

1. **Reconstruction phase**: si aggiornano encoder e decoder minimizzando l'errore di ricostruzione.$$
\min_{\theta,\phi}
\mathbb{E}_{x \sim p_{\text{data}}}
\left[
\mathcal{L}_{rec}(x, g_{\phi}(f_{\theta}(x)))
\right]
$$
2. **Regularization phase**: si usa un training avversariale nello spazio latente.

Prima si aggiorna il discriminatore:$$
\max_{\psi}
\left[
\mathbb{E}_{z \sim p(z)}[\log D_{\psi}(z)]
+
\mathbb{E}_{x \sim p_{\text{data}}}
[\log(1 - D_{\psi}(f_{\theta}(x)))]
\right]
$$

Poi si aggiorna l'encoder per far classificare le sue codifiche come campioni del prior:
$$
\max_{\theta}
\mathbb{E}_{x \sim p_{\text{data}}}
[\log D_{\psi}(f_{\theta}(x))]
$$

Questa seconda parte e analoga alla loss non saturante del generatore nelle [[Generative Adversarial Networks (GAN)|GAN]]: l'encoder gioca il ruolo del generatore, ma genera punti nello spazio latente invece che direttamente dati osservabili.

```pseudo
\begin{algorithm}
\caption{Training di un Adversarial Autoencoder}
\begin{algorithmic}
    \For{numero di iterazioni di training}
        \State Campiona un minibatch di dati reali $\{x^{(1)}, \dots, x^{(m)}\}$
        \State Codifica i dati: $z^{(i)} = f_{\theta}(x^{(i)})$
        \State Ricostruisci: $\tilde{x}^{(i)} = g_{\phi}(z^{(i)})$
        \State Aggiorna encoder e decoder minimizzando la reconstruction loss
        \State Campiona un minibatch di punti latenti $\{z_p^{(1)}, \dots, z_p^{(m)}\}$ dal prior $p(z)$
        \State Aggiorna il discriminatore per distinguere $z_p$ da $f_{\theta}(x)$
        \State Aggiorna l'encoder per far classificare $f_{\theta}(x)$ come campione del prior
    \EndFor
\end{algorithmic}
\end{algorithm}
```

## Interpretazione

L'AAE separa due obiettivi:
- la **ricostruzione** mantiene informazione sul dato osservato;
- la **regolarizzazione avversariale** organizza lo spazio latente secondo una distribuzione scelta.

Il risultato e uno spazio latente campionabile: se $q_{\theta}(z)$ coincide bene con $p(z)$, allora un punto $z \sim p(z)$ dovrebbe cadere in una regione dello spazio latente che il decoder ha visto durante il training. Per generare un nuovo campione si usa:
$$
z \sim p(z)
$$

$$
\tilde{x} = g_{\phi}(z)
$$

Questo collega gli AAE all'idea di [[Latent or hidden Model]]: il dato osservato viene spiegato tramite variabili latenti, ma la forma dello spazio latente e controllata in modo avversariale.

## Differenza rispetto ai VAE

Sia gli AAE sia i VAE cercano di rendere lo spazio latente regolare e campionabile, ma lo fanno in modo diverso.

Nei **VAE** si ottimizza un obiettivo variazionale, cioe l'[[Evidence lower bound (ELBO) Method|ELBO]], che contiene:
- un termine di ricostruzione;
- un termine di KL tra posterior approssimato e prior.

Negli **AAE** il termine di KL viene sostituito da un discriminatore. Questo e utile quando si vuole imporre un prior per cui la KL e difficile da calcolare, non ha forma chiusa oppure e poco comoda da ottimizzare.

Esempi di prior possibili:
- gaussiana standard;
- mixture di gaussiane;
- variabili categoriche;
- prior empirici;
- fattorizzazioni supervisionate tra classe e stile.

![[IMG - AAE vs  VAE.png]]

## Perche usarli

Gli **Adversarial Autoencoders** sono utili quando si vuole mantenere la capacita di ricostruzione degli autoencoder, ma ottenere anche uno spazio latente con struttura generativa controllata.

Rispetto a un autoencoder standard, un AAE evita che lo spazio latente sia arbitrario e difficile da campionare. Rispetto a un VAE, permette di imporre prior piu flessibili usando un discriminatore, ma eredita anche alcune difficolta del training avversariale, come instabilita e sensibilita al bilanciamento tra encoder e discriminatore.





