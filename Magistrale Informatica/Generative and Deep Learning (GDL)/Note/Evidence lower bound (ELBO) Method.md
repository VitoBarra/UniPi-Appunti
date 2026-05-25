---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Evidence lower bound (ELBO) method
---
L'**Evidence Lower Bound**, o **ELBO**, è un lower bound trattabile della [[Maximum Liklehood learning|log-likelihood]] marginale, cioe della **observed-data log-likelihood**, di un [[Latent or hidden Model|modello a variabili latenti]] in cui il posteriore non puo essere calcolato.

L'ELBO si puo vedere come una **estensione variazionale** della [[Expectation Maximization (EM) Method|Expectation Maximization]]. Infatti, nell'[[Expectation Maximization (EM) Method|EM esatta]] l'**E-step** richiede di calcolare il [[Formula di Bayes|posteriore]] vero $\mathcal{P}(z \mid x,\theta)$; quando questo posteriore non e **trattabile**, non si puo applicare direttamente EM, quindi si ottimizza un **lower bound** trattabile della **observed-data log-likelihood** $\log \mathcal{P}(x \mid \theta)$ chiamato **Evidence Lower Bound** (**ELBO**).

L'idea di base e generale: si vuole massimizzare una funzione difficile $f(\theta)$ che, in questo contesto, coincide con la **observed-data log-likelihood** $$f(\theta)=\log \mathcal{P}(x \mid \theta)$$Se questa funzione non e trattabile direttamente, si cerca una funzione ausiliaria piu semplice $Q(\theta)$ tale che $$f(\theta)\geq Q(\theta)\quad \forall \theta$$Massimizzare $$Q(\theta)$$non significa in generale risolvere esattamente il problema originale, ma fornisce comunque un'approssimazione utile, perche vale $$\max_\theta f(\theta)\geq \max_\theta Q(\theta)$$Ancora meglio, invece di considerare un singolo lower bound, si puo considerare una **famiglia di lower bound** $$\mathcal{Q}=\{Q_1,Q_2,Q_3,\dots\}$$ e cercare il migliore all'interno di questa famiglia. In questo modo si ottiene una approssimazione piu flessibile, perche $$\max_\theta f(\theta)\geq \max_{Q\in\mathcal{Q}}\max_\theta Q(\theta)$$
![[IMG - Evidence lower bound (ELBO).png]]
Nel caso dell'ELBO, questa famiglia di bound viene costruita introducendo una distribuzione ausiliaria o **distribuzione variazionale**.


Per fare cio si introduce una **distribuzione variazionale** $Q(z \mid \phi)$, che approssima il [[Formula di Bayes|posteriore]] vero $\mathcal{P}(z \mid x,\theta)$. Inserendola nella **observed-data log-likelihood** e moltiplicando e dividendo per $Q(z \mid \phi)$ nei punti in cui $Q(z \mid \phi)>0$, si ottiene:

Nel caso continuo, $$\log \mathcal{P}(x \mid \theta)=\log \int \frac{Q(z \mid \phi)}{Q(z \mid \phi)}\mathcal{P}(x,z \mid \theta)\,dz$$Nel caso discreto vale in modo del tutto analogo, sostituendo l'integrale con una sommatoria: $$\log \mathcal{P}(x \mid \theta)=\log \sum_z \frac{Q(z \mid \phi)}{Q(z \mid \phi)}\mathcal{P}(x,z \mid \theta)$$Quindi, in forma compatta, vale $$\log \mathcal{P}(x\mid \theta)=\log \mathbb{E}_{z\sim Q(z \mid \phi)}\left[\frac{\mathcal{P}(x,z \mid \theta)}{Q(z \mid \phi)}\right]$$


Poiché il logaritmo è una funzione concava, dalla [[Jensen inequality]] vale $$\log \mathbb{E}_Q[Y]\geq \mathbb{E}_Q[\log Y]$$
![[IMG - Jensen inequality funzione logaritmo.png]]

Applicandola con $Y=\cfrac{\mathcal{P}(x,z \mid \theta)}{Q(z \mid \phi)}$ si ottiene $$\log \mathcal{P}(x \mid \theta)\geq \mathbb{E}_Q\left[\log \frac{\mathcal{P}(x,z \mid \theta)}{Q(z \mid \phi)}\right]$$ cioè $$\log \mathcal{P}(x \mid \theta)\geq \mathbb{E}_Q[\log \mathcal{P}(x,z \mid \theta)]-\mathbb{E}_Q[\log Q(z \mid \phi)]$$

Il membro destro è l'**ELBO**: $$\mathcal{L}(x,\theta,\phi)=\mathbb{E}_Q[\log \mathcal{P}(x,z \mid \theta)]+H(Q)$$ dove $H(Q)=-\mathbb{E}_Q[\log Q(z \mid \phi)]$ è l'[[Entropia|entropia]] della distribuzione variazionale.

Il termine $\mathbb{E}_Q[\log \mathcal{P}(x,z \mid \theta)]$ è la **complete-data log-likelihood attesa**: misura quanto il modello generativo assegna alta probabilità alla coppia $(x,z)$, mediando rispetto alla distribuzione approssimante $Q$. Il termine di entropia $H(Q)$ impedisce a $Q$ di diventare troppo deterministica se i dati e il modello non lo giustificano.


Per capire quanto questo lower bound sia buono, si considera direttamente la diffdeverenza $$\log \mathcal{P}(x \mid \theta)-\mathcal{L}(x,\theta,\phi)$$Ora si introduce $Q(z \mid \phi)$ per [[FJD - Marginalizzazione|marginalizzazione]] in $\log \mathcal{P}(x \mid \theta)$ e applicando la formula di [[Formula di Bayes|Bayes]] si ha che $$
\begin{align}
\log \mathcal{P}(x \mid \theta)-\mathcal{L}(x,\theta,\phi)
&=
\int Q(z \mid \phi)\log \mathcal{P}(x \mid \theta)\,dz-\int Q(z \mid \phi)\log \frac{\mathcal{P}(x,z \mid \theta)}{Q(z \mid \phi)}\,dz
\\
&=
\int Q(z \mid \phi)\left[\log \mathcal{P}(x \mid \theta)-\log \frac{\mathcal{P}(x,z \mid \theta)}{Q(z \mid \phi)}\right]dz
\\
&=
\int Q(z \mid \phi)\log \cfrac{\mathcal{P}(x \mid \theta)}{\mathcal{P}(x\mid z,  \theta)\mathcal{P}(z\mid \theta)}Q(z \mid \phi)dz
\\
(\text{bayes formula})&=
\int Q(z \mid \phi)\log \cfrac{Q(z \mid \phi)}{\mathcal{P}(z \mid x,\theta)}dz \\
 & =\mathbb{E}_{Q(z \mid \phi)}\left[\log \frac{Q(z \mid \phi)}{\mathcal{P}(z \mid x,\theta)}\right] 
\end{align}
$$che è definizione di [[kullback-Leibler (KL) Divergence|KL divergence]] si ha quindi che  
$$\log \mathcal{P}(x \mid \theta)-\mathcal{L}(x,\theta,\phi)=KL(Q(z \mid \phi) \Vert \mathcal{P}(z \mid x,\theta))$$
Quindi la decomposizione finale e esatta è$$\log \mathcal{P}(x \mid \theta)=\mathcal{L}(x,\theta,\phi)+KL(Q(z \mid \phi)\Vert \mathcal{P}(z \mid x,\theta))$$

Dato che la [[kullback-Leibler (KL) Divergence|KL divergence]] è sempre non negativa, l'ELBO è sempre un lower bound: $$\log \mathcal{P}(x \mid \theta)\geq \mathcal{L}(x,\theta,\phi)$$Inoltre, scelte diverse di $Q(z \mid \phi)$ producono lower bound diversi, e la bonta del bound dipende da quanto $Q(z \mid \phi)$ e vicina al posteriore vero $\mathcal{P}(z \mid x,\theta)$ in termini di KL divergence. Il bound diventa stretto quando la distribuzione variazionale coincide con il posteriore vero: $$Q(z \mid \phi)=\mathcal{P}(z \mid x,\theta)$$ In quel caso il termine di KL si annulla e l'ELBO coincide con la **observed-data log-likelihood**.

Questa relazione permette anche di riscrivere l'ELBO come $$\mathcal{L}(x,\theta,\phi)=\log \mathcal{P}(x \mid \theta)-KL(Q(z \mid \phi)\Vert \mathcal{P}(z \mid x,\theta))$$Da questa forma si vede che, per ogni $\theta$ fissato, massimizzare l'ELBO rispetto a $Q(z \mid \phi)$ equivale a rendere $Q(z \mid \phi)$ il piu possibile vicina al posteriore vero in termini di [[kullback-Leibler (KL) Divergence|KL divergence]].

Quindi l'inferenza variazionale puo essere vista in due modi equivalenti:
1. come **massimizzazione di un lower bound** trattabile, cioe l'ELBO
2. come **minimizzazione della distanza** $KL(Q(z \mid \phi)\Vert \mathcal{P}(z \mid x,\theta))$  tra distribuzione variazionale e posteriore vero

Seguendo questa idea, l'ottimizzazione variazionale alterna tipicamente due sottoproblemi:
1. **E-step variazionale**: per parametri generativi fissati $\theta^{(k)}$, si aggiorna la distribuzione variazionale risolvendo $$\phi^{(k)}=\arg\max_\phi \mathcal{L}(x,\theta^{(k)},\phi)$$
2. In modo equivalente, lo stesso **E-step variazionale** puo essere visto come $$\phi^{(k)}=\arg\min_\phi KL(Q(z \mid \phi)\Vert \mathcal{P}(z \mid x,\theta^{(k)}))$$
3. **M-step**: fissata la distribuzione variazionale, si aggiornano i parametri generativi risolvendo $$\theta^{(k)}=\arg\max_\theta \mathcal{L}(x,\theta,\phi^{(k)})$$

Questa seconda vista e spesso concettualmente piu chiara, ma nella pratica il calcolo esplicito della KL rispetto al posteriore vero non sempre e disponibile in forma chiusa. Per questo, molto spesso si lavora direttamente massimizzando l'ELBO, oppure si usano approssimazioni ulteriori come metodi di campionamento.

![[IMG - Evidence lower bound (ELBO) Method distanze.png]]
