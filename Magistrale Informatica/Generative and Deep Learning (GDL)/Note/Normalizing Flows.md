---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Modelli Generativi
topic: Flow-based models
SubTopic:
---
# Normalizing Flows
---
I **Normalizing Flows** sono [[Modelli Generativi|modelli generativi]] espliciti che trasformano una [[Distribuzione di probabilita|distribuzione]] semplice e trattabile in una distribuzione complessa sui dati tramite una sequenza di **[[Applicazioni tra insiemi|trasformazioni invertibili]]**.

L'idea di base e partire da una variabile **latente semplice** $$z \sim p_Z(z)$$ di solito una [[Variabili Aleatorie Notevoli - Gaussiana multivariata|gaussiana multivariata]] standard, e applicare una trasformazione deterministica invertibile $$x = g_{\theta}(z)$$ In questo modo il modello induce una distribuzione sui dati $x$, ma a differenza di una [[Generative Adversarial Networks (GAN)|GAN]] la densita resta calcolabile in forma chiusa se la trasformazione e scelta nel modo giusto.

Questa e la caratteristica centrale dei **Normalizing Flows**:
- generano campioni tramite trasformazioni neurali
- definiscono una densità esplicita sui dati
- possono essere addestrati con [[Maximum Liklehood learning|Maximum Likelihood]]

Il **flow generativo** e la mappa diretta che porta un campione latente semplice nello spazio dei dati:$$x = g_{\theta}(z)$$Il **flow di normalizzazione** e la mappa inversa che riporta un dato osservato nello spazio latente semplice: $$z = f_{\theta}(x) = g_{\theta}^{-1}(x)$$
![[IMG - Normalizing Flows generative e samplign direction.png]]
La base matematica viene dalla regola di [[Trasformazioni di variabili con densita|cambio di variabile]] per densita.Nel caso multivariato, se $$x = g_{\theta}(z)$$ con $g_{\theta}$ invertibile, allora la densità di $x$ si ottiene da quella di $z$ correggendo il volume _locale introdotto dalla trasformazione: $$p_X(x) = p_Z(g_{\theta}^{-1}(x))\left|\det J_{g_{\theta}^{-1}}(x)\right|$$dove $J_{g_{\theta}^{-1}}(x)$ e il [[Jacobiana di una funzione|jacobiano]] della trasformazione inversa. Equivalentemente, scrivendo il modello in avanti come $x=g_{\theta}(z)$ e ponendo $z=g_{\theta}^{-1}(x)=f_{\theta}(x)$, si puo anche usare: $$p_X(x) = p_Z(z)\left|\det J_{g_{\theta}}(z)\right|^{-1}$$Passando al logaritmo si ottiene una forma piu comoda per il training:$$\log p_X(x) = \log p_Z(g_{\theta}^{-1}(x)) + \log \left|\det J_{g_{\theta}^{-1}}(x)\right|$$Questa formula mostra che la log-densita del dato osservato dipende da due contributi:
- quanto il punto trasformato all'indietro $z=g_{\theta}^{-1}(x)=f_{\theta}(x)$ sia plausibile sotto la distribuzione base;
- quanto la trasformazione comprima o dilati localmente i volumi.
![[IMG - Normalizing Flows.png]]

## Perche si chiamano flow
Il nome **flow** richiama l'idea che la distribuzione di probabilita venga deformata progressivamente da una sequenza di trasformazioni invertibili. Invece di modellare direttamente $p_X(x)$ con una formula chiusa, si prende una distribuzione semplice e la si spinge poco alla volta verso la distribuzione dei dati.

Se si usano piu trasformazioni invertibili in cascata, $$x = g_K \circ g_{K-1} \circ \dots \circ g_1(z)$$allora il modello costruisce una trasformazione complessiva sempre invertibile. Definendo gli stati intermedi$$h_0 = z, \quad h_k = g_k(h_{k-1}), \quad h_K = x$$la densita finale si ottiene sommando i contributi log-determinante di tutti i passaggi: $$\log p_X(x) = \log p_Z(z) - \sum_{k=1}^{K}\log\left|\det J_{g_k}(h_{k-1})\right|$$oppure, in forma equivalente usando le inverse,$$\log p_X(x) = \log p_Z(h_0) + \sum_{k=1}^{K}\log\left|\det J_{g_k^{-1}}(h_k)\right|$$Quindi un flow profondo resta trattabile solo se ogni blocco $g_k$ soddisfa due proprieta:
- deve essere invertibile;
- il determinante del jacobiano deve essere calcolabile in modo efficiente.
  
## Training
I **Normalizing Flows** sono [[Modelli Probabilistici|modelli probabilistici]] espliciti, quindi il training segue direttamente il criterio di [[Maximum Liklehood learning|massima likelihood]]. Dato un dataset [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite (IDD)|iid]] $\mathcal{D}=\{x_1,\dots,x_N\}$ si vuole massimizzare: $$L(\theta;\mathcal{D}) = \prod_{i=1}^{N} p_{\theta}(x_i) \implies \log L(\theta;\mathcal{D}) = \sum_{i=1}^{N}\log p_{\theta}(x_i)$$
Questo e un vantaggio importante rispetto ad altri [[Modelli Generativi|modelli generativi]]:
- rispetto ai [[Generative Adversarial Networks (GAN)|GAN]], non serve un discriminatore avversariale;
- rispetto ai [[Variational Autoencoder (VAE)|VAE]], non si ottimizza un lower bound come l'[[Evidence lower bound (ELBO) Method|ELBO]], ma una likelihood esatta;
- il modello assegna una densita valutabile a ogni punto dello spazio.

## Generazione e inferenza inversa
Una volta addestrato il modello, generare nuovi campioni e semplice:
- si campiona $$z \sim p_Z(z)$$
- si applica il flow generativo $$x = g_{\theta}(z)$$
Anche il passaggio inverso e disponibile in modo esplicito:$$z = f_{\theta}(x) = g_{\theta}^{-1}(x)$$Questo rende i flow utili non solo per generare dati, ma anche per mappare osservazioni complesse in uno spazio latente semplice in cui la distribuzione e nota.

## Scelta delle trasformazioni
Il problema pratico e che una rete neurale arbitraria non va bene: puo essere molto espressiva, ma in generale non e invertibile e il suo jacobiano puo essere troppo costoso da trattare.

Per questo i **Normalizing Flows** usano trasformazioni progettate apposta. Ogni blocco cerca un compromesso tra:
- espressivita, cioe capacita di deformare la distribuzione;
- invertibilita;
- costo del calcolo di $\det J$
Una strategia comune e usare btlocchi strutturati, ad esempio con jacobiano triangolare o quasi diagonale, cosi il determinante diventa semplice da calcolare come prodotto degli elementi diagonali.

Uno dei blocchi piu usati per ottenere questa proprieta e il [[Coupling Flow]], in cui solo una parte delle variabili viene trasformata direttamente mentre l'altra parte controlla i parametri della trasformazione.

## Interpretazione geometrica
Geometricamente, un flow non crea o distrugge punti: riorganizza lo spazio deformandolo in modo invertibile. Regioni ad alta densita della distribuzione base vengono stirate, compresse o ruotate fino a combaciare con la geometria della distribuzione dei dati.

Il termine con il determinante del jacobiano misura proprio questa deformazione locale dei volumi:
- se la trasformazione espande localmente una regione, la densita si abbassa;
- se la comprime, la densita aumenta.

In questo senso i **Normalizing Flows** forniscono una costruzione molto diretta di una densita complessa a partire da una densita semplice.

## Principali famiglie
Le architetture di flow si distinguono soprattutto per il modo in cui impongono invertibilita e trattabilita del jacobiano. Una prima famiglia e quella dei [[Coupling Flow]], in cui il vettore viene partizionato e solo una parte viene trasformata condizionandola sull'altra; questo produce tipicamente un jacobiano triangolare a blocchi e rende semplice il calcolo del determinante. Una seconda famiglia e quella degli [[Autoregressive Flows]], in cui ogni componente trasformata dipende da quelle precedenti secondo un ordinamento; anche qui il jacobiano resta triangolare, ma cambia il trade-off computazionale tra valutazione della densita e generazione. Una terza direzione e quella dei [[Residual Flows]], in cui si definisce la trasformazione come una mappa residua invertibile, del tipo $f(x)=x+r(x)$ con vincoli opportuni sulla funzione $r$ per garantire invertibilita e controllo del log-determinante.

Queste famiglie condividono lo stesso principio, cioe trasformare una distribuzione base semplice in una distribuzione dei dati piu complessa, ma differiscono nella struttura del blocco elementare e quindi nel compromesso tra espressivita, costo computazionale e facilita di inversione.



## Limiti
I **Normalizing Flows** hanno anche vincoli importanti:
- l'invertibilita restringe la famiglia di trasformazioni che si possono usare;
- il costo del jacobiano impone architetture specializzate;
- in alta dimensionalita il trade-off tra espressivita e trattabilita puo essere difficile;
Questi limiti hanno motivato altre famiglie di modelli generativi, tra cui i modelli [[Score Function|score-based]] e i [[Diffusion Models]], che rinunciano alla likelihood esatta in favore di dinamiche di denoising o campi vettoriali piu flessibili.
