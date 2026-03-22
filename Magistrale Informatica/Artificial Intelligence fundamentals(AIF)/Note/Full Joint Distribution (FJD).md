---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Full Joint Distribution (FJD)
---
La **full joint distribution** e la distribuzione congiunta di un insieme di [[Variabili Aleatorie (Casuali)|variabili aleatorie]] $X_1,\dots,X_n$ e descrive la probabilita associata a tutte le possibili configurazioni simultanee delle variabili. Nel caso discreto essa e una [[Distribuzione di probabilita|distribuzione di probabilita]] $P(X_1,\dots,X_n)$ e soddisfa $$\sum_{x_1,\dots,x_n}P(x_1,\dots,x_n)=1$$ mentre nel caso continuo l'oggetto analogo e la densita congiunta $p(x_1,\dots,x_n)$ e vale $$\int p(x_1,\dots,x_n)\,dx_1\cdots dx_n=1$$
La **full joint distribution** contiene l'informazione completa sul sistema probabilistico: da essa si possono ricavare distribuzioni marginali tramite [[FJD - Marginalizzazione|marginalizzazione]] e, applicando la [[Formula del condizionamento ripetuto (Chain rule)|chain rule]], la si puo decomporre in prodotto di probabilita condizionate senza assumere [[Indipendenza Stocastica|indipendenza]]:
$$P(X_1,\dots,X_n)=P(X_1)P(X_2\mid X_1)P(X_3\mid X_1,X_2)\cdots P(X_n\mid X_1,\dots,X_{n-1})$$
In forma compatta $$P(X_1,\dots,X_n)=\prod_{i=1}^n P(X_i\mid X_1,\dots,X_{i-1})$$ dove per $i=1$ si intende semplicemente $P(X_1)$.
