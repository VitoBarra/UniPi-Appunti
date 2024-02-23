---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Statistica Descrittiva - Dati Multivariati
---
in [[Statistica descrittiva|Statistica descrittiva]] i _dati multivariati_ sono vettori di $n$-uple. gli strumenti per l analisi statistica sotto definiti sono con $n =2$ ma si adattano a $n$ piu grande

#### Covarianza definizione (definizione)
_sia_ $(x,y)$ il vettore $((x_{1},y_{1})\dots(x_{n},y_{n}))$ 
_allora_ abbiamo che 
_Covarianza empirica_$$
cov_e(x,y)=\sum^n_{i=1}\frac{(x_i-\overline{x})(y_i-\overline{y})}{n}
$$*covarianza campionaria*$$
cov(x,y)=\sum^n_{i=1}\frac{(x_i-\overline{x})(y_i-\overline{y})}{n-1}
$$
e come per il caso di dati singoli vale l’eguaglianza$$
\sum^n_{i=1}(x_i-\overline{x})(y_i-\overline{y}) = \sum^n_{i=1}x_iy_i-n\overline{x}\overline{y}
$$e di conseguenza$$
cov(x,y)= \sum^n_{i=1}\frac{x_iy_i}{n}-\overline{x}\overline{y}
$$
#### Coefficiente di correlazione (Definizione)
_sia_ $(x,y)$ il vettore $((x_{1},y_{1})\dots(x_{n},y_{n}))$ 
_se_ $\sigma(x) \not= 0$ e $\sigma(y) \not= 0$
_allora_ abbiamo che 
$$
\begin{array}{}
r_{e}(x,y)=\cfrac{cov_e(x,y)}{\sigma_e(x)\sigma_e(y)} &  &  & 
r(x,y)=\cfrac{cov(x,y)}{\sigma(x)\sigma(y)}
\end{array}
$$
espandendo entrambi le formule e semplificando notiamo che $r_{e}(x,y)=r(x,y)$ sono uguali quindi non cambia se si utilizza la versione _empirica_ o _campionaria_ delle formule. Infatti vale che $$
r(x,y)=\cfrac{\sum^n_{i=1}(x_i-\overline{x})(y_i-\overline{y})}{\sqrt{\sum^n_{i=1}(x_i-\overline{x})^2}\sqrt{\sum^n_{i=1}(y_i-\overline{y})^2}}
$$
Dalla [[Diseguaglianza di Schwartz|diseguaglianza di Schwartz]] in $\mathbb{R}^n$ sappiamo che$$
\sum^n_{i=1}|(x_i-\overline{x})(y_i-\overline{y})|\leq \sqrt{\sum^n_{i=1}(x_i-\overline{x})^2}\sqrt{\sum^n_{i=1}(y_i-\overline{y})^2}
$$
e quindi deve valere  $|r(x,y)| \leq 1$ 

il _coefficiente di correlazione_ ci dice quando due valori dei dati sono tra loro _linearmente_ correlati, ovvero quanto al variare di uno varia l altro. 
