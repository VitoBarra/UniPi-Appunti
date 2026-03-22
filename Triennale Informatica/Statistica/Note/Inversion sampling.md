---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Inversion sampling
---
Il **metodo dell'inversione** (inversion sampling) consente di generare una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] con una distribuzione assegnata a partire da una [[Variabili Aleatorie Notevoli - Distribuzione uniforme|variabile uniforme]]. è di fatto il risultato inverso del [[Teorema della trasformazione integrale della probabilita|Teorema della trasformazione integrale della probabilita]]

Sia $Y$ una [[Variabili Aleatorie Notevoli - Distribuzione uniforme|variabile uniforme]] su $[0,1]$ e sia $F$ una [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]] continua e invertibile associata ad una distribuzione di probabilità. Definendo $$X = F^{-1}(Y)$$ la [[Variabili Aleatorie (Casuali)|variabile aleatoria]] $X$ ha [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]] $F$.


In particolare$$F(X)=P(X \le x) = P(F^{-1}(Y) \le x)$$e poiché $F$ è monotona crescente si puo applicare da entrambi i lati preservando la relazione $$P(F^{-1}(Y) \le x) = P(Y \le F(x)).$$Essendo $Y \sim \text{Unif}(0,1)$,$$P(Y \le F(x)) = F(x),$$da cui segue che la funzione di ripartizione di $X$ è proprio $F$.

Questo risultato è alla base dell'**inversion sampling method**, una tecnica usata simulazione di [[Variabili Aleatorie (Casuali)|variabili aleatorie]]: per generare campioni da una distribuzione con CDF $F$, si genera prima $Y \sim \text{Unif}(0,1)$ e poi si pone $$X = F^{-1}(Y).$$
