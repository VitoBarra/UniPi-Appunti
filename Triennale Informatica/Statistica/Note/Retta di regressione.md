---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Retta di regressione
---
in [[Statistica descrittiva|Statistica descrittiva]] la _retta di regressione_ è uno strumento utile per i [[Statistica Descrittiva - Dati Multivariati|dati multivariati]] è la _retta di regressione_ questa è la [[Retta|retta]] su cui tanto più il coefficiente di correlazione in valore assoluto $|r(x,y)|$ è vicino a 1 più i dati sono distribuiti sulla retta. il segno di $r(x,y)$ determina il segno del [[Retta|coefficiente angolare]] della _retta_.
Per calcolare la _retta di regressione_ vogliamo calcolare la quantità$$\inf_{a,b\in \mathbb{R}^{2}} \sum^{n}_{i=1}(y_{i}-a-bx_{i})^{2}$$ovvero siamo approssimando i valori di $y_{i}$ con una combinazione lineare affine $a+bx_{i}$. l _inf_ equivale al minimo e vale il seguente teorema

#### Teorema e Definizione retta di regressione
il minimo volare $(a,b)\in \mathbb{R}^{2}$ della quantità $\sum^{n}_{i=1}(y_{i}-a-bx_{i})^{2}$ si puo calcolare con $b^* = \cfrac{cov(x,y)}{var(x)}$ e $a^* = -b^*\overline{x} + \overline{y}$ e la retta $$y =a^*+b^*x$$è chiamata _retta di regressione_

in piu vale l eguaglianza $$\sum^{n}_{i=1}(y_{i}-a^*-b^*x_{i})^{2}= \sum^{n}_{i=1}(y_{i} -\overline{y})(1-r(x,y)^{2})$$che ci dice che i dati sono allineati sulla retta tanto piu $|r(x,y)|$ si avvicina ad $1$

>[!note]
>nella formula di $b^{*}$ è indifferente l utilizzo di formule empiriche o campionarie

###### Dimostrazione
_sia_ $Q(a,b)=\sum^{n}_{i=1}(y_{i}-a-bx_{i})^{2}$ che è una [[Funzioni|funzione]] [[Continuità di una funzione|continua]] ($C^{\infty}$) e che tende ad $Q(a,b)\to\infty$ quando $|a|,|b| \to \infty$
_Vogliamo dimostrare_ che il punto di [[Massimi e minimi|minimo]] di $Q(a,b)$ é il punto $Q(b^{*},a^{*})$ con  $b^* = \cfrac{cov(x,y)}{var(x)}$ e $a^* = -b^*\overline{x} + \overline{y}$ 

un punto è di minimo se la sua [[Derivate|derivata]] è nulla. deve quindi valere $\frac{\partial Q}{\partial a}=0$ e $\frac{\partial Q}{\partial b}=0$ e bisogna risolvere$$\begin{cases}
\sum_{i}y_{i}-na-b\sum_{i}x_{i} & =0 \\
\sum_{i}x_{i}y_{i}-a\sum_{i}x_{i}-b\sum_{i}x_{i}^{2} & =0
\end{cases}$$
e dividendo per $n$ si arrivera alle equazioni $$\begin{cases}
a+b\overline{x}=\overline{y} \\
a\overline{x}+b\sum_{i}\cfrac{x_{i}^{2}}{n}=\sum \cfrac{x_{i}y_{i}}{n}
\end{cases}$$
e risolvendo il sistema ottoniamo$$\begin{cases}
a^{*}=-b^{*}\overline{x}+\overline{y} \\
b^{*}=\cfrac{\sum_{i}\cfrac{x_{i}y_{i}}{n}-\overline{x}\overline{y}}{\sum_{i}\cfrac{x_{i}^{2}}{n}-\overline{x}^{2}}=\cfrac{cov_{e}(x,y)}{var_{e}(x)}
\end{cases}$$
inserendo i valori si ottiene $$Q(a^{*},b^{*})= \sum_{i=1}^{n}(y_{i}- \overline{y})(1-r(x,y)^{2})$$
##### Esempi
$r(x,y)\approx-0.78, a^* \approx 1.76,b^* \approx-28.7$
	![[Statistica/Media/Untitled 9.png]]

$r(x,y)\approx-0.2422, a^* \approx ??,b^* \approx??$
	![[UniPi-Appunti/Triennale Informatica/Statistica/Media/Untitled 10.png]]
