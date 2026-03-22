---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Mixture Models
---
I mixture models sono modelli generativi probabilistici in cui la [[Distribuzione di probabilita|distribuzione di probabilita]] osservata e rappresentata come combinazione pesata di piu componenti elementari. Ogni osservazione $x$ e associata a una [[Latent or hidden Model|variabile latente]] discreta $z$ che seleziona la componente generatrice, quindi il modello descrive una popolazione eterogenea come unione di sottopopolazioni piu semplici.

## Struttura del modello

Si introduce $z \in \{1,\dots,K\}$ con probabilita a priori $P(z=k)=\pi_k$, dove $\pi_k \geq 0$ e $\sum_{k=1}^K \pi_k=1$. Condizionatamente a $z=k$, il dato e distribuito secondo $p(x\mid z=k)=p(x\mid \theta_k)$. La distribuzione congiunta e $$p(x,z=k)=p(z=k)p(x\mid z=k)=\pi_k p(x\mid \theta_k)$$ mentre la distribuzione marginale osservata si ottiene per [[FJD - Marginalizzazione|marginalizzazione]] della variabile latente: $$p(x)=\sum_{k=1}^K p(x,z=k)=\sum_{k=1}^K \pi_k p(x\mid \theta_k)$$ Questa forma rende naturale la modellazione di densita multimodali e di assegnazioni soft alle componenti.

## Dataset osservato e likelihood

Dato un insieme iid $\mathcal{D}=\{x_1,\dots,x_N\}$, si introduce una variabile latente $z_n$ per ogni osservazione $x_n$. La likelihood osservata e $$p(\mathcal{D})=\prod_{n=1}^N \sum_{k=1}^K \pi_k p(x_n\mid \theta_k)$$ e la log-likelihood e $$\log p(\mathcal{D})=\sum_{n=1}^N \log\left(\sum_{k=1}^K \pi_k p(x_n\mid \theta_k)\right)$$ Il termine $\log \sum_k$ rende il problema di [[Stima Parametrica - Metodo di Massima Verosomiglianza|massima verosomiglianza]] non direttamente trattabile come nei modelli senza variabili nascoste.

Se invece le assegnazioni fossero note, usando variabili indicatori $z_{nk}\in\{0,1\}$ con $\sum_k z_{nk}=1$, la complete-data likelihood sarebbe $$p(X,Z\mid \pi,\theta)=\prod_{n=1}^N \prod_{k=1}^K [\pi_k p(x_n\mid \theta_k)]^{z_{nk}}$$ e la complete-data log-likelihood sarebbe $$\log p(X,Z\mid \pi,\theta)=\sum_{n=1}^N \sum_{k=1}^K z_{nk}[\log \pi_k+\log p(x_n\mid \theta_k)]$$ In questa forma la dipendenza dalle variabili latenti diventa lineare.

## Posterior e responsibilities

La probabilita a posteriori che $x_n$ provenga dalla componente $k$ si ottiene con la [[Formula di Bayes|formula di Bayes]]: $$\gamma(z_{nk})=P(z_n=k\mid x_n)=\frac{\pi_k p(x_n\mid \theta_k)}{\sum_{j=1}^K \pi_j p(x_n\mid \theta_j)}$$ Le quantita $\gamma(z_{nk})$ sono dette responsibilities e soddisfano $0\leq \gamma(z_{nk})\leq 1$ e $\sum_{k=1}^K \gamma(z_{nk})=1$. Esse descrivono un'assegnazione probabilistica dei punti alle componenti, quindi il mixture model induce un clustering soft.

## Apprendimento con EM

L'apprendimento dei parametri $\pi,\theta$ avviene tipicamente con l'algoritmo Expectation-Maximization. Nel passo E si calcolano le posterior sulle variabili latenti mantenendo fissi i parametri correnti, quindi $$\gamma(z_{nk})=P(z_n=k\mid x_n,\pi,\theta)$$ Nel passo M si massimizza rispetto ai parametri il valore atteso della complete-data log-likelihood: $$Q(\pi,\theta)=\mathbb{E}_{Z\mid X}[\log p(X,Z\mid \pi,\theta)]$$ L'alternanza tra inferenza delle variabili nascoste e aggiornamento parametrico produce una successione di valori della log-likelihood osservata non decrescente, con convergenza a un ottimo locale.

## Gaussian Mixture Models

Il caso piu rilevante e [[Mixture of Gaussian model (GMM)|Gaussian Mixture Model]], in cui ogni componente appartiene alla famiglia delle [[Variabili Aleatorie Notevoli - Gaussiana|gaussiane]]: $$p(x\mid z=k)=\mathcal{N}(x\mid \mu_k,\Sigma_k)$$ La densita risultante e $$p(x)=\sum_{k=1}^K \pi_k \mathcal{N}(x\mid \mu_k,\Sigma_k)$$ I parametri del modello sono i coefficienti di mixing $\pi_k$, le medie $\mu_k$ e le matrici di covarianza $\Sigma_k$.

Nel GMM il passo E assume la forma $$\gamma(z_{nk})=\frac{\pi_k \mathcal{N}(x_n\mid \mu_k,\Sigma_k)}{\sum_{j=1}^K \pi_j \mathcal{N}(x_n\mid \mu_j,\Sigma_j)}$$ Definendo poi $N_k=\sum_{n=1}^N \gamma(z_{nk})$, il passo M fornisce gli aggiornamenti $$\mu_k=\frac{1}{N_k}\sum_{n=1}^N \gamma(z_{nk})x_n$$ $$\Sigma_k=\frac{1}{N_k}\sum_{n=1}^N \gamma(z_{nk})(x_n-\mu_k)(x_n-\mu_k)^T$$ $$\pi_k=\frac{N_k}{N}$$ Le medie e le covarianze risultano quindi stime pesate dalle responsibilities, mentre i coefficienti di mixing rappresentano la massa media assegnata a ciascuna componente.

## Proprieta essenziali

- I mixture models descrivono distribuzioni multimodali mediante somma pesata di componenti.
- La variabile latente $z$ rende esplicita la struttura nascosta del processo generativo.
- L'inferenza su $z$ produce appartenenze probabilistiche e non assegnazioni hard.
- EM dipende dall'inizializzazione e puo convergere a massimi locali.
- La scelta di $K$ non e interna al modello e richiede un criterio esterno di selezione.
