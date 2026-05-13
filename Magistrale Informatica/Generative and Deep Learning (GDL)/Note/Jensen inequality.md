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
La **disuguaglianza di Jensen** mette in relazione il valore di una [[Funzioni|funzione]] applicata a una [[Statistica descrittiva - Dati Numerici|media]] con la media dei **valori della funzione**.

In forma generale, Jensen si può applicare a un [[Applicazioni Lineari|operatore lineare]] $L$ quando questo rappresenta una media pesata, ovvero quando l'operatore rispetta:
- **positivo**: per ogni funzione o quantità $g$ tale che $g\geq 0$, deve valere $L(g)\geq 0$;
- **normalizzato**: deve valere $L(1)=1$.
Se $L$ soddisfa queste condizioni, allora per una funzione convessa $f$ vale:$$f(L(x))\leq L(f(x))$$Per funzioni concave il verso della disuguaglianza si inverte.

## Caso discreto
Nel caso discreto si considerano punti $x_i$ nel dominio di $f$ e coefficienti $a_i\geq 0$ non tutti nulli. Questi coefficienti possono essere trasformati in pesi normalizzati dividendo per la loro somma:$$\lambda_i=\frac{a_i}{\sum_j a_j}$$In questo modo si ha $\lambda_i\geq 0$ e $\sum_i\lambda_i=1$, quindi i $\lambda_i$ sono i pesi di una **media pesata**.

L'operatore lineare $L$ è allora la [[Convessita#Combinazione convessa|combinazione convessa]] ovvero una media pesata dei punti $x_i$:$$L(x)=\sum_i \lambda_i x_i$$
Per una [[Funzioni Convesse-Concave|funzione convessa]] $f$, la disuguaglianza di Jensen diventa:$$f\left(\sum_i \lambda_i x_i\right) \le \sum_i \lambda_i f(x_i)$$Sostituendo i pesi normalizzati $\lambda_i=\frac{a_i}{\sum_j a_j}$ si ottiene la forma equivalente:$$f\left(\frac{\sum_i a_i x_i}{\sum_i a_i}\right)\leq \frac{\sum_i a_i f(x_i)}{\sum_i a_i}$$Per **[[Funzioni Convesse-Concave|funzioni concave]]** il verso della disuguaglianza si inverte.

Poiché i pesi $\lambda_i$ hanno le stesse proprietà di una [[Definizione di Probabilita|distribuzione di probabilità]] discreta, Jensen si può scrivere anche usando il [[Variabili aleatoria - Valore atteso|valore atteso]], che è un operatore lineare positivo e normalizzato:
$$f(\mathbb{E}[X]) \le \mathbb{E}[f(X)]$$
se $f$ è convessa. Se invece $f$ è concava, il verso della disuguaglianza si inverte:
$$f(\mathbb{E}[X]) \ge \mathbb{E}[f(X)]$$

## Caso del logaritmo
Nel contesto della [[Inferenza variazionale]], la funzione importante è il logaritmo. Poiché $\log$ è concava, per una variabile aleatoria positiva $Y$ vale:
$$\log \mathbb{E}[Y] \ge \mathbb{E}[\log Y]$$

Questa forma permette di **portare il logaritmo dentro un'aspettazione**, ottenendo però un lower bound. È il passaggio chiave usato per derivare l'[[Evidence Lower Bound|ELBO]].

## Uso nella derivazione dell'ELBO

Per un modello a variabili latenti:
$$\log p(x \mid \theta)= \log \int p(x,z \mid \theta)\,dz$$

si introduce una distribuzione variazionale $q(z \mid \phi)$ moltiplicando e dividendo per $q(z \mid \phi)$, nei punti in cui $q(z \mid \phi)>0$:
$$
\log p(x \mid \theta)
=
\log \int q(z \mid \phi)
\frac{p(x,z \mid \theta)}{q(z \mid \phi)}\,dz
$$

L'integrale può essere letto come un'aspettazione rispetto a $q$:
$$
\log p(x \mid \theta)
=
\log \mathbb{E}_q
\left[
\frac{p(x,z \mid \theta)}{q(z \mid \phi)}
\right]
$$

Applicando Jensen al logaritmo:
$$
\log p(x \mid \theta)
\ge
\mathbb{E}_q
\left[
\log \frac{p(x,z \mid \theta)}{q(z \mid \phi)}
\right]
$$

e quindi:
$$
\log p(x \mid \theta)
\ge
\mathbb{E}_q[\log p(x,z \mid \theta)]
-
\mathbb{E}_q[\log q(z \mid \phi)]
$$

Il membro destro è l'[[Evidence Lower Bound|ELBO]]:
$$\mathcal{L}(x,\theta,\phi)= \mathbb{E}_q[\log p(x,z \mid \theta)] + H(q)$$
dove $H(q)=-\mathbb{E}_q[\log q(z \mid \phi)]$ è l'entropia della distribuzione variazionale.

Jensen trasforma un obiettivo difficile, la log-likelihood marginale, in un obiettivo più trattabile:
$$\mathcal{L}(x,\theta,\phi) \le \log p(x \mid \theta)$$
Il prezzo pagato è che non si ottiene più l'obiettivo esatto, ma un **lower bound**. La qualità del bound dipende dalla scelta della distribuzione approssimante $q(z \mid \phi)$.

Nel caso ideale in cui $q(z \mid \phi)$ coincide con il vero posteriore $p(z \mid x,\theta)$, il bound diventa stretto e si recupera il comportamento dell'[[Expectation Maximization|EM]] esatto.
