---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Statistica Descrittiva - Dati Numerici
---
Nella [[Statistica descrittiva|statistica descrittiva]] spesso si ha a che fare con quantità numeri e c è la necessita di sintetizzare _queste quantità_ con dei numeri che li descrivono


considerando vettori di dati numerici a priori tutti diversi (quindi _[[Statistica descrittiva|qualitativi]]_)  per sintetizzare i dati come strumenti abbiamo:

### Quantità che sintetizzano i dati 
Alcuni valori utili sono i seguenti e possono essere di due tipi a seconda della quantità di dati a cui abbiamo a disposizione.
- **Empirica**: se su tutta la popolazione $P$ 
- **Campionaria**: se su un campione $C$
considerando sempre un vettore numeri $x=(x_{1},\dots x_{n})$ abbiamo che

##### Media (definizione)
la _Media_ campionaria ($n= |C|$) o _empirica_ ($n = |P|$) è il numero$$
    \overline{x}=\sum^n_{i=1}\frac{x_i}{n}
    $$
##### Varianza (definizione)
la _Varianza empirica_$$
var_e(x)=\sum^n_{i=1}\frac{(x_i-\overline{x})^2}{n}
$$mentre la _Varianza campionaria_ è

$$
var(x)=\sum^n_{i=1}\frac{(x_i-\overline{x})^2}{n-1}
$$
la _varianza_ misura quanto i dati si discostano dalla _media_ infatti $var(x)=0 \iff$i dati sono tutti uguali.

possiamo riscrivere la formulare della _varianza_ osservando che vale l’eguaglianza$$
\sum^n_{i=1}(x_i-\overline{x})^2 = \sum^n_{i=1}x_i^2-n\overline{x}^2
$$da cui dividendo per $n$ deriva la seguente formula$$
var_e(x)=\sum^n_{i=1}\frac{x^2_i}{n}-\overline{x}^2
$$

##### Deviazione standard (definizione)
la _Deviazione standard empirica_  è il numero$$
\sigma_e(x)=\sqrt{var_e(x)}
$$
mentente la _Deviazione standard campionaria_ è$$
\sigma(x)=\sqrt{var(x)}
$$
questa viene anche chiamata _scarto quadratico medio_.




#### Proprietà
la _varianza_ misura la _dispersione_ dei dati rispetto alla media e in generale 
_siano_ $x$ dei dati e $d$ un _numero positivo qualsiasi_ 
_vale che_
$$
\#\{ x_i:|x_i-\overline{x}|>d\} \leq \frac{\sum_i(x_i-\overline{x})^2}{d^2}
$$
dove $\#$ indica la [[Cardinalità di un insieme|Cardinalità]] del [[Insiemi Matematici|insieme]] che porta ad un caso particolare della [[Diseguaglianza di Cebyshev|diseguaglianza di Cebyshev]]

$$
\frac{\#\{x_i:|x_i-\overline{x}|>d\}}{n} \leq \frac{var_e(x)}{d^2}
$$

formula che mette in relazione la _varianza_ con la percentuale di elementi che differiscono dalla _media_ $\overline{x}$ _più_ di $d$

##### Osservazioni Empiriche
se un _istogramma_ che rappresenta il vettore dei dati $X$ è [[Normale]] allora vale la seguente regola _empirica_  che ci descrive quale percentuale di dati cade in quale intervallo

- il $68\%$     circa in $[\overline{x}-\sigma(x),\overline{x}+\sigma(x)]$
- il $95\%$    circa in $[\overline{x}-2\sigma(x),\overline{x}+2\sigma(x)]$
- il $99.7\%$ circa in $[\overline{x}-3\sigma(x),\overline{x}+3\sigma(x)]$
la regola è stata formulata guardando gli esperimenti e non è matematicamente _dimostrabile_
#### Funzione di ripartizione empirica
_sia_ $x$ un vettore ordinato in modo cresce di dati 

la funzione di ripartizione empirica $F_e(.): \mathbb{R} \rightarrow \mathbb{R}$  su $\mathbb{R}$  è definita come$$
F_e(t)=\frac{\#\{x_i|x_i\leq t\}}{n}
$$
per questa funzione vale che 
- è debolmente crescente
- per $\forall t <x_1$ è $F_{e}(t)=0$
- per $\forall t \geq x_n$ è $F_{e}(t)  = 1$
è una funzione a "gradoni" che al aumentare di $t$ ogni volta che incontra un dato fa un salto di $\cfrac{1}{n}$ se ci sono $m$ dati uguali, il salto è di $\frac{m}{n}$ 

alcuni esempi sono:
il vettore di dati $(1.2,-0.7,3.4,1.6,2.1)$ quindi riordinando $(-0.7,1.2,1.6,2.1,3.4)$ e si traccia la funzione
	![[UniPi INF/Note/2° Anno/Statistica/Media/Untitled 5.png]]

nel caso di un vettore con 65 elementi gli scalini sono molto meno “visibili”
	![[UniPi INF/Note/2° Anno/Statistica/Media/Untitled 6.png]]

#### Percentile e Quantile
_sia_ $x$ un vettore di dati e un numero $k\in (0,100)$ 
Il _percentile_  $k-mo$  di $x$ è un numero $t$ _tale che_  ci sono almeno $k\% \leq t$ dati che soddisfano l equazione e almeno $1-k\% \geq t$  dati che soddisfano l equazione

il _percentile_ non sempre è unicamente determinato ci possono essere piu punto che soddisfano la condizione e per _convenzione_ si prende il punto di mezzo.


invece viene chiamato _quantile_ il numero  $\beta =\cfrac{k}{100} (k\%)$ ed è detto $\beta-$quantile

alcuni _quantili_ hanno dei nomi particolari:
- $0.25-quantile$ è detto $1°$ __quartile__
- $0.50-quantile$ è detto $2°$ __quartile__ o _mediana_
- $0.75-quantile$ è detto $3°$ __quartile__

 per rappresentare graficamente si utilizza il **box-plot** sovrapponendo ad una linea che va dal minimo al massimo dei valori dei dati un rettangolo che va dal $1°$ quartile al $3°$ quartile con una linea sulla _mediana_

![[UniPi INF/Note/2° Anno/Statistica/Media/Untitled 7.png]]

## Dati Multipli
i dati multipli sono vettori di $n$-uple. gli strumenti per l analisi statistica sotto definiti sono con $n =2$ ma si adattano a $n$ piu grande


##### Covarianza definizione (definizione)
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
##### Coefficiente di correlazione (Definizione)
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

#### Retta di regressione
uno strumento utile per i dati multivariati è la _retta di regressione_ questa è la [[Retta|retta]] su cui tanto più il coefficiente di correlazione in valore assoluto $|r(x,y)|$ è vicino a 1 più i dati sono distribuiti sulla retta. il segno di $r(x,y)$ determina il segno del [[Retta|coefficiente angolare]] della _retta_.
Per calcolare la _retta di regressione_ vogliamo calcolare la quantità$$\inf_{a,b\in \mathbb{R}^{2}} \sum^{n}_{i=1}(y_{i}-a-bx_{i})^{2}$$ovvero siamo approssimando i valori di $y_{i}$ con una combinazione lineare affine $a+bx_{i}$. l _inf_ equivale al minimo e vale il seguente teorema

#### Teorema e Definizione retta di regressione
il minimo volare $(a,b)\in \mathbb{R}^{2}$ della quantità $\sum^{n}_{i=1}(y_{i}-a-bx_{i})^{2}$ si puo calcolare con $b^* = \cfrac{cov(x,y)}{var(x)}$ e $a^* = -b^*\overline{x} + \overline{y}$ e la retta $$y =a^*+b^*x$$è chiamata _retta di regressione_

in piu vale l eguaglianza $$\sum^{n}_{i=1}(y_{i}-a^*-b^*x_{i})^{2}= \sum^{n}_{i=1}(y_{i} -\overline{y})(1-r(x,y)^{2})$$che ci dice che i dati sono allineati sulla retta tanto piu $|r(x,y)|$ si avvicina ad $1$

>[!note]
>nella formula di $b^{*}$ è indifferente l utilizzo di formule empiriche o campionarie

###### Dimostrazione
_sia_ $Q(a,b)=\sum^{n}_{i=1}(y_{i}-a-bx_{i})^{2}$ che è una [[Funzioni|funzione]] [[Continuità di una funzione|continua]] ($C^{\infty}$) e che tende ad $Q(a,b)\to\infty$ quando $|a|,|b| \to \infty$
_Vogliamo dimostrare_ che il punto di [[Minimi e Massimi|minimo]] di $Q(a,b)$ é il punto $Q(b^{*},a^{*})$ con  $b^* = \cfrac{cov(x,y)}{var(x)}$ e $a^* = -b^*\overline{x} + \overline{y}$ 

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



##### Esempi
$r(x,y)\approx-0.78, a^* \approx 1.76,b^* \approx-28.7$
	![[UniPi INF/Note/2° Anno/Statistica/Media/Untitled 9.png]]

$r(x,y)\approx-0.2422, a^* \approx ??,b^* \approx??$
	![[UniPi INF/Note/2° Anno/Statistica/Media/Untitled 10.png]]
