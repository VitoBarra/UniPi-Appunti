---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Variational Autoencoder
SubTopic:
---
# Variational Autoencoder (VAE)
---
I **Variational Autoencoders** (**VAE**) trasformano l'idea degli [[Autoencoders (AE)|autoencoders]] in un [[Latent Model|modello latente]] [[Modelli Probabilistici|probabilistico]] e [[Modelli Generativi|generativo]].

In un VAE, il codice $z$ latente non è un singolo vettore deterministico, ma una [[Variabili Aleatorie (Casuali)|variabile aleatoria]].
Il modello definisce:
- un **prior** sulle variabili latenti, di solito $\mathcal{P}(z) = \mathcal{N}(0, I)$;
- un **encoder variazionale** $q_{\phi}(z \mid x)$ che approssima il posterior;
- un **decoder probabilistico** $\mathcal{P}_{\theta}(x \mid z)$.
Il modello generativo è:
$$
\begin{array}{}
z \sim \mathcal{P}(z) \\
x \sim \mathcal{P}_{\theta}(x \mid z)
\end{array}
$$

Quindi, per [[FJD - Marginalizzazione|marginalizzazione]], la distribuzione congiunta del modello generativo è:
$$
\mathcal{P}_{\theta}(x, z) = \mathcal{P}_{\theta}(x \mid z)\mathcal{P}(z)
$$
Le variabili latenti $z$ rappresentano **fattori di variazione** del dato, ad esempio identità, stile, rotazione, posa o dimensione. Nella [[Bayesian network|Bayesian network]] della figura, $z$ è il nodo latente da cui dipende il nodo osservato $x$, quindi la fattorizzazione è proprio:
$$
\mathcal{P}_{\theta}(x, z) = \mathcal{P}_{\theta}(x \mid z)\mathcal{P}(z)
$$

![[IMG - Variational Autoencoder combined.png]]

Per generare un modello esplicito sui dati, si vorrebbe calcolare:
$$
\mathcal{P}_{\theta}(x)
=
\int \mathcal{P}_{\theta}(x \mid z)\mathcal{P}(z)\,dz
$$

e massimizzare la log-likelihood:
$$
\log \mathcal{P}_{\theta}(x)
=
\log
\int \mathcal{P}_{\theta}(x \mid z)\mathcal{P}(z)\,dz
$$

Il problema è che questo [[Integrali|integrale]] è di solito intrattabile quando il decoder è una [[Reti Neurali (NN)|rete neurale]] e $z$ è continuo.

Anche il posterior vero:
$$\mathcal{P}_{\theta}(z \mid x)= \frac{\mathcal{P}_{\theta}(x \mid z)\mathcal{P}(z)}{\mathcal{P}_{\theta}(x)}$$
è intrattabile, perché richiede proprio la marginal likelihood $\mathcal{P}_{\theta}(x)$ al denominatore.

![[IMG - contrattive vs variational AE.png]]

Il VAE introduce una distribuzione trattabile:
$$
q_{\phi}(z \mid x)
$$

che approssima il posterior vero $p_{\theta}(z \mid x)$. Questa è la parte **variazionale** del modello: invece di calcolare il posterior esatto, si sceglie una famiglia parametrica semplice e la si ottimizza.

Nel VAE standard si usa una gaussiana diagonale:
$$
q_{\phi}(z \mid x)
=
\mathcal{N}
\left(
\mu_{\phi}(x),
(\sigma_{\phi}(x)^2I)
\right)
$$

L'encoder non produce direttamente $z$, ma i parametri della distribuzione:$$\mu_{\phi}(x), \sigma_{\phi}(x)$$Da questa distribuzione si campiona poi un valore latente $z$ da passare al decoder. ![[IMG - Architettura Variational Autoencoder (VAE).png]]

## Training

Dato che $\log p_{\theta}(x)$ è intrattabile, il VAE massimizza un lower bound chiamato [[Evidence lower bound (ELBO)|Evidence Lower Bound]]:
$$
\mathcal{L}(x;\theta,\phi)
=
\mathbb{E}_{q_{\phi}(z \mid x)}
\left[
\log p_{\theta}(x \mid z)
\right]
-
KL(q_{\phi}(z \mid x) \Vert p(z))
$$

Il primo termine è il **termine di ricostruzione**:
$$
\mathbb{E}_{q_{\phi}(z \mid x)}
\left[
\log p_{\theta}(x \mid z)
\right]
$$

e spinge il codice latente a contenere abbastanza informazione per spiegare o ricostruire $x$.

Il secondo termine è la **regolarizzazione KL**:
$$
KL(q_{\phi}(z \mid x) \Vert p(z))
$$

e spinge il posterior approssimato a rimanere vicino al prior. Questo evita che l'encoder collochi ogni input in regioni arbitrarie e scollegate dello spazio latente.

L'obiettivo introduce quindi un trade-off:
- ricostruire bene i dati;
- mantenere lo spazio latente compatibile con il prior da cui si vuole campionare.

Con prior standard:$$p(z) = \mathcal{N}(0, I)$$e posterior approssimato gaussiano diagonale:$$q_{\phi}(z \mid x)=\mathcal{N}(\mu, \operatorname{diag}(\sigma^2))$$la [[kullback-Leibler (KL) Divergence|KL divergence]] ha forma chiusa:$$KL(q_{\phi}(z \mid x) \Vert p(z))=\frac{1}{2}\sum_j\left(\mu_j^2+\sigma_j^2-\log \sigma_j^2-1\right)$$Questo rende il termine di regolarizzazione calcolabile direttamente durante il training.

## Reparameterization Trick

Il training richiede di fare backpropagation attraverso il campionamento:
$$
z \sim q_{\phi}(z \mid x)
$$

ma campionare direttamente da una distribuzione che dipende dai parametri dell'encoder non è una operazione differenziabile nel modo standard.

Il **reparameterization trick** separa la parte casuale dai parametri:
$$
\epsilon \sim \mathcal{N}(0, I)
$$

$$
z = \mu_{\phi}(x) + \sigma_{\phi}(x) \odot \epsilon
$$

La casualità è tutta in $\epsilon$, che non dipende dai parametri. Il passaggio da $\mu_{\phi}(x)$ e $\sigma_{\phi}(x)$ a $z$ è invece deterministico e differenziabile, quindi si può usare la backpropagation.

La parte di ricostruzione dell'ELBO diventa:
$$
\mathbb{E}_{\epsilon \sim \mathcal{N}(0,I)}
\left[
\log p_{\theta}
\left(
x \mid
\mu_{\phi}(x) + \sigma_{\phi}(x) \odot \epsilon
\right)
\right]
$$
![[UniPi-Appunti/Magistrale Informatica/Generative and Deep Learning (GDL)/media/IMG - Variational Autoencoder (VAE).png]]

## Training e generazione
Durante il training:
1. l'encoder riceve $x$ e produce $\mu_{\phi}(x)$ e $\sigma_{\phi}(x)$;
2. si campiona $\epsilon \sim \mathcal{N}(0,I)$;
3. si costruisce $z = \mu_{\phi}(x) + \sigma_{\phi}(x) \odot \epsilon$;
4. il decoder calcola $p_{\theta}(x \mid z)$;
5. si massimizza l'ELBO.

In fase di generazione l'encoder non serve. Si campiona dal prior:
$$
z \sim \mathcal{N}(0,I)
$$

e si decodifica:
$$
\tilde{x} \sim p_{\theta}(x \mid z)
$$

oppure, usando direttamente l'output del decoder:
$$
\tilde{x} = g_{\theta}(z)
$$

Questa procedura funziona perché durante il training il termine KL ha regolarizzato gli encoder posterior verso lo stesso prior usato per generare.

## Conditional VAE

Un **Conditional VAE** (**CVAE**) aggiunge una condizione $y$, ad esempio una classe:
$$
q_{\phi}(z \mid x,y)
$$

$$
p_{\theta}(x \mid z,y)
$$

In generazione si campiona:
$$
z \sim \mathcal{N}(0,I)
$$

e si passa anche la condizione $y$ al decoder. In questo modo $y$ controlla il contenuto richiesto, mentre $z$ può rappresentare stile o variazioni non specificate.

## Interpretazione dello spazio latente

Il VAE produce uno spazio latente più regolare rispetto a un autoencoder classico:
- input simili tendono a essere mappati in regioni vicine;
- interpolare tra due punti latenti spesso produce transizioni continue;
- alcune direzioni latenti possono corrispondere a fattori di variazione;
- il termine KL evita che lo spazio latente sia frammentato.

Questo rende i VAE utili per representation learning, interpolazione, generazione condizionata e analisi dei fattori latenti.

## Limiti

I VAE hanno alcuni limiti importanti:
- l'ELBO è solo un lower bound della log-likelihood vera;
- la marginal likelihood rimane intrattabile;
- una gaussiana diagonale può essere troppo restrittiva come posterior approssimato;
- con decoder semplici e loss tipo MSE, le immagini generate possono risultare sfocate.

Per questo i VAE sono molto importanti per imparare spazi latenti strutturati, ma non sempre producono campioni visivamente nitidi come altri [[Modelli Generativi|modelli generativi]].
