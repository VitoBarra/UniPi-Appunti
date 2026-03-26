---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie notevoli - Beta
---
La distribuzione **Beta** e una [[Probabilita sui numeri Reali#Densità di probabilità (Definizione)|densita di probabilita]] continua definita sull'intervallo $[0,1]$.

Siano $\alpha,\beta \in [0,\infty]$ i parametri della distribuzione
Si dice che una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] $X$ ha distribuzione Beta di parametri $\alpha,\beta$, e si scrive
$$
X\sim \mathrm{Beta}(\alpha,\beta),
$$
se ha densita
$$
f_X(x)=
\begin{cases}
\dfrac{x^{\alpha-1}(1-x)^{\beta-1}}{B(\alpha,\beta)} & 0\leq x\leq 1 \\
0 & \text{altrove}
\end{cases}
$$

dove $B(\alpha,\beta)$ è la **funzione Beta** ed il **fattore di normalizzazione** che serve a fare in modo che la densità abbia area totale uguale a $1$ è definita come $$B(\alpha,\beta)=\int_0^1 x^{\alpha-1}(1-x)^{\beta-1}\,dx$$ e risolvendo l [[Integrali|integrale]] si ha che è esprimibili con la [[Funzione Gamma di Eulero|funzione Gamma]]: $$B(\alpha,\beta)= \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}$$

si  mostra che è una densità valida notando che 
$$
\int_0^1 f_X(x)\,dx
=
\frac{1}{B(\alpha,\beta)}
\int_0^1 x^{\alpha-1}(1-x)^{\beta-1}\,dx
=1.
$$


## Supporto e forma

La distribuzione Beta vive solo in $[0,1]$, quindi e naturale quando si descrivono variabili limitate tra $0$ e $1$.

La forma dipende dai parametri:
- se $\alpha=\beta=1$, la distribuzione e uniforme su $[0,1]$;
- se $\alpha>\beta$, la massa si concentra di piu verso $1$;
- se $\alpha<\beta$, la massa si concentra di piu verso $0$;
- se $\alpha,\beta>1$, la densita tende ad avere una forma unimodale interna;
- se $\alpha,\beta<1$, la densita tende a concentrarsi vicino agli estremi $0$ e $1$.

![[IMG - Variabili Aleatorie notevoli - Beta grafici con parametri diversi.png]]

## Media e varianza

Se $X\sim \mathrm{Beta}(\alpha,\beta)$, allora
$$
\mathbb{E}[X]=\frac{\alpha}{\alpha+\beta}
$$
e
$$
\mathrm{Var}(X)=\frac{\alpha\beta}{(\alpha+\beta)^2(\alpha+\beta+1)}.
$$

Quindi:
- $\alpha$ e $\beta$ controllano la posizione media;
- la loro somma $\alpha+\beta$ controlla quanto la distribuzione e concentrata.

## Moda

Se $\alpha>1$ e $\beta>1$, la moda vale
$$
\frac{\alpha-1}{\alpha+\beta-2}.
$$

## Momenti

La distribuzione Beta ammette tutti i [[Variabili aleatoria - Valore atteso|momenti]].

In particolare, per $n\geq 1$,
$$
\mathbb{E}[X^n]
=
\frac{B(\alpha+n,\beta)}{B(\alpha,\beta)}.
$$

Usando la relazione con la funzione Gamma, si puo anche scrivere
$$
\mathbb{E}[X^n]
=
\frac{\Gamma(\alpha+n)\Gamma(\alpha+\beta)}
{\Gamma(\alpha)\Gamma(\alpha+\beta+n)}.
$$

## Relazione con altre distribuzioni

La distribuzione Beta:
- e la versione su $[0,1]$ della famiglia continua con due parametri di forma;
- e strettamente collegata alla [[Variabili Aleatorie Notevoli - Gamma|distribuzione Gamma]];
- e il caso bidimensionale della [[Variabili aleatorie Notevoli - Dirichlet|distribuzione di Dirichlet]].

## Uso statistico

La distribuzione Beta e molto usata in statistica bayesiana come distribuzione a priori per una probabilita $p\in[0,1]$, ad esempio nel modello binomiale.

>[!tip]
> Se si vuole modellare una probabilita ignota, la Beta e spesso la scelta naturale perche e definita proprio su $[0,1]$ e ha forma molto flessibile.
