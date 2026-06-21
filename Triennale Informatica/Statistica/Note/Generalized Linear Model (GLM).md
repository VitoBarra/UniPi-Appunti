---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Generalized Linear Model (GLM)
---
Un **Generalized Linear Model** (**GLM**) è un [[Modelli Probabilistici  - Agire in domini incerti|modello probabilistico]] per studiare relazioni tra variabili. Fornisce un framework comune che generalizza la [[Regressione lineare - Interpretazione probabilistica|regressione lineare vista come modello probabilistico]], la [[Regressione Logistica|regressione logistica]] e altri modelli per outcome diversi.  nei GLM lo stesso schema viene esteso anche a conteggi, proporzioni e altri tipi di risposta.

L'idea di fondo è: dato un outcome o **risposta** $Y$, vogliamo capire come una o più variabili esplicative influenzano il suo [[Variabili aleatoria - Valore atteso|valore atteso]]. 
In un dataset con osservazioni $i=1,\dots,n$ distinguiamo:
- **risposta** $Y_i$: la variabile che vogliamo **modellare o predire**;
- **covariate** $x_i=(x_{i1},\dots,x_{ip})$: le variabili esplicative osservate per la stessa unità.
Una covariata è un input del modello, ad esempio trattamento/controllo, età, sesso, dose, batch, tempo o gruppo sperimentale.



per modellare correttamente $Y_i$ si cerca di capire la  **media condizionata delle osservazione della risposta** è ovvero [[Variabili aleatoria - Valore atteso|valore atteso]] [[Probabilita condizionata|condizionao]] ai valori **osservati delle covariate**, cioè $$\mu_i=\mathbb{E}[Y_i\mid x_i]$$Questa quantità rappresenta il valore medio che ci aspettiamo per $Y_i$ tra osservazioni con covariate uguali a $x_i$. Se $Y_i$ è binaria, $\mu_i$ è una probabilità; se $Y_i$ è un conteggio, $\mu_i$ è il conteggio medio atteso.

per fare ciòin un **GLM** è costruito combinando tre componenti.

La **componente casuale** specifica la [[Legge di Probabilita|distribuzione]] della risposta $Y_i$. 
Nei GLM classici questa distribuzione appartiene alla [[Famiglia esponenziale di distribuzioni|famiglia esponenziale]], una classe che include molte distribuzioni comuni:
- [[Variabili Aleatorie Notevoli - Gaussiana|Gaussiana]] per risposte continue;
- [[Variabili Aleatorie Notevoli - Bernulli|Bernoulli]] o [[Variabili Aleatorie Notevoli - Binomiale|Binomiale]] per risposte binarie o proporzioni;
- [[Variabili Aleatorie Notevoli - Poisson|Poisson]] per conteggi;
- [[Variabili Aleatorie Notevoli - Gamma|Gamma]] per variabili positive continue.
La distribuzione scelta deve rispettare il tipo di valori che la risposta può assumere. Per esempio, un conteggio può assumere solo valori interi non negativi, quindi una Gaussiana può essere solo un'approssimazione; una Poisson è spesso più naturale. La distribuzione scelta determina anche la relazione tra [[Variabili aleatoria - Valore atteso|media]] e [[Variabili aleatorie - Varianza|varianza]].

La **componente sistematica** combina le covariate in una **forma lineare**. Si costruisce il **predittore lineare** $$\eta_i=x_i^T\beta=\beta_0+\beta_1x_{i1}+\dots+\beta_px_{ip}$$dove $x_i$ è il vettore delle covariate dell'osservazione $i$ e $\beta$ è il vettore dei parametri da stimare.

Il termine **lineare** qui non significa che la media $\mu_i$ debba essere lineare nelle covariate. Significa che è lineare il predittore $\eta_i$, cioè la quantità costruita sulla scala del link.

Questa parte si chiama sistematica perché raccoglie l'effetto ordinato e modellato delle covariate sulla risposta. Le covariate possono essere trattate come valori osservati/fissati, anche quando nella realtà derivano da un processo casuale.


La **funzione di link** $g$ collega la **componente casuale** e la **componente sistematica**. Si impone che una trasformazione della media sia uguale al predittore lineare: $$g(\mu_i)=\eta_i=x_i^T\beta$$Questa scrittura non significa che $\mu_i$ sia già calcolata e poi trasformata. Significa che $\mu_i$ è definita implicitamente come il valore che soddisfa la relazione. Equivalentemente: $$\mu_i=g^{-1}(x_i^T\beta)$$Quindi il modello può essere **non lineare sulla scala originale della risposta**, anche se resta lineare sulla scala del link.
La funzione di link serve anche a rispettare il supporto della risposta. Se $Y_i$ è binaria, la media è una probabilità e deve stare tra $0$ e $1$; se $Y_i$ è un conteggio, la media deve essere positiva.

Esempi:
- **link identità**: $g(\mu_i)=\mu_i$, quindi $\mu_i=x_i^T\beta$;
- **link logit**: $g(p_i)=\log\frac{p_i}{1-p_i}$, quindi $p_i=\frac{1}{1+e^{-x_i^T\beta}}$;
- **link log**: $g(\mu_i)=\log(\mu_i)$, quindi $\mu_i=e^{x_i^T\beta}$.

La funzione di link ottenuta naturalmente dalla forma in [[Famiglia esponenziale di distribuzioni|famiglia esponenziale]] è detta **link canonico**. Per esempio, il link canonico della Binomiale/Bernoulli è il **logit**, mentre il link canonico della Poisson è il **log**. In alcuni casi si possono usare link diversi dalla scelta canonica, ad esempio probit o complementary log-log per risposte binarie.


## Stima e test
I parametri $\beta$ sono stimati dai dati tramite [[Maximum Liklehood learning|massima verosimiglianza]]. Nel linguaggio di [[Stimatori statistici]], $\hat{\beta}$ è uno **stimatore** dei parametri ignoti $\beta$, perché è una statistica calcolata dal campione.
Una volta ottenuto $\hat{\beta}$, si sostituisce $\beta$ nel predittore lineare e si ottiene il **predittore lineare stimato** $$\hat{\eta}_i=x_i^T\hat{\beta}$$Questa quantità è lineare nelle covariate sulla scala del link.

La **media stimata** della risposta si ottiene poi tornando alla scala originale con l'inversa del link: $$\hat{\mu}_i=g^{-1}(\hat{\eta}_i)=g^{-1}(x_i^T\hat{\beta})$$Quindi $\hat{\eta}_i$ è lineare, mentre $\hat{\mu}_i$ può essere non lineare nelle covariate.

Una volta stimato il modello, si possono fare [[Test Statistici|test statistici]] sui coefficienti. Tipicamente si testa: $$H_0:\beta_j=0$$cioè si verifica se la covariata $j$ ha effetto sulla risposta, tenendo conto delle altre covariate presenti nel modello.

Il coefficiente $\beta_j$ non agisce sempre direttamente su $\mu_i$: agisce sul predittore lineare $\eta_i$ e quindi sulla scala definita dalla funzione di link. Per questo l'interpretazione dei coefficienti dipende dal link:
- con link identità, $\beta_j$ è una differenza additiva sulla media;
- con link logit, $\beta_j$ è una differenza nei log-odds;
- con link log, $e^{\beta_j}$ è un rapporto moltiplicativo sulla media o sul rate.
