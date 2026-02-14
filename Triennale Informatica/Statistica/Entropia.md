---
Course: "[[Teoria del informazione (TDI)]]"
tags:
  - TDI
Area:
topic:
SubTopic:
---

# Entropia
---
L'**entropia** $H$ è una funzione che misura l'incertezza media associata ad una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] $X$. Formalmente quantifica la quantità di informazione prodotta dall'osservazione dell'esito di $X$.

Sia $X$ una variabile aleatoria discreta con alfabeto $\mathcal{X}$ e distribuzione di probabilità $p(x)=P(X=x)$. L'entropia di $X$ è definita come  
$H(X)=-\sum_{x\in\mathcal{X}} p(x)\log p(x)$

- $p(x)$ probabilità dell'esito $x$
- il logaritmo determina l'unità di misura dell'informazione
- se $\log_2$ l'unità è il [[bit|bit]]
- se $\log_e$ l'unità è il [[nat|nat]]

Interpretazione informativa:
- $-\log p(x)$ rappresenta l'[[informazione (teoria dell'informazione)|informazione]] associata all'evento $x$
- $H(X)$ è il valore atteso dell'informazione: $H(X)=\mathbb{E}[-\log p(X)]$

Proprietà fondamentali:
- non negatività: $H(X)\ge 0$
- massimo quando la distribuzione è uniforme
- minimo quando una probabilità vale $1$ e tutte le altre $0$

Caso uniforme con $|\mathcal{X}|=n$  
$H(X)=\log n$

Interpretazione strutturale:
- misura la dispersione della distribuzione di probabilità
- rappresenta l'incertezza media prima dell'osservazione della variabile
- coincide con il limite inferiore della lunghezza media nei sistemi di [[codifica di sorgente|codifica di sorgente]]

Per una distribuzione $p(x)$ su $\mathcal{X}$:  
$0\le H(X)\le \log |\mathcal{X}|$