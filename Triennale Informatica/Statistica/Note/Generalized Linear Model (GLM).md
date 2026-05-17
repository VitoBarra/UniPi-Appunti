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
Un **Generalized Linear Model** (**GLM**) è un [[Modelli probabilistici|modello probabilistico]] usato per descrivere come cambia la [[Variabili aleatoria - Valore atteso|media]] di una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]] risposta_ al variare di alcune [[Variabili aleatorie - Covarianza e correlazione|covariate]].

Il **GLM** è una generalizzazione della [[Regressione lineare - Interpretazione probabilistica|regressione lineare vista come modello probabilistico gaussiano]] in cui  si assume che la risposta sia continua e che gli errori siano [[Variabili Aleatorie Notevoli - Gaussiana|gaussiani]]; 

nei **GLM** invece scegliamo si assume che ogni osservazione $Y_i$ segua una certa [[Legge di Probabilita|distribuzione]], scelta in base al tipo di dato. Per esempio si può usare:
- [[Variabili Aleatorie Notevoli - Gaussiana|Gaussiana]] per dati continui
- [[Variabili Aleatorie Notevoli - Bernulli|Bernoulli]] o una [[Variabili Aleatorie Notevoli - Binomiale|Binomiale]] per dati binari o proporzioni,
- [[Variabili Aleatorie Notevoli - Poisson|Poisson]] per conteggi
- [[Variabili aleatorie Notevoli - Negative Binomial|Negative Binomial]] per conteggi con overdispersion.

La distribuzione scelta determina anche la relazione tra [[Variabili aleatoria - Valore atteso|media]] e [[Variabili aleatorie - Varianza|varianza]]. Indicando con $$\mu_i=\mathbb{E}[Y_i]$$la media della risposta, il GLM non impone necessariamente che $\mu_i$ sia una funzione lineare delle covariate. Impone invece che una trasformazione della media sia lineare nei parametri.

Si costruisce quindi un predittore lineare $\eta_i$ a partire dalle covariate: $$\eta_i=x_i^T\beta$$dove:
- $x_i$ è il vettore delle covariate dell'osservazione $i$
- $\beta$ è il vettore dei parametri da stimare

La media $\mu_i$ viene collegata al predittore lineare tramite una **funzione di link** $g$:$$g(\mu_i)=\eta_i$$cioè$$\mu_i=g^{-1}(\eta_i)$$Questa è la forma generale del modello: si sceglie una distribuzione per $Y_i$, si definisce la sua media $\mu_i$, e si usa una funzione di link per rendere lineare nelle covariate una trasformazione della media.

La funzione di link serve anche a rispettare il supporto della variabile risposta. Per esempio, se $Y_i$ è un conteggio, la media deve essere positiva


#### Esempi

Nel modello lineare classico:
$$
Y_i\sim \mathcal{N}(\mu_i,\sigma^2)
$$
e si usa il link identità:
$$
\mu_i=x_i^T\beta
$$

Nella regressione logistica la risposta è binaria, quindi si usa una variabile [[Variabili Aleatorie Notevoli - Bernulli|Bernoulli]]:
$$
Y_i\sim Bernoulli(p_i)
$$
e il link logit:
$$
\log\frac{p_i}{1-p_i}=x_i^T\beta
$$

Nella regressione di [[Variabili Aleatorie Notevoli - Poisson|Poisson]] la risposta è un conteggio:
$$
Y_i\sim Poisson(\mu_i)
$$
e si usa tipicamente il link [[Funzione logaritmica|log]]:
$$
\log(\mu_i)=x_i^T\beta
$$

Nel caso di conteggi con overdispersion si può usare una [[Variabili aleatorie Notevoli - Negative Binomial|Negative Binomial]]:
$$
Y_i\sim NB(\mu_i,\phi)
$$
con
$$
Var(Y_i)=\mu_i+\phi\mu_i^2
$$
e anche qui si usa spesso il link [[Funzione logaritmica|log]]:
$$
\log(\mu_i)=x_i^T\beta
$$

#### Stima e test
I parametri $\beta$ sono stimati tramite [[Stima Parametrica - Maximum Liklehood|massima verosimiglianza]].

Una volta stimato il modello, si possono fare [[Test Statistici|test statistici]] sui coefficienti. Tipicamente si testa:$$H_0:\beta_j=0$$cioè si verifica se la covariata $j$ ha un effetto sulla media della risposta.

Il coefficiente $\beta_j$ non agisce direttamente sempre su $\mu_i$, ma sul predittore lineare $\eta_i$. Per questo la sua interpretazione dipende dalla funzione di link usata.