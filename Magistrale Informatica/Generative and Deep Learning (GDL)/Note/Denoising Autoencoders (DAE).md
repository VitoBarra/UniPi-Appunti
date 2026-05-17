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

Dato un esempio pulito $x$, si costruisce una versione corrotta:
$$
\hat{x} = x + \epsilon
$$
comunemente si assume che
$$
\epsilon \sim \mathcal{N}(0, \sigma^2 I)
$$
ovvero che il rumore sia [[Variabili Aleatorie Notevoli - Gaussiana|gaussiano]]. In questo caso il processo di corruzione può essere scritto come:
$$
C(\hat{x} \mid x) = \mathcal{N}(\hat{x} \mid x, \sigma^2 I)
$$
dove $C(\hat{x} \mid x)$ rappresenta la distribuzione con cui si genera l'input rumoroso $\hat{x}$ a partire dal dato pulito $x$. 
In pratica, fissato $x$, si campiona un punto attorno a esso da una gaussiana centrata in $x$ con varianza $\sigma^2$ uguale in tutte le direzioni, $\sigma^2$ controlla l'intensità della corruzione: 
- se è piccolo, le perturbazioni sono locali; 
- se è grande, l'input viene spostato più lontano dal punto originale.


L'**encoder** $f_\theta$ riceve $\hat{x}$ e costruisce una rappresentazione latente $z$:
$$
z = f_{\theta}(\hat{x})
$$
il **decoder** $g_\phi$ produce una **ricostruzione**:
$$
\tilde{x} = g_{\phi}(z)
$$
Il target della ricostruzione resta il dato pulito $x$, non il dato corrotto $\hat{x}$:
$$
\min_{\theta,\phi}\mathcal{L}\left(x,g_{\phi}(f_{\theta}(\hat{x}))\right)
$$
In questo modo il modello impara a rimuovere perturbazioni casuali e a riportare l'input verso una configurazione più **plausibile**.
![[IMG - Denoising autoencoders.png]]
Secondo la [[Manifold Hypothesis|manifold hypothesis]], i dati ad alta dimensionalità si trovano vicino a una manifold di dimensione più bassa. Un punto corrotto $\hat{x}$ può essere visto come un punto spostato fuori dalla manifold.

Il **denoising autoencoder** impara quindi un [[Campo vettoriale|campo vettoriale]] che riporta $\hat{x}$ verso una regione più probabile dei dati:
$$
\hat{x} \rightarrow \tilde{x}
$$
con $\tilde{x} \approx x$. La differenza
$$
g_{\phi}(f_{\theta}(\hat{x})) - \hat{x}
$$
può essere interpretata come una direzione locale di ritorno verso la manifold.


## Interpretazione probabilistica
Un **Denoising Autoencoder** può essere letto in chiave [[Modelli Probabilistici|probabilistica]] come un modello che, dato il campione corrotto $\hat{x}$ campionato dal processo di corruzione $C(\hat{x}\mid x)$, produce una ricostruzione
$$
\tilde{x} = g_{\phi}(f_{\theta}(\hat{x}))
$$
del dato pulito $x$. Scegliendo come loss la $\mathrm{MSE}$, il training equivale a minimizzare:
$$
\mathcal{L}(x,\tilde{x}) = \|x-\tilde{x}\|_2^2
$$
e quindi:
$$
\min_{\theta,\phi}\mathbb{E}_{x,\hat{x}}
\left[
\mathcal{L}\left(x,g_{\phi}(f_{\theta}(\hat{x}))\right)
\right]
$$
dove l'aspettativa è rispetto a $x \sim p_{\mathrm{data}}(x)$ e $\hat{x} \sim C(\hat{x}\mid x)$. La relazione probabilistica di interesse è quindi la [[Probabilita condizionata|condizionata]]:
$$
\mathcal{P}(x \mid \hat{x})
$$
Disegnata come [[Bayesian network|Bayesian network]] diventa:
![[IMG - Denoising Autoencoders Bayesian network.png]]
Il fatto fondamentale è che il **minimizzatore ottimo** di questa loss, per ogni $\hat{x}$ fissato, è:
$$
g_{\phi^*}(f_{\theta^*}(\hat{x})) = \mathbb{E}[x \mid \hat{x}]
$$
ovvero la media dei possibili valori puliti $x$ compatibili con l'osservazione corrotta $\hat{x}$. Quindi un DAE addestrato con MSE non impara necessariamente l'intera distribuzione condizionata $\mathcal{P}(x \mid \hat{x})$, ma la sua **media condizionata**.

Se si introduce una formulazione probabilistica del decoder e si assume una **likelihood [[Variabili Aleatorie Notevoli - Gaussiana|gaussiana]] condizionata**:
$$
\mathcal{P}_{\phi}(x \mid z) = \mathcal{N}(x \mid \mu_{\phi}(z), \sigma_r^2 I)
$$
allora
$$
\log \mathcal{P}_{\phi}(x \mid z)
=
-\frac{1}{2\sigma_r^2}\|x-\mu_{\phi}(z)\|_2^2 + C
$$
per una costante $C$ indipendente dai parametri. Di conseguenza, massimizzare la log-likelihood condizionata
$$
\mathbb{E}_{x,\hat{x}}\left[\log \mathcal{P}_{\phi}(x \mid z=f_{\theta}(\hat{x}))\right]
$$
equivale, a meno di costanti additive e fattori di scala, a minimizzare la MSE:
$$
\mathbb{E}_{x,\hat{x}}\left[\|x-\mu_{\phi}(f_{\theta}(\hat{x}))\|_2^2\right]
$$
Questa non è un'ipotesi sul fatto che i dati siano globalmente gaussiani: l'assunzione è solo che, **dato il codice latente $z$**, l'errore di ricostruzione venga modellato localmente come rumore gaussiano isotropo.

Il collegamento più profondo con la probabilità passa però attraverso la [[Score Function]]. Se la corruzione è gaussiana:
$$
\hat{x} = x + \epsilon,
\qquad
\epsilon \sim \mathcal{N}(0,\sigma^2 I)
$$
allora, per la [[Formula di Tweedie|formula di Tweedie]], la media condizionata ottima soddisfa:
$$
g_{\phi^*}(f_{\theta^*}(\hat{x})) = \mathbb{E}[x \mid \hat{x}] = \hat{x} + \sigma^2 \nabla_{\hat{x}} \log p_{\hat{x}}(\hat{x})
$$
dove $p_{\hat{x}}$ è la densità del dato **corrotto**, ottenuta convolvendo la distribuzione dei dati con il rumore gaussiano. Sostituendo il minimizzatore ottimo:
$$
\frac{g_{\phi^*}(f_{\theta^*}(\hat{x})) - \hat{x}}{\sigma^2}
=
\nabla_{\hat{x}} \log p_{\hat{x}}(\hat{x})
$$
e quindi, in pratica:
$$
\frac{g_{\phi}(f_{\theta}(\hat{x})) - \hat{x}}{\sigma^2}
\approx
\nabla_{\hat{x}} \log p_{\hat{x}}(\hat{x})
$$
In altre parole, il [[campo vettoriale|campo vettoriale]] appreso dal modello approssima la [[Score Function|score function]] della **distribuzione rumorosa**. Per rumore piccolo, questa score è una buona approssimazione locale della score della distribuzione dei dati, e quindi definisce una direzione che riporta il punto corrotto verso regioni più dense e più plausibili del [[Manifold Hypothesis|manifold]] dei dati.
![[IMG - autoencoders come learning di manifold.png]]
![[GIF - Sample from encoder.gif]]

## Limite
Questa stima dello score è locale: viene imparata intorno ai punti di training e alle loro perturbazioni rumorose. Non definisce necessariamente una densità globale affidabile su tutto lo spazio.
![[IMG - Denoising Autoencoders (DAE) limiti.png]]
Questo limite motiva modelli generativi latenti più regolarizzati, come i [[Variational Autoencoder (VAE)|Variational Autoencoders]], e modelli generativi basati direttamente su score e denoising.
