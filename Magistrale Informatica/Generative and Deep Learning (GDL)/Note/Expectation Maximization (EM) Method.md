---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Expectation Maximization (EM)
---
L'**Expectation Maximization** (**EM**) e un algoritmo iterativo di [[Maximum Liklehood learning|massima likelihood]] usato nei [[Latent or hidden Model|modelli a variabili latenti]], cioe quando parte del processo generativo non e osservata direttamente.


### Modello a variabili latenti (da spostare)
Assumendo
- $X$ indica le [[Variabili Aleatorie (Casuali)|variabili aleatorie]] osservate, oppure l'intero dataset osservato
- $Z$ indica una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] **latente** o **nascosta**, cioe introdotta dal modello ma non osservata nei dati
- $\theta$ indica i parametri del modello

In un modello latente si assume una [[Full Joint Distribution (FJD)|distribuzione congiunta]] $\mathcal{P}(X,Z \mid \theta)$. 
La distribuzione osservata si ottiene [[FJD - Marginalizzazione|marginalizzando]] la variabile latente e puo essere vista come un [[Variabili aleatoria - Valore atteso|valore atteso]] rispetto a $\mathcal{P}(Z \mid \theta)$: $$\mathcal{P}(X \mid \theta)=\mathbb{E}_{\mathcal{P}(Z \mid \theta)}[\mathcal{P}(X \mid Z,\theta)]$$Se $Z$ e discreta questa espressione coincide con $$\mathcal{P}(X \mid \theta)=\sum_z \mathcal{P}(X,Z=z \mid \theta)$$mentre se $Z$ e continua la somma viene sostituita da un integrale.

Nel caso di [[Maximum Liklehood learning|massimo di likelihood]] si vuole stimare$$\theta_{ML}=\arg\max_\theta \mathcal{L}(\theta \mid X)=\arg\max_\theta \mathcal{P}(X \mid \theta)$$dove $\mathcal{L}(\theta \mid X)$ e la **incomplete likelihood** oppure **observed-data likelihood**, perche dipende solo dai dati osservati $X$ Il punto difficile e che la log-likelihood osservata contiene il logaritmo di una somma o di un integrale:$$\log \mathcal{P}(X \mid \theta)=\log \sum_Z \mathcal{P}(X,Z \mid \theta)$$e questo rende la massimizzazione **intrattabile** in modo diretto

Se invece si conoscessero anche i valori di $Z$, allora si potrebbe lavorare con i **dati completi** $d=(X,Z)$, con la **complete-data likelihood** e la **complete-data log-likelihood** $$\mathcal{L}_c(\theta \mid d)=\mathcal{P}(X,Z \mid \theta) \implies \log \mathcal{L}_c(\theta \mid d)=\log \mathcal{P}(X,Z \mid \theta)$$che e spesso molto piu semplice da ottimizzare.

Nei [[Latent or hidden Model|modelli latenti]] la [[Full Joint Distribution (FJD)|distribuzione congiunta]] si tipicamente fattorizza tramite [[Regola del prodotto|regola del prodotto]] come$$\mathcal{P}(X,Z \mid \theta)=\mathcal{P}(X \mid Z,\theta)\mathcal{P}(Z \mid \theta)$$mentre vale anche la decomposizione bayesiana$$\mathcal{P}(X,Z \mid \theta)=\mathcal{P}(Z \mid X,\theta)\mathcal{P}(X \mid \theta)$$ma questa non elimina il problema computazionale, perche contiene comunque la quantita difficile $\mathcal{P}(X \mid \theta)$.


### Expetation Maximization algorithm
l algoritmo del **Expetation Maximization** massimizza **iterativamente** il [[Variabili aleatoria - Valore atteso|valore atteso]] della **complete-data log-likelihood** rispetto al [[Formula di Bayes|posteriore]] corrente sulle **variabili latenti**.

 all'iterazione $k$ si definisce$$
Q(\theta \mid \theta^{(k)}) = \mathbb{E}_{Z \sim \mathcal{P}(Z \mid X,\theta^{(k)})}\left[\log \mathcal{P}(X,Z \mid \theta)\right]
$$ e poi si seguono gli step:
- **E-step**: si calcola il posteriore della variabile latente sotto i parametri correnti $\mathcal{P}(Z \mid X,\theta^{(k)})$ ovvero si chiede: "dato $X$ e dato il modello corrente $\theta^{(k)}$, quali valori di $Z$ sono plausibili?"
- **M-step**: si aggiorna il modello massimizzando la **complete-data log-likelihood** attesa, cioe $\theta^{(k+1)}=\arg\max_\theta Q(\theta \mid \theta^{(k)})$ ovvero si chiede: "se usassi queste plausibilita come informazione sui dati nascosti, quali parametri $\theta$ sarebbero migliori?"
L'E-step produce quindi **soft assignments** o **soft counts**: invece di dire quale valore abbia sicuramente $Z$, assegna probabilita ai diversi valori possibili di $Z$.
![[IMG - Expectation Maximization (EM) graficamete.png]]
L'algoritmo viene iterato finche un criterio di convergenza e soddisfatto. Per esempio ci si puo fermare quando $$|\log \mathcal{P}(X \mid \theta^{(k+1)})-\log \mathcal{P}(X \mid \theta^{(k)})|<\varepsilon$$ oppure quando si raggiunge un numero massimo di iterazioni.

Quindi EM trasforma un problema di massima likelihood con variabili non osservate in una sequenza di problemi piu semplici. $Q$ è una funzione ausiliaria che tocca la likelihood osservata nel punto corrente e che permette un aggiornamento monotono.

In particolare vale il seguente teorema di **Dempster, Laird e Rubin (1977)**:
**se** nell'**E-step** si usa il [[Formula di Bayes|posteriore]] esatto $\mathcal{P}(Z \mid X,\theta^{(k)})$
**allora** un processo EM garantisce $$\mathcal{L}(\theta^{(k+1)} \mid X)\geq \mathcal{L}(\theta^{(k)} \mid X) \implies \log \mathcal{P}(X \mid \theta^{(k+1)}) \geq \log \mathcal{P}(X \mid \theta^{(k)})$$Quindi a ogni iterazione la log-likelihood osservata non diminuisce. 

Una scrittura utile per capire l'algoritmo e:$$\log \mathcal{P}(X \mid \theta)=Q(\theta \mid \theta^{(k)})-\mathbb{E}_{Z \mid X,\theta^{(k)}}[\log \mathcal{P}(Z \mid X,\theta)]+\text{costante}$$da cui si ricava la classica interpretazione di EM come massimizzazione di un lower bound ottenuto tramite [[Jensen inequality|Jensen]].

![[IMG - Expectation Maximization (EM) interpretazione geometrica.png]]
EM esatto richiede che il posteriore $\mathcal{P}(Z \mid X,\theta)$ sia calcolabile. Quando questo non e possibile, si usano metodi approssimati come inferenza variazionale, [[Evidence lower bound (ELBO)|ELBO]] o tecniche Monte Carlo.

Quindi EM e praticabile quando il calcolo del posteriore delle variabili latenti e fattibile, oppure almeno abbastanza semplice da approssimare bene.
