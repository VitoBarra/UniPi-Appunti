---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Test approssimato sulla media di un campione di taglia grande
---
Come per gli intervalli di fiducia, l'approssimazione tramite il Teorema Centrale del Limite si può usare in generale per formulare test sulla media di una popolazione non necessariamente gaussiana, se il campione ha taglia $n$ grande.

Sia $X$ una v.a. con media $m$ (non nota) e varianza $\sigma^2$ nota, sia $X_1, \ldots X_n$ un campione i.i.d. con $n$ grande. Per il Teorema Centrale del Limite, la statistica $Z=\sqrt{n}(\bar{X}-m) / \sigma$ ha distribuzione approssimativamente gaussiana standard. Quindi valgono le stesse formule viste per il caso di campioni gaussiani a varianza nota. Ad esempio, per il test bilatero
$$
\left.\left.\mathscr{H}_0\right) m=m_0, \quad \text { contro } \quad \mathscr{H}_1\right) m \neq m_0
$$
al livello $\alpha$, la regione critica approssimata è
$$
C=\left\{\sqrt{n} \frac{\left|\bar{X}-m_0\right|}{\sigma}>q_{1-\frac{\alpha}{2}}\right\}
$$
e il $p$-value di $\left(x_1, \ldots x_n\right)$ è
$$
\mathbb{P}\left\{|Z|>\frac{\sqrt{n}}{\sigma}\left|\bar{x}-m_0\right|\right\} \approx 2\left[1-\Phi\left(\frac{\sqrt{n}}{\sigma}\left|\bar{x}-m_0\right|\right)\right] .
$$

Nel caso di varianza non nota, (sempre con $n$ grande), per il corollario al Teorema Centrale del Limite, la statistica $Z=\sqrt{n}(\bar{X}-m) / S$ ha distribuzione approssimativamente gaussiana standard. Quindi valgono ancora le formule viste per il caso di campioni gaussiani a varianza nota, ma rimpiazzando $\sigma$ con $S$.