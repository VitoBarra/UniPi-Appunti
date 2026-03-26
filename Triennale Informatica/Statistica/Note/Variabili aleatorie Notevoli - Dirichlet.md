---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili aleatorie Notevoli - Dirichlet
---
La distribuzione **Dirichlet** e una distribuzione continua multivariata definita sul [[Simplex (Simplesso)|simplesso]].

E utile per modellare vettori di probabilita
$$
(\theta_1,\dots,\theta_K)
$$
con
$$
\theta_i\geq 0, \qquad \sum_{i=1}^K \theta_i=1.
$$

## Supporto

La Dirichlet e definita sul simplesso
$$
\Delta^{K-1}=\left\{(\theta_1,\dots,\theta_K)\in\mathbb{R}^K \mid \theta_i\geq 0,\ \sum_{i=1}^K \theta_i=1\right\}.
$$

Quindi descrive un vettore di proporzioni o probabilita che devono sommare a $1$.

## Definizione

Sia
$$
\alpha=(\alpha_1,\dots,\alpha_K), \qquad \alpha_i>0.
$$

Si dice che il vettore aleatorio
$$
\Theta=(\Theta_1,\dots,\Theta_K)
$$
ha distribuzione di Dirichlet di parametro $\alpha$, e si scrive
$$
\Theta\sim \mathrm{Dir}(\alpha_1,\dots,\alpha_K),
$$
se ha densita
$$
f(\theta_1,\dots,\theta_K)
=
\frac{\Gamma(\alpha_0)}{\prod_{i=1}^K \Gamma(\alpha_i)}
\prod_{i=1}^K \theta_i^{\alpha_i-1},
$$
per $(\theta_1,\dots,\theta_K)\in\Delta^{K-1}$, dove
$$
\alpha_0=\sum_{i=1}^K \alpha_i.
$$

Il termine
$$
\frac{\Gamma(\alpha_0)}{\prod_{i=1}^K \Gamma(\alpha_i)}
$$
e il fattore di normalizzazione.

## Interpretazione dei parametri

I parametri $\alpha_1,\dots,\alpha_K$ controllano la forma della distribuzione.

In particolare:
- ciascun $\alpha_i$ pesa la componente $\theta_i$;
- la somma $\alpha_0=\alpha_1+\dots+\alpha_K$ controlla la concentrazione totale;
- i rapporti $\alpha_i/\alpha_0$ determinano la posizione media.

Dal punto di vista intuitivo, i parametri $\alpha_i$ possono essere letti come **pseudo-conteggi**.

## Media, varianza e covarianza

Se $\Theta\sim \mathrm{Dir}(\alpha_1,\dots,\alpha_K)$, allora per ogni $i$ vale
$$
\mathbb{E}[\Theta_i]=\frac{\alpha_i}{\alpha_0}.
$$

Le [[Variabili aleatorie - Varianza|varianze]] sono
$$
\mathrm{Var}(\Theta_i)=\frac{\alpha_i(\alpha_0-\alpha_i)}{\alpha_0^2(\alpha_0+1)}.
$$

Per $i\neq j$ le covarianze valgono
$$
\mathrm{Cov}(\Theta_i,\Theta_j)=
-\frac{\alpha_i\alpha_j}{\alpha_0^2(\alpha_0+1)}.
$$

Le covarianze sono negative perche le componenti devono sommare a $1$: se una cresce, almeno un'altra deve diminuire.

## Relazione con la Beta

La distribuzione Dirichlet e la generalizzazione multivariata della [[Variabili Aleatorie notevoli - Beta|distribuzione Beta]].

Infatti, per $K=2$ si ottiene
$$
(\Theta_1,\Theta_2)\sim \mathrm{Dir}(\alpha_1,\alpha_2)
$$
con
$$
\Theta_1+\Theta_2=1,
$$
e quindi basta studiare una sola componente, che ha distribuzione Beta:
$$
\Theta_1\sim \mathrm{Beta}(\alpha_1,\alpha_2).
$$

## Effetto dei parametri

La forma della distribuzione cambia molto al variare di $\alpha$:
- se tutti gli $\alpha_i=1$, la distribuzione e uniforme sul simplesso;
- se gli $\alpha_i<1$, la massa tende a concentrarsi vicino ai vertici;
- se gli $\alpha_i>1$, la massa tende a concentrarsi verso il centro;
- se alcuni parametri sono piu grandi di altri, la distribuzione favorisce le componenti corrispondenti.

![[IMG - visualizazione Dirichlet in 3 variabili.png]]

## Relazione con la multinomiale

La Dirichlet e il prior coniugato naturale della [[Variabili Aleatorie Notevoli - Multinomiale|multinomiale]].

Se
$$
\Theta\sim \mathrm{Dir}(\alpha_1,\dots,\alpha_K)
$$
e, condizionatamente a $\Theta$, si osserva un campione multinomiale con conteggi
$$
n=(n_1,\dots,n_K),
$$
allora la distribuzione a posteriori e ancora una Dirichlet:
$$
\Theta \mid n \sim \mathrm{Dir}(\alpha_1+n_1,\dots,\alpha_K+n_K).
$$

Questo rende la Dirichlet molto importante in statistica bayesiana.

## Interpretazione probabilistica

La Dirichlet modella incertezza su un vettore di probabilita discrete.

Per questo compare spesso quando:
- le probabilita delle categorie non sono note;
- si vuole usare un modello bayesiano;
- si lavora con distribuzioni categoriali o multinomiali.

>[!tip]
> La [[Variabili Aleatorie notevoli - Beta|Beta]] e un caso particolare della Dirichlet: basta prendere due componenti.
