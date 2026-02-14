---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---
# Funzione di ripartizione empirica 
---
**_funzione di ripartizione empirica_** è una [[funzioni|funzione]] che descrive la distribuzione di un campione di dati numerici ed è l’analogo campionario della [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di distribuzione cumulativa]] di una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] discreta.

__sia__ $x=(x_1,\dots,x_n)$ un vettore di dati ordinato in modo crescente. 
__allora__ la funzione di ripartizione empirica $F_e(.):\mathbb{R}\rightarrow\mathbb{R}$ è definita come$$
F_e(t)=\frac{\#\{x_i\mid x_i\le t\}}{n}
$$questa definizione può essere vista come la [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]] di una distribuzione discreta che assegna probabilità $\frac{1}{n}$ a ciascun dato osservato, infatti$$F_e(t)=\sum_{x_i\le t}\frac{1}{n}$$per questa [[Funzioni|funzione]] vale che
- è debolmente crescente
- per $\forall t<x_1$ è $F_e(t)=0$
- per $\forall t\ge x_n$ è $F_e(t)=1$
come nel caso della [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione discreta]], la funzione è a gradini: al crescere di $t$ ogni volta che incontra un dato osservato produce un salto.

se un valore compare una sola volta il salto vale $\frac{1}{n}$, mentre se lo stesso valore compare $m$ volte il salto vale$$\frac{m}{n}$$quindi la funzione di ripartizione empirica può essere interpretata come la funzione di distribuzione cumulativa associata alla distribuzione discreta che attribuisce uguale probabilità a tutte le osservazioni del campione.