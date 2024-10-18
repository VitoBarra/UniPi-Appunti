---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Test approssimato su un campione di bernoulli
---
Sia $X_1, \ldots, X_n$ un campione i.i.d. di variabili di Bernoulli di parametro $p \in(0,1)$ : vogliamo formulare un test relativo al parametro $p$. Esattamente come per gli intervalli di fiducia approssimati, usiamo il fatto che, per $n$ grande, la variabile $\sqrt{n} \frac{\bar{x}_{-p}}{\sqrt{p(1-p)}}$ è approssimativamente Gaussiana standard.
Consideriamo ad esempio il test bilatero dell'ipotesi
$$
\left.\left.\mathscr{H}_0\right) p=p_0 \quad \text { contro } \quad \mathscr{H}_1\right) p \neq p_0
$$
al livello $\alpha$, assumendo che $n$ sia grande.
- Formulazione del test: La regione critica approssimata è
$$
C=\left\{\frac{\sqrt{n}\left|\bar{X}-p_0\right|}{\sqrt{p_0\left(1-p_0\right)}}>q_{1-\frac{a}{2}}\right\} .
$$
- p-value: Il $p$-value è
$$
\mathbb{P}_{p_0}\left\{\frac{\sqrt{n}\left|\bar{X}-p_0\right|}{\sqrt{p_0\left(1-p_0\right)}}>\frac{\sqrt{n}\left|\bar{x}-p_0\right|}{\sqrt{p_0\left(1-p_0\right)}}\right\} \approx 2\left[1-\Phi\left(\frac{\sqrt{n}\left|\bar{x}-p_0\right|}{\sqrt{p_0\left(1-p_0\right)}}\right)\right]
$$
- Curva Operativa: A differenza del caso varianza sconosciuta (nel quale la curva operativa non era ben definita) questa volta la curva operativa può essere calcolata approssimativamente. Tuttavia i calcoli sono più laboriosi di quelli fatti per il caso del test sulla media di un campione Gaussiano con varianza nota, poiché quando cambia $p$ cambia anche la varianza. Per questo non li riportiamo.