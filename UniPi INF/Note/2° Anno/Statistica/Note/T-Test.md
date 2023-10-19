---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# T-Test
---
il _T-test_ e' un [[Test Statistici|Test statistico]] sulla [[Idd - Media Campionaria|media]] di un [[Campione Statistico|campione]] [[Variabili aleatorie Gaussiane|Gaussiano]] con [[Idd - varianza campionaria|varianza]] sconosciuta

Consideriamo ora il caso (più realistico) di campione gaussiano di cui non conosciamo la deviazione standard: si chiama T-test il test sulla media di un campione Gaussiano con varianza sconosciuta.
Sia $X_1, \ldots X_n$ un campione aleatorio di legge gaussiana $N\left(m, \sigma^2\right)$, e ricordiamo la notazione
$$
\bar{X}_n=\frac{X_1+\cdots+X_n}{n}, \quad S_n^2=\frac{1}{n-1} \sum_{i=1}^n\left(X_i-\bar{X}_n\right)^2 .
$$

Il procedimento per formulare il test è analogo a quanto visto per lo Z-test, ma questa volta il punto di partenza è il fatto che, se la media è $m$, la variabile $T=\sqrt{n}\left(\bar{X}_n-m\right) / S_n$ ha densità di Student $T(n-1)$. Consideriamo il test bilatero dell'ipotesi
$$
\left.\left.\mathscr{H}_0\right) m=m_0 \quad \text { contro } \quad \mathscr{H}_1\right) m \neq m_0 \text {. }
$$
- Formulazione del test: Anche in questo caso cerchiamo una regione critica della forma $C=\left\{\left|\bar{X}-m_0\right|>d\right\}$. Imponiamo $\mathbb{P}_{m_0}(C)=\alpha$ e usiamo la statistica $T=\sqrt{n}\left(\bar{X}_n-m\right) / S$ :
$$
\mathbb{P}_{m_0}\left\{\left|\bar{X}-m_0\right|>d\right\}=\mathbb{P}_{m_0}\left\{\frac{\sqrt{n}}{S}\left|\bar{X}-m_0\right|>\frac{d \sqrt{n}}{S}\right\}=\mathbb{P}\left\{|T|>\frac{d \sqrt{n}}{S}\right\}=\alpha
$$
e quindi $d \sqrt{n} / S_n=\tau_{1-\frac{\alpha}{2}, n-1}$, dove $\tau_{\beta, k}$ è il $\beta$-quantile della densità di Student $T(k)$. La regione critica a livello $\alpha$ è quindi
$$
C=\left\{\sqrt{n} \frac{\left|\bar{X}-m_0\right|}{S}>\tau_{\left(1-\frac{a}{2}, n-1\right)}\right\} .
$$- p-value: Procedendo in modo analogo al caso $\sigma$ nota, ma usando la statistica $T=\sqrt{n}\left(\bar{X}_n-\right.$ $m) / S$, otteniamo la formula per il $p$-value dei dati $\left(x_1, \ldots x_n\right)$ :
$$
\mathbb{P}_{m_0}\left\{\sqrt{n} \frac{\left|\bar{X}-m_0\right|}{S}>\frac{\sqrt{n}}{s}\left|\bar{x}-m_0\right|\right\}=2\left[1-F_{n-1}\left(\frac{\sqrt{n}}{s}\left|\bar{x}-m_0\right|\right)\right],
$$
dove $\bar{x}$ e $\bar{s}$ sono rispettivamente la media campionaria e la varianza campionaria di $\left(x_1, \ldots x_n\right)$ e dove $F_k$ è la c.d.f. della variabile $T(k)$ (che i software sono in grado di calcolare con ottima approssimazione).
- Curva operativa: In questo caso, la curva operativa non è ben definita. Il motivo è il seguente: se il valore atteso delle variabili è $m_0$, qualunque sia $\sigma$ la variabile $T=\sqrt{n}\left(\bar{X}_n-\right.$ $\left.m_0\right) / S$ ha densità di Student $T(n-1)$, ma se la media è diversa da $m_0$ la densità di $T$ non dipende solo da $m$ ma anche da $\sigma$, dunque non possiamo applicare la definizione.

In modo simile si ottengono le formule per il test unilatero. Nel caso
$$
\left.\left.\mathscr{H}_0\right) m \leq m_0 \quad \text { contro } \quad \mathscr{H}_1\right) m>m_0
$$
la regione critica a livello $\alpha$ e il $p$-value sono dati rispettivamente da
$$
\begin{aligned}
& C=\left\{\sqrt{n} \frac{\left(\bar{X}-m_0\right)}{S_n}>\tau_{1-\alpha, n-1}\right\}, \\
& \bar{\alpha}\left(x_1, \ldots, x_n\right)=\mathbb{P}_{m_0}\left(\sqrt{n} \frac{\left(\bar{X}-m_0\right)}{S_n}>\frac{\sqrt{n}}{s}\left(\bar{x}-m_0\right)\right)=1-F_{n-1}\left(\frac{\sqrt{n}}{s}\left(\bar{x}-m_0\right)\right) .
\end{aligned}
$$

Discorso analogo per $\left.\mathscr{K}_0\right) m \geq m_0$.