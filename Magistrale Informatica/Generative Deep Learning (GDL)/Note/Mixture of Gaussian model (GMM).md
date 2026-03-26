---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Mixture of Gaussian model (GMM)
---
Il **Mixture of Gaussian model** (**GMM**) e un caso particolare di [[Mixture Models|mixture model]] in cui ciascuna componente appartiene alla famiglia delle [[Variabili Aleatorie Notevoli - Gaussiana|gaussiane]]. Il modello descrive la [[Distribuzione di probabilita|distribuzione di probabilita]] dei dati come combinazione pesata di $M$ densita gaussiane e introduce una [[Latent or hidden Model|variabile latente]] discreta $z_j$ che identifica la componente generatrice del dato $x_j$. Nella notazione delle slide i parametri sono raccolti in $\theta=(\pi,\mu,\sigma)$.

Si assume:
- $\mathbf{X} \in \mathbb{R}^d$ le osservazioni per questo modello
- $\pi_m\geq 0$ e $\sum_{m=1}^M \pi_m=1$, quindi $\pi=(\pi_1,\dots,\pi_M)$ e una [[Variabili Aleatorie Notevoli - Multinomiale|distribuzione multinomiale]]
- $z_j\in\{1,\dots,M\}$ con $\mathcal{P}(z_j=m\mid \pi)=\pi_m$
- [[Probabilita condizionata|condizionatamente]] a $z_j=m$, il dato $x_j$ osservato ha distribuzione [[Variabili Aleatorie Notevoli - Gaussiana|gaussiana]] $$\mathcal{P}(x_j\mid z_j=m)\sim\mathcal{N}(\mathbf{\mu}_m,\mathbf{\sigma}_m)$$La variabile $z_j$ seleziona quindi la componente gaussiana da cui viene estratto $x_j$.
La **distribuzione marginale** $\mathcal{P}(x)$ osservata si ottiene per [[FJD - Marginalizzazione|marginalizzazione]] della variabile latente da $\mathcal{P}(x,z)$ ![[IMG - Mixture of Gaussian model marginalizazzione.png]]

I parametri del modello sono quindi i coefficienti di mixing $\pi_m$, le medie $\mu_m$ e i parametri di dispersione $\sigma_m$ e in [[Bayesian network - Plate notation|plate notation]] il modello risulta:
![[IMG - Mixture of Gaussian model Plate notation.png]]

Il **GMM** rappresenta una densita multimodale come somma di componenti gaussiane. Ogni coefficiente $\pi_m$ misura il peso relativo della componente $m$, ogni media $\mu_m$ ne determina la posizione e ogni parametro $\sigma_m$ ne controlla la dispersione. La presenza della variabile latente rende il modello adatto a descrivere sottopopolazioni non osservabili direttamente.

## Derivazione della Complete Likelihood del dataset

Dato un **dataset** di [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite (IDD)|iid]] $\mathbf{X}=\{x_1,\dots,x_N\}$ per via del [[Indipendenza Stocastica|indipendenze]] delle $x_i$ la [[Formula di Bayes|likelihood]] osservata risulta$$\mathcal{L}(\theta\mid \mathbf{X})=\mathcal{P}(\mathbf{X}\mid \theta)=\prod_{j=1}^N \mathcal{P}(x_j\mid \theta)$$Poiche ogni osservazione dipende da una [[Latent or hidden Model|variabile latente]] $z_j$, per ogni dato si introduce la marginalizzazione$$\mathcal{P}(x_j\mid \theta)=\sum_{m=1}^M \mathcal{P}(x_j,z_j=m\mid \theta)$$e usando la [[Regola del prodotto|regola del prodotto]] e le [[Indipendenza Stocastica|dipendenze]] del modello,
$$
\mathcal{P}(x_j,z_j=m\mid \theta)=\mathcal{P}(z_j=m\mid \pi)\mathcal{P}(x_j\mid z_j=m,\mu,\sigma)=\pi_m\mathcal{P}(x_j\mid \mu_m,\sigma_m)
$$
Quindi la likelihood osservata diventa
$$
\mathcal{L}(\theta\mid \mathbf{X})=\prod_{j=1}^N \sum_{m=1}^M \pi_m\mathcal{P}(x_j\mid \mu_m,\sigma_m)
$$
La **log-likelihood osservata** si ottiene applicando il logaritmo alla likelihood osservata:
$$
\log \mathcal{L}(\theta\mid \mathbf{X})
=
\sum_{j=1}^N \log\left(\sum_{m=1}^M \pi_m\mathcal{P}(x_j\mid \mu_m,\sigma_m)\right)
$$
e non puo essere semplificata come somma dei logaritmi dei singoli termini, perche il logaritmo di una somma non e uguale alla somma dei logaritmi. Questa e la difficolta principale che impedisce una massimizzazione diretta della likelihood osservata.

Equivalentemente,
$$
\mathcal{P}(\mathbf{X}\mid \theta)=\sum_{\mathbf{Z}} \mathcal{P}(\mathbf{X},\mathbf{Z}\mid \theta)
$$
quindi questa e una **incomplete likelihood** o **observed-data likelihood**, perche riguarda solo i dati osservati $\mathbf{X}$ ed e ottenuta marginalizzando le variabili latenti $\mathbf{Z}$.


Per definire la complete likelihood $\mathcal{L}_c(\theta\mid \mathbf{X},\mathbf{Z})$ si introducono variabili indicatrici ausiliarie $\bar z_{jm}$ tali che
$$
\bar z_{jm}(z_j)=
\begin{cases}
1 & \text{se } z_j=m \\
0 & \text{altrimenti}
\end{cases}
$$
In pratica, $\bar z_{jm}=1$ significa che il campione $x_j$ e assegnato alla componente $m$, mentre $\bar z_{jm}=0$ significa che non lo e. $\bar z_{jm}(z_j)$ sono quindi [[Variabili Aleatorie (Casuali)|variabili aleatorie]] binarie dove $\mathcal{P}(\bar z_{jm}=1)=\mathcal{P}(z_j=m\mid x_j)$. 


Assumendo di conoscere il valore di ogni variabile $z_{jm}$ **allora** la complete likelihood assume allora la forma$$
\mathcal{L}_c(\theta\mid \mathbf{X},\mathbf{Z})=\prod_{j=1}^N \sum_{m=1}^M \bar z_{jm}\pi_m \mathcal{P}(x_j\mid \mu_m,\sigma_m)=\prod_{j=1}^N\prod_{m=1}^M\left(\pi_m \mathcal{P}(x_j\mid \mu_m,\sigma_m)\right)^{\bar z_{jm}}
$$In questo modo il contributo del termine $\pi_m\mathcal{P}(x_j\mid \mu_m,\sigma_m)$ alla likelihood è $\not=0$ solo per la componente effettivamente associata al dato.

Non si sta piu marginalizzando sulle variabili latenti: la likelihood e detta **completa** proprio perche le assegnazioni $\mathbf{Z}$ sono considerate note e compaiono esplicitamente nell'espressione.

e la complete log-likelihood diventa
$$
\log \mathcal{L}_c(\theta\mid \mathbf{X},\mathbf{Z})=\sum_{j=1}^N\sum_{m=1}^M \bar z_{jm}\log\left(\pi_m \mathcal{P}(x_j\mid \mu_m,\sigma_m)\right)
$$
Questa espressione e piu semplice da trattare perche separa i contributi delle diverse componenti.
La presenza del logaritmo di una somma impedisce una massimizzazione diretta con i metodi usuali di [[Stima Parametrica - Metodo di Massima Verosomiglianza|massima verosimiglianza]].

## Learning tramite Expectation massimization

La probabilità a posteriori che il dato $x_j$ sia stato generato dalla componente $m$ si ottiene con la [[Formula di Bayes|formula di Bayes]]:
$$
\mathcal{P}(z_j=m\mid x_j,\theta)=\frac{\pi_m\mathcal{P}(x_j\mid \mu_m,\sigma_m)}{\sum_{m'=1}^M \pi_{m'}\mathcal{P}(x_j\mid \mu_{m'},\sigma_{m'})}
$$
Queste quantita sono dette responsibilities e verificano
$$
\sum_{m=1}^M \mathcal{P}(z_j=m\mid x_j,\theta)=1
$$
Esse forniscono un'assegnazione soft dei dati alle componenti gaussiane.


L'apprendimento del GMM avviene tipicamente con l'algoritmo **Expectation-Maximization**.

Nel passo $E$ si calcolano le responsibilities
$$
\mathcal{P}(z_j=m\mid x_j,\theta^{(k)})=\frac{\pi_m^{(k)}\mathcal{P}(x_j\mid \mu_m^{(k)},\sigma_m^{(k)})}{\sum_{m'=1}^M \pi_{m'}^{(k)}\mathcal{P}(x_j\mid \mu_{m'}^{(k)},\sigma_{m'}^{(k)})}
$$
Poiche le variabili indicatrici sono binarie, il loro [[Variabili aleatoria - Valore atteso|valore atteso]] rispetto alla posterior coincide con la probabilita di appartenenza alla componente:
$$
\mathbb{E}[\bar z_{jm}\mid x_j,\theta^{(k)}]=\mathcal{P}(z_j=m\mid x_j,\theta^{(k)})
$$

Questo permette di definire la **funzione ausiliaria** di EM come valore atteso della complete log-likelihood rispetto alla distribuzione delle variabili latenti calcolata ai parametri correnti:
$$
Q(\theta\mid \theta^{(k)})=\mathbb{E}_{\mathcal{P}(Z\mid X,\theta^{(k)})}\left[\log \mathcal{L}_c(\theta\mid \mathbf{X},\mathbf{Z})\right]
$$
che nel caso del GMM diventa$$
Q(\theta\mid \theta^{(k)})=\sum_{j=1}^N\sum_{m=1}^M \mathcal{P}(z_j=m\mid x_j,\theta^{(k)})\log\left(\pi_m\mathcal{P}(x_j\mid \mu_m,\sigma_m)\right)
$$
Usando la proprietà $\log(ab)=\log a+\log b$, la funzione ausiliaria si puo decomporre in due gruppi di sommatorie:
$$
\begin{aligned}
Q(\theta\mid \theta^{(k)})
&=\sum_{j=1}^N\sum_{m=1}^M \mathcal{P}(z_j=m\mid x_j,\theta^{(k)})\log \pi_m \\
&\quad+\sum_{j=1}^N\sum_{m=1}^M \mathcal{P}(z_j=m\mid x_j,\theta^{(k)})\log \mathcal{P}(x_j\mid \mu_m,\sigma_m)
\end{aligned}
$$
Il primo termine dipende dai coefficienti di mixing $\pi_m$, mentre il secondo dipende dai parametri delle **componenti gaussiane**.

Nel passo M i parametri vengono aggiornati massimizzando $Q(\theta\mid \theta^{(k)})$ rispetto a $\theta$, cioe risolvendo$$\frac{\partial Q(\theta\mid \theta^{(k)})}{\partial \theta}=0$$tenendo pero conto del vincolo di normalizzazione sui coefficienti di mixing:$$\sum_{m=1}^M \pi_m=1$$Per il termine che dipende da $\pi_m$ si usa quindi il [[Metodo di ottimizzazione vincolata con moltiplicatori di Lagrange]], mentre i termini che dipendono da $\mu_m$ e $\sigma_m$ possono essere massimizzati separatamente per ogni componente.

Per comodità si definisce prima$$N_m=\sum_{j=1}^N \mathcal{P}(z_j=m\mid x_j,\theta^{(k)})$$che rappresenta il numero efficace di punti assegnati alla componente $m$.

La soluzione dei problemi di massimizzazione indipendenti rispetto a $\pi_m$, $\mu_m$ e $\sigma_m$ porta allora agli aggiornamenti
$$
\pi_m^{(k+1)}=\frac{N_m}{N}
$$
$$
\mu_m^{(k+1)}=\frac{1}{N_m}\sum_{j=1}^N \mathcal{P}(z_j=m\mid x_j,\theta^{(k)})x_j
$$
$$
\sigma_m^{(k+1)}=\sqrt{  \frac{1}{N_m}\sum_{j=1}^N \mathcal{P}(z_j=m\mid x_j,\theta^{(k)})(x_j-\mu_m^{(k+1)})^2 }
$$

Le medie risultano quindi medie pesate dei dati, i parametri $\sigma_m$ risultano dispersioni o covarianze pesate e i coefficienti di mixing coincidono con la proporzione media di massa assegnata a ciascuna componente.

## Vincoli e proprietà

- l'algoritmo EM puo convergere a massimi locali e **dipende dall'inizializzazione**

## Relazione con il clustering

Il GMM puo essere usato come modello di [[Data analysis -  Clustering|clustering]] probabilistico. A differenza di [[k-means|k-means]], che assegna ogni osservazione a un solo cluster, il GMM assegna a ogni osservazione una distribuzione di probabilità sulle componenti. In presenza di covarianze sferiche uguali e assegnazioni hard, il comportamento del modello si avvicina a quello di [[k-means|k-means]].
