---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Jensen inequality
---
La **disuguaglianza di Jensen** mette in relazione il valore di una funzione applicata a una media con la media dei valori della funzione. 

È uno strumento fondamentale quando si lavora con funzioni [[Funzioni Convesse-Concave|convesse o concave]] e con operatori lineari come l'[[Variabili aleatoria - Valore atteso|il valore atteso]].

Per una funzione convessa $f$ e pesi $\lambda_i \ge 0$ tali che $\sum_i \lambda_i = 1$: $$
f\left(\sum_i \lambda_i x_i\right)
\le
\sum_i \lambda_i f(x_i)
$$
In forma probabilistica:$$f(\mathbb{E}[X]) \le \mathbb{E}[f(X)]$$se $f$ è convessa. Se invece $f$ è concava, il verso della disuguaglianza si inverte:

$$
f(\mathbb{E}[X]) \ge \mathbb{E}[f(X)]
$$

![[IMG - Jensen inequality.png]]


## Caso del logaritmo
Nel contesto della [[Inferenza variazionale]], la funzione importante è il logaritmo. Poiché $\log$ è concava: $$\log \mathbb{E}[Y] \ge \mathbb{E}[\log Y]$$Questa forma permette di **portare il logaritmo dentro un'aspettazione**, ottenendo però un lower bound. È il passaggio chiave usato per derivare l'[[Evidence Lower Bound|ELBO]].

## Uso nella derivazione dell'ELBO

Per un modello a variabili latenti:$$ \log p(x \mid \theta)= \log \int p(x,z \mid \theta)\,dz $$si introduce una distribuzione variazionale $q(z \mid \phi)$ moltiplicando e dividendo per la stessa quantità:$$
\log p(x \mid \theta)
=
\log \int q(z \mid \phi)
\frac{p(x,z \mid \theta)}{q(z \mid \phi)}\,dz
$$

L'integrale può essere letto come un'aspettazione rispetto a $q$:$$
\log p(x \mid \theta)
=
\log \mathbb{E}_q
\left[
\frac{p(x,z \mid \theta)}{q(z \mid \phi)}
\right]
$$

Applicando Jensen al logaritmo: $$
\log p(x \mid \theta)
\ge
\mathbb{E}_q
\left[
\log \frac{p(x,z \mid \theta)}{q(z \mid \phi)}
\right]
$$

e quindi:$$
\log p(x \mid \theta)
\ge
\mathbb{E}_q[\log p(x,z \mid \theta)]
-
\mathbb{E}_q[\log q(z \mid \phi)]
$$

Il membro destro è l'[[Evidence Lower Bound|ELBO]]:$$ \mathcal{L}(x,\theta,\phi)= \mathbb{E}_q[\log p(x,z \mid \theta)] + H(q)$$

Jensen trasforma un obiettivo difficile, la log-likelihood marginale, in un obiettivo più trattabile: $$\mathcal{L}(x,\theta,\phi) \le \log p(x \mid \theta)$$
Il prezzo pagato è che non si ottiene più l'obiettivo esatto, ma un **lower bound**. La qualità del bound dipende dalla scelta della distribuzione approssimante $q(z \mid \phi)$.

Nel caso ideale in cui $q(z \mid \phi)$ coincide con il vero posteriore $p(z \mid x,\theta)$, il bound diventa stretto e si recupera il comportamento dell'[[Expectation Maximization|EM]] esatto.


