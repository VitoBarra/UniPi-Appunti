---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Kullback-Leibler (KL) Divergence
---
La **Kullback–Leibler divergence** è una [[Definizione di divergenza|divergenza]] misura quanto una [[Distribuzione di probabilita|distribuzione di probabilità]] $q$ differisce da una **[[Distribuzione di probabilita|distribuzione di riferimento]]** $p$. È una quantità della [[Teoria del informazione (TDI)|Teoria dell'informazione]] e della [[Inferenza statistica]] e quantifica la perdita di informazione quando $q$ viene usata per approssimare $p$

In forma generale si scrive come [[Variabili aleatoria - Valore atteso|valore atteso]] rispetto alla distribuzione $q$ del logaritmo del rapporto tra $q$ e $p$, ovvero $$KL(q \parallel p)=\mathbb{E}_q\left[\log\frac{q(z)}{p(z)}\right]$$la variabile $z$ è solo la variabile su cui sono definite le due distribuzioni. 

Dal punto di vista intuitivo, la formula confronta $q$ e $p$ punto per punto tramite il rapporto $\frac{q(z)}{p(z)}$ e poi fa una media pesata con $q$. Quindi pesano di più proprio i valori di $z$ che per $q$ sono più probabili. Se in una zona $q(z)$ è molto più grande di $p(z)$, allora il termine $\log \frac{q(z)}{p(z)}$ è positivo e contribuisce ad aumentare la divergenza; se invece $q$ e $p$ coincidono, il rapporto vale $1$, il logaritmo vale $0$ e la divergenza si annulla.

La **Kullback–Leibler divergence** è
- **non negativa** $D_{KL}(q \parallel p) \ge 0$  vale zero se e solo se $q(x)=p(x)$ quasi ovunque. Questa proprietà deriva dalla **[[Disuguaglianza di Gibbs|disuguaglianza di Gibbs]]**.
- **non è simmetrica** $D_{KL}(q \parallel p) \neq D_{KL}(p \parallel q)$ e non soddisfa la [[Diseguaglianza triangolare|disuguaglianza triangolare]] e per questo motivo viene interpretata come una **misura direzionale di divergenza informativa**. 
![[IMG - kullback-Leibler (KL) Divergence.png]]

La **Kullback–Leibler divergence**  può essere espressa tramite [[Entropia]] e [[Cross-entropy|Cross-entropy]] nella forma
$$
D_{KL}(q \parallel p)
= H(q,p) - H(q) $$
dove
- $H(q,p) = -\mathbb{E}_q[\log p(x)]$ è la **cross-entropy**
- $H(q) = -\mathbb{E}_q[\log q(x)]$ è l'**entropia di Shannon**

Questa formulazione si ottiene partendo dalla definizione generale
$$
D_{KL}(q \parallel p)=\mathbb{E}_q\left[\log\frac{q(x)}{p(x)}\right]
$$
e usando la proprietà del [[Funzione logaritmica|logaritmo]]
$$
\log\frac{q(x)}{p(x)}=\log q(x)-\log p(x)
$$
Quindi sostituendo nella definizione e sfruttando il fatto che il [[Variabili aleatoria - Valore atteso|Valore atteso]] è un [[Applicazioni Lineari|operatore lineare]]
$$
D_{KL}(q \parallel p)
= \mathbb{E}_q[\log q(x)]-\mathbb{E}_q[\log p(x)]
= -H(q)+H(q,p)
= H(q,p)-H(q).
$$

### Definizione nel contesto variazionale
Nel contesto della [[Inferenza variazionale]] la forma generale della KL si applica prendendo come distribuzione di riferimento il posterior vero $p(z\mid x)$, cioè la distribuzione della variabile latente $z$ condizionata al dato osservato $x$, mentre $q(z)$ è la distribuzione approssimante scelta per avvicinarlo. Si ottiene quindi
$$
KL(q \parallel p) = \mathbb{E}_q \left[ \log \frac{q(z)}{p(z \mid x)} \right]
= \mathbb{E}_q[\log q(z)] - \mathbb{E}_q[\log p(z \mid x)]
$$
Questa non è una definizione diversa della KL, ma la sua specializzazione al problema variazionale.

L'intuizione è che la media è fatta rispetto a $q$, quindi contano soprattutto i valori di $z$ che $q$ considera probabili:
- se $q(z)$ è alta e anche $p(z\mid x)$ è alta, il contributo è piccolo e la situazione è favorevole
- se $q(z)$ è alta ma $p(z\mid x)$ è bassa, il contributo è grande e la situazione è sfavorevole
- se $q(z)$ è bassa, quel valore di $z$ pesa poco nel valore atteso, quindi conta poco

Per questo minimizzare $KL(q\parallel p)$ significa spingere $q$ a concentrare massa proprio nelle zone in cui anche il posterior vero $p(z\mid x)$ è grande.