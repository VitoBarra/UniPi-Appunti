---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
topic:
---
# Test Statistici su distribuzioni gaussiane - Varianza
---
[[Test Statistici|Test statistico]] sulla varianza di un campione gaussiano. Come per gli [[Intervalli di fiducia|intervalli di fiducia]], ci occupiamo solo del caso unilatero,$$
\left.\left.\mathscr{H}_0\right) \sigma^2 \leq \sigma_0^2 \quad \text { contro } \quad \mathscr{H}_1\right) \sigma^2>\sigma_0^2,
$$ricordando che, se il campione $X_1, \ldots, X_n$ è formato da variabili Gaussiane con varianza $\sigma^2$, la variabile $\sum_{i=1}^n \frac{\left(X_i-\bar{X}\right)^2}{\sigma^2}$ ha densità $\chi^2(n-1)$.

Formulazione del test: Risulta naturale considerare una regione critica della forma $C=$ $\left\{\sum_i\left(X_i-\bar{X}\right)^2>d\right\}$ con $d$ tale che si abbia, per $\sigma \leq \sigma_0$,
$$
\mathbb{P}_\sigma\left\{\sum_{i=1}^n\left(X_i-\bar{X}\right)^2>d\right\} \leq \alpha .
$$

È facile provare che la probabilità sopra scritta cresce con $\sigma$ e, cercando una regione critica più piccola possibile (purché di livello $\alpha$ ) si ottiene
$$
\mathbb{P}_{\sigma_0}\left\{\sum_{i=1}^n\left(X_i-\bar{X}\right)^2>d\right\}=\mathbb{P}_{\sigma_0}\left\{\frac{\sum_{i=1}^n\left(X_i-\bar{X}\right)^2}{\sigma_0^2}>\frac{d}{\sigma_0^2}\right\}=\alpha,
$$
e questo ci porta a scegliere $\frac{d}{\sigma_0^2}=\chi_{1-\alpha, n-1}^2$. Si ottiene quindi la regione critica di livello $\alpha$
$$
C=\left\{\frac{\sum_{i=1}^n\left(X_i-\bar{X}\right)^2}{\sigma_0^2}>\chi_{1-\alpha, n-1}^2\right\}
$$$p$-value: Il $p$-value dei dati $\left(x_1, \ldots x_n\right)$ è
$$
\mathbb{P}_{\sigma_0}\left\{\frac{\sum_{i=1}^n\left(X_i-\bar{X}\right)^2}{\sigma_0^2}>\frac{\sum_{i=1}^n\left(x_i-\bar{x}\right)^2}{\sigma_0^2}\right\}=1-G_{n-1}\left(\frac{\sum_{i=1}^n\left(x_i-\bar{x}\right)^2}{\sigma_0^2}\right),
$$
dove $\operatorname{con} G_n$ si indica la c.d.f. della variabile $\chi^2(n)$.
Curva operativa: La curva operativa è
$$
\begin{aligned}
\beta(\sigma) & =\mathbb{P}_\sigma\left\{\frac{\sum_{i=1}^n\left(X_i-\bar{X}\right)^2}{\sigma_0^2} \leq \chi_{1-\alpha, n-1}^2\right\} \\
& =\mathbb{P}_\sigma\left\{\frac{\sum_{i=1}^n\left(X_i-\bar{X}\right)^2}{\sigma^2} \leq \frac{\sigma_0^2}{\sigma^2} \chi_{1-\alpha, n-1}^2\right\}=G_{n-1}\left(\frac{\sigma_0^2}{\sigma^2} \chi_{1-\alpha, n-1}^2\right) .
\end{aligned}
$$

Naturalmente, se si considera un test unilatero nell'altra direzione, cioè dell'ipotesi $\left.\mathscr{H}_0\right) \sigma^2 \geq$ $\sigma_0^2$, si rovesciano tutte le diseguaglianze ed il quantile $\chi_{1-\alpha, n-1}^2$ è cambiato in $\chi_{\alpha, n-1}^2$.