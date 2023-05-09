---
type: nota
course: Statistica
topic: 
tags: STAT
---

Prev: [[Statistica (STAT)]]

# Statistica descrittiva
---

la statistica descrittiva riguarda l’analisi di dati senza l’utilizzo di modelli probabilistici

al contrario [[Inferenza statistica|l’inferenza Statistica]] li utilizza

# Concetti di base

- Popolazione : la totalità dei dati
- Campione: una parte della popolazione

dal campione si possono ricavare informazioni sul intera popolazione

### Caratteri (tipi di dato):

Dati Qualitativi:

- ricadono $n$ caratteri fissi
- Frequenza  assoluta: numero di volte della presenza di un carattere
- Frequenza  relativa: numero di volte della presenza di un carattere in percentuale rispetto al totale
- solitamente la frequenza relativa da più informazioni di quella assoluta

Dati Quantitativi:

- ricadono in  $n$ caratteri possibilmente tutti diversi
- non si può parlare di una frequenza dei caratteri

### Grafici

i dati sono più intuitivamente compresi con il supporto dei grafici ad esempio

gli istogrammi ovvero grafici a bastoni dove l altezza del bastone rappresenta la frequenza del dato indicato alla base, sono più adatti a rappresentare dati quantitativi e sono raggruppati in categorie alcuni esempi sono:

normale

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled.png]]

bimodale

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 1.png]]

right-skewed

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 2.png]]

left-skewed

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 3.png]]

i diagrammi a torta dove lo spessore della fetta ne indica la frequenza, sono piu adatti a presentare dati qualitativi

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 4.png]]

# Analisi di dati Numerici

considerando vettori di dati numerici a priori tutti diversi (quindi qualitativi)  per sintetizzare i dati come strumenti abbiamo:

### Media, varianza e deviazione standard

**Empirica**: se su tutta la popolazione $P$ con $n = \#P$

- Media

    $$
    \overline{x}=\sum^n_{i=1}\frac{(x_i-\overline{x})}{n}
    $$

- Varianza

$$
var_e(x)=\sum^n_{i=1}\frac{(x_i-\overline{x})^2}{n}
$$

- Deviazione standard

$$
\sigma_e(x)=\sqrt{var_e(x)}
$$

**Campionaria**: se su un campione $C$                      con $n= \#C$

- Media

$$
\overline{x}=\sum^n_{i=1}\frac{(x_i-\overline{x})}{n}
$$

- Varianza

$$
var(x)=\sum^n_{i=1}\frac{(x_i-\overline{x})^2}{n-1}
$$

- Deviazione standard

$$
\sigma(x)=\sqrt{var(x)}
$$

vale l’euguaglianza

$$
\sum^n_{i=1}(x_i-\overline{x})^2 = \sum^n_{i=1}x_i^2-n\overline{x}^2
$$

da cui deriva la seguente formula

$$
var_e(x)=\sum^n_{i=1}\frac{x^2_i}{n}-\overline{x}^2
$$

la varienza misura quanto i dati si discostano dalla media infatti $var(x)=0 \iff$i dati sono tutti uguali.

In generale vale che

$$
\#\{ x_i:|x_i-\overline{x}|>d\} \leq \frac{\sum_i(x_i-\overline{x})^2}{d^2}
$$

che porta ad un caso particolare della formula di Cebyshev

$$
\frac{\#\{x_i:|x_i-\overline{x}|>d\}}{n} \leq \frac{var_e(x)}{d^2}
$$

formula che mette in relazione la varianza con la percentuale di elementi che differiscono da $\overline{x}$ più di $d$

### Osservazioni Empiriche:

se un istogramma che rappresenta il vettore dei dati $X$ è [[Normale]] allora vale la seguente regola empirica  quindi non dimostrata che ci descrive quale percentuale di dati cade  in quale intervallo

- il $68\%$     circa in $[\overline{x}-\sigma(x),\overline{x}+\sigma(x)]$
- il $95\%$    circa in $[\overline{x}-2\sigma(x),\overline{x}+2\sigma(x)]$
- il $99.7\%$ circa in $[\overline{x}-3\sigma(x),\overline{x}+3\sigma(x)]$

## Funzione di ripartizione empirica

dato un vettore ordinato in modo cresce $x$

la funzione di ripartizione empirica $F_e(.)$  su $\R$  è definita come

$$
F_e(t)=\frac{\#\{x_i|x_i\leq t\}}{n}
$$

Osservazioni: questa funzione

- è debolmente crescente
- per $\forall t <x_1$ è $F(t)=0$
- per $\forall t \geq x_n$ è $F(t)  = 1$

### Esempio:

il vettore di dati $(1.2,-0.7,3.4,1.6,2.1)$ quindi riordinando $(-0.7,1.2,1.6,2.1,3.4)$ e si traccia la funzione

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 5.png]]

nel caso di un vettore con 65 elementi gli scalini sono molto meno “visibili”

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 6.png]]

---

## Percentile e Quantile

il percentile  $k-mo$ è un numero $t$ tale che in un vettore di dati

$$
\frac{k}{100} \leq t
$$

$$
1-\frac{k}{100} \geq t
$$

mentre $\beta =\frac{k}{100}$ è detto $\beta-quantile$

alcuni quantili hanno dei nomi particolari:

- $0.25-quantile$ è detto $1°$ quartile
- $0.50-quantile$ è detto $2°$ quartile o mediana
- $0.75-quantile$ è detto $3°$ quartile

 per rappresentare graficamente si utilizza il **box-plot** sovrapponendo ad una linea tra che va dal minimo al massimo valore un rettangolo che va dal $1°$ quartile al $3°$ quartile con una linea sulla mediana

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 7.png]]

## Dati Multipli

i dati multipli sono vettori di $n$-uple ma qui gli esempi sono per $n =2$

**Empirica**: se su tutta la popolazione $P$ con $n = \#P$

- Covarianza

$$
cov_e(x,y)=\sum^n_{i=1}\frac{(x_i-\overline{x})(y_i-\overline{y})}{n}
$$

**Campionaria**: se su un campione $C$                      con $n= \#C$

- Covarianza

$$
cov_e(x,y)=\sum^n_{i=1}\frac{(x_i-\overline{x})(y_i-\overline{y})}{n-1}
$$

come per il caso di dati singoli vale l’eguaglianza

$$
\sum^n_{i=1}(x_i-\overline{x})(y_i-\overline{y}) = \sum^n_{i=1}x_iy_i-n\overline{x}\overline{y}
$$

e di conseguenza

$$
cov(x,y)= \sum^n_{i=1}\frac{x_iy_i}{n}-\overline{x}\overline{y}
$$

## Coefficiente di correlazione

in più per capire quanto due dati siano correlai si può calcolare il coefficiente di correlazione supponendo $\sigma(x) \not= 0$ e $\sigma(y) \not= 0$



$$
r(x,y)=\frac{cov_e(x,y)}{\sigma_e(x)\sigma_e(y)}
$$

$$
r(x,y)=\frac{cov(x,y)}{\sigma(x)\sigma(y)}
$$

espandendo entrambi le formule e semplificando notiamo che in generale vale la formula

$$
r(x,t)=\frac{\sum^n_{i=1}(x^i-\overline{x})(y^i-\overline{y})}{\sqrt{\sum^n_{i=1}(x^i-\overline{x})^2}\sqrt{\sum^n_{i=1}(y^i-\overline{y})^2}}
$$

### Proprietà:

- $r(x,y) \leq 1$ grazie alla diseguaglianza di Schwartz in $\R^n$ sappiamo che

$$
\sum^n_{i=1}|(x_i-\overline{x})(y_i-\overline{y})|\leq \sqrt{\sum^n_{i=1}(x_i-\overline{x})^2}\sqrt{\sum^n_{i=1}(y_i-\overline{y})^2}
$$

## Retta di regressione

la retta di regressione è la retta su cui tanto più il coefficiente di correlazione in valore assoluto $|r(x,y)|$ è vicino a 1 più i dati sono distribuiti sulla retta in più in segno di $r(x,y)$ determina il segno del coefficiente angolare della retta

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 8.png]]

### Esempi:

$r(x,y)\approx-0.78, a^* \approx 1.76,b^* \approx-28.7$

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 9.png]]

$r(x,y)\approx-0.2422, a^* \approx ??,b^* \approx??$

![[Raccolta UniPi INF/Note/2° Anno/Statistica/Media/Untitled 10.png]]
