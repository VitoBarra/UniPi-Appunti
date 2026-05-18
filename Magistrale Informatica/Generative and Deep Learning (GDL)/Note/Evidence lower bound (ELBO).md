---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Evidence lower bound (ELBO)
---
L'**Evidence Lower Bound**, o **ELBO**, è un lower bound trattabile della [[Stima Parametrica - Maximum Liklehood|log-likelihood]] marginale di un [[Latent Model|modello a variabili latenti]].

In un modello latente si osserva $x$, ma si introduce una variabile non osservata $z$ che spiega la struttura generativa dei dati. La probabilità marginale del dato si ottiene integrando la variabile latente: $$p(x \mid \theta)=\int p(x,z \mid \theta)\,dz$$ quindi l'obiettivo di massima likelihood è: $$\log p(x \mid \theta)=\log \int p(x,z \mid \theta)\,dz$$
Il problema è che questo integrale è spesso intrattabile. Per renderlo ottimizzabile si introduce una distribuzione variazionale $q(z \mid \phi)$, che approssima il posteriore vero $p(z \mid x,\theta)$. Moltiplicando e dividendo per $q(z \mid \phi)$ nei punti in cui $q(z \mid \phi)>0$: $$\log p(x \mid \theta)=\log \int q(z \mid \phi)\frac{p(x,z \mid \theta)}{q(z \mid \phi)}\,dz=\log \mathbb{E}_q\left[\frac{p(x,z \mid \theta)}{q(z \mid \phi)}\right]$$
Poiché il logaritmo è una funzione concava, dalla [[Jensen inequality]] vale: $$\log \mathbb{E}_q[Y]\geq \mathbb{E}_q[\log Y]$$![[IMG - Jensen inequality funzione logaritmo.png]]

Applicandola con $Y=\cfrac{p(x,z \mid \theta)}{q(z \mid \phi)}$ si ottiene: $$\log p(x \mid \theta)\geq \mathbb{E}_q\left[\log \frac{p(x,z \mid \theta)}{q(z \mid \phi)}\right]$$ cioè: $$\log p(x \mid \theta)\geq \mathbb{E}_q[\log p(x,z \mid \theta)]-\mathbb{E}_q[\log q(z \mid \phi)]$$

Il membro destro è l'**ELBO**: $$\mathcal{L}(x,\theta,\phi)=\mathbb{E}_q[\log p(x,z \mid \theta)]+H(q)$$ dove $H(q)=-\mathbb{E}_q[\log q(z \mid \phi)]$ è l'entropia della distribuzione variazionale.

Il termine $\mathbb{E}_q[\log p(x,z \mid \theta)]$ è la **complete-data log-likelihood attesa**: misura quanto il modello generativo assegna alta probabilità alla coppia $(x,z)$, mediando rispetto alla distribuzione approssimante $q$. Il termine di entropia $H(q)$ impedisce a $q$ di diventare troppo deterministica se i dati e il modello non lo giustificano.

## Decomposizione esatta
La log-likelihood marginale si può decomporre come: $$\log p(x \mid \theta)=\mathcal{L}(x,\theta,\phi)+KL(q(z \mid \phi)\Vert p(z \mid x,\theta))$$
Dato che la [[kullback-Leibler (KL) Divergence|KL divergence]] è sempre non negativa, l'ELBO è sempre un lower bound: $$\mathcal{L}(x,\theta,\phi)\leq \log p(x \mid \theta)$$
Il bound diventa stretto quando la distribuzione variazionale coincide con il posteriore vero: $$q(z \mid \phi)=p(z \mid x,\theta)$$ In quel caso il termine di KL si annulla e l'ELBO coincide con la log-likelihood marginale.

## Perché è utile

L'ELBO sostituisce un obiettivo difficile, $\log p(x \mid \theta)$, con un obiettivo più trattabile da ottimizzare. Questo permette di addestrare modelli a variabili latenti anche quando l'inferenza esatta sul posteriore $p(z \mid x,\theta)$ non è disponibile.

In pratica, ottimizzare l'ELBO significa fare due cose insieme: migliorare i parametri generativi $\theta$ affinché spieghino meglio i dati e migliorare i parametri variazionali $\phi$ affinché $q(z \mid \phi)$ approssimi meglio il posteriore vero.
