---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Multinomiale
---
La [[Variabili Aleatorie Notevoli - Multinomiale|variabile multinomiale]] generalizza la [[Variabili Aleatorie Notevoli - Binomiale|variabile binomiale]] al caso in cui ogni prova possa produrre $K$ classi possibili invece di due soli esiti. Si considerano $n$ prove [[Indipendenza Stocastica|indipendenti]] con le stesse probabilità di classe $p_1,\dots,p_K$, dove $p_i\in(0,1)$ e $\sum_{i=1}^K p_i=1$.

#### Variabile multinomiale
_sia_ $X=(X_1,\dots,X_K)$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] vettoriale in cui $X_i$ conta quante volte compare la classe $i$ nelle $n$ prove
_se_ vale che $$\mathcal{P}(X_1=x_1,\dots,X_K=x_K)=\frac{n!}{x_1!\cdots x_K!}p_1^{x_1}\cdots p_K^{x_K}$$ con $x_i\geq 0$ interi e $$\sum_{i=1}^K x_i=n$$
_allora_ $X$ e detta __variabile multinomiale__ di parametri $n$ e $(p_1,\dots,p_K)$ e si indica con $$X\sim Mult(n;p_1,\dots,p_K)$$

dove
- $p_1^{x_1}\cdots p_K^{x_K}$ e la probabilita di una sequenza con $x_i$ occorrenze della classe $i$
- $\frac{n!}{x_1!\cdots x_K!}$ e il numero di modi di [[Combinatoria#Disposizioni|disporre]] le $n$ osservazioni mantenendo fissati i conteggi

la [[Definizione di Probabilita|probabilita]] totale e $1$ come conseguenza dello sviluppo multinomiale di $$(p_1+\dots+p_K)^n$$

> [!tip]
> per $K=2$ la multinomiale coincide con la [[Variabili Aleatorie Notevoli - Binomiale|variabile binomiale]]

#### Proprieta elementari
le componenti $X_1,\dots,X_K$ soddisfano $$X_1+\dots+X_K=n$$ quindi non sono indipendenti. Ciascuna componente presa singolarmente ha pero legge binomiale: $$X_i\sim B(n,p_i)$$

i [[Variabili aleatoria - Momenti o Valore atteso|momenti]] primi sono $$\mathbb{E}[X_i]=np_i$$
le [[Variabili aleatorie - Varianza|varianze]] sono $$Var(X_i)=np_i(1-p_i)$$
le covarianze tra componenti distinte sono $$Cov(X_i,X_j)=-np_ip_j \ \ \ \ , i\neq j$$

la matrice di covarianza ha quindi diagonale $$np_i(1-p_i)$$ e termini fuori diagonale $$-np_ip_j$$

#### Interpretazione
la multinomiale descrive un vettore di conteggi associato a una partizione discreta di $n$ prove. Ogni realizzazione non fornisce un singolo numero di successi, ma un intero profilo di frequenze $(x_1,\dots,x_K)$ vincolato dalla relazione $\sum_i x_i=n$.

#### Relazione con Bernulli categoriale
ogni prova puo essere rappresentata da un vettore one-hot $Z=(Z_1,\dots,Z_K)$ tale che uno solo tra i termini vale $1$ e gli altri valgono $0$, con $$\mathcal{P}(Z_i=1)=p_i$$ Allora la variabile multinomiale si ottiene come somma di $n$ vettori indipendenti dello stesso tipo: $$X=\sum_{r=1}^n Z^{(r)}$$

#### Relazione con Dirichlet
la [[Variabili aleatorie Notevoli - Dirichlet|Dirichlet]] e il prior coniugato naturale della multinomiale. Se il vettore dei parametri $(p_1,\dots,p_K)$ e incognito e viene modellato con una Dirichlet, l'aggiornamento bayesiano mantiene la stessa famiglia dopo l'osservazione dei conteggi multinomiali.
