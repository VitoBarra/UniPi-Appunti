---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Z-score
---
Lo **z-score** e una trasformazione che permette di esprimere un valore rispetto alla sua [[Statistica descrittiva - Dati Numerici#Media (definizione)|media]], misurando lo scarto in unita di [[Statistica descrittiva - Dati Numerici#Deviazione standard (definizione)|deviazione standard]].

L'idea e trasformare un valore qualunque in un numero puro, cioe indipendente dall'unita di misura dei dati, che dica quanto quel valore e lontano dal centro della distribuzione.

#### Definizione empirica
Dato un vettore di dati numerici $x=(x_1,\dots,x_n)$, con [[Statistica descrittiva - Dati Numerici#Media (definizione)|media]] $\overline{x}$ e [[Statistica descrittiva - Dati Numerici#Deviazione standard (definizione)|deviazione standard]] $\sigma(x)>0$, lo **z-score** del dato $x_i$ e
$$
z_i=\frac{x_i-\overline{x}}{\sigma(x)}
$$

Se si usa la deviazione standard empirica $\sigma_e(x)$, si ottiene invece
$$
z_i=\frac{x_i-\overline{x}}{\sigma_e(x)}
$$

Il valore $z_i$ indica quante deviazioni standard separano $x_i$ dalla media:
- $z_i=0$ significa che $x_i$ coincide con la media;
- $z_i>0$ significa che $x_i$ e sopra la media;
- $z_i<0$ significa che $x_i$ e sotto la media;
- $|z_i|$ grande significa che $x_i$ e lontano dalla media rispetto alla dispersione dei dati.

Questa trasformazione e detta **standardizzazione** dei dati.

#### Standardizzazione di una variabile aleatoria
Sia $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] con [[Variabili aleatoria - Valore atteso|valore atteso]] $\mu$ e [[Variabili aleatorie - Varianza|varianza]] $\sigma^2>0$.

La variabile standardizzata associata a $X$ e
$$
Z=\frac{X-\mu}{\sigma}
$$

Questa trasformazione centra la variabile in $0$ e la riscrive rispetto alla sua deviazione standard.

Infatti vale:
$$
\mathbb{E}[Z]=\mathbb{E}\left[\frac{X-\mu}{\sigma}\right]
=\frac{\mathbb{E}[X]-\mu}{\sigma}=0
$$

e
$$
Var(Z)=Var\left(\frac{X-\mu}{\sigma}\right)
=\frac{1}{\sigma^2}Var(X)=1
$$

quindi lo z-score trasforma una variabile con media $\mu$ e varianza $\sigma^2$ in una variabile con media $0$ e varianza $1$.


###### **Caso gaussiano:** 
Se $X$ e una [[Variabili Aleatorie Notevoli - Gaussiana|variabile gaussiana]] con distribuzione $N(\mu,\sigma^2)$, allora la sua standardizzazione e una gaussiana standard:
$$
Z=\frac{X-\mu}{\sigma}\sim N(0,1)
$$

Questo permette di ricondurre i calcoli su una gaussiana qualunque ai calcoli sulla [[Variabili Aleatorie Notevoli - Gaussiana|gaussiana standard]] $\Phi$.

Per esempio:
$$
\mathcal{P}\{a<X<b\}
=
\mathcal{P}\left\{\frac{a-\mu}{\sigma}<Z<\frac{b-\mu}{\sigma}\right\}
=
\Phi\left(\frac{b-\mu}{\sigma}\right)-\Phi\left(\frac{a-\mu}{\sigma}\right)
$$

#### Interpretazione statistica
Lo z-score e utile quando si vuole capire se un valore osservato e compatibile con una distribuzione di riferimento oppure se risulta anomalo rispetto alla variabilita attesa.

In generale, se la distribuzione di riferimento e circa gaussiana:
- valori con $|z|\leq 1$ sono vicini alla media;
- valori con $|z|\approx 2$ sono relativamente rari;
- valori con $|z|\geq 3$ sono molto lontani dalla media.

Queste soglie non sono regole assolute: dipendono dal modello probabilistico assunto e dal contesto applicativo.

>[!note]
>Questa interpretazione e collegata alla regola empirica vista in [[Statistica descrittiva - Dati Numerici#Osservazioni Empiriche|statistica descrittiva per dati numerici]]: in dati circa gaussiani, la maggior parte dei valori cade entro poche deviazioni standard dalla media.
