---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Statistica descrittiva - Dati Numerici
---
Nella [[Statistica descrittiva|statistica descrittiva]] spesso si ha a che fare con quantità numeri e c è la necessita di sintetizzare _queste quantità_ con dei numeri che li descrivono


considerando vettori di dati numerici a priori tutti diversi (quindi _[[Statistica descrittiva|qualitativi]]_)  per sintetizzare i dati come strumenti abbiamo:

### Quantità che sintetizzano i dati 
Alcuni valori utili sono i seguenti e possono essere di due tipi a seconda della quantità di dati a cui abbiamo a disposizione.
- **Empirica**: se su tutta la popolazione $P$ 
- **Campionaria**: se su un campione $C$
considerando sempre un vettore numeri $x=(x_{1},\dots x_{n})$ abbiamo che

#### Media (definizione)
la _Media_ campionaria ($n= |C|$) o _empirica_ ($n = |P|$) è il numero$$
    \overline{x}=\sum^n_{i=1}\frac{x_i}{n}
    $$
#### Varianza (definizione)
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

#### Deviazione standard (definizione)
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
