---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---
# Teorema della trasformazione integrale della probabilità
---
il teorema di **trasformazione integrale della probabilità** dice che  
**_sia_** $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] continua con [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]] $F$ e **_si definisca_** la trasformazione $$Y=F(X)$$ **_allora_** vale che $Y\sim U(0,1)$ è una [[Variabili Aleatorie Notevoli - Distribuzione uniforme|variabile uniforme]] su $[0,1]$

**Dimostrazione**: consideriamo la [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]] di $Y$ $$P(Y\le y)=P(F(X)\le y)$$ poiché $F$ è crescente (essendo una funzione di distribuzione) possiamo applicare l'inversa $$P(F(X)\le y)=P(X\le F^{-1}(y))$$ usando la definizione di [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]] $$P(X\le a)=F(a)$$ si ottiene $$P(X\le F^{-1}(y))=F(F^{-1}(y))$$ da cui segue $$P(Y\le y)=y \qquad 0\le y\le1$$ questa è esattamente la [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]] della [[Variabili Aleatorie Notevoli - Distribuzione uniforme|variabile uniforme]] su $[0,1]$

#### Interpretazione
la trasformazione integrale della probabilità stabilisce che ogni [[Variabili Aleatorie (Casuali)|variabile aleatoria]] continua può essere trasformata in una [[Variabili Aleatorie Notevoli - Distribuzione uniforme|variabile uniforme]] tramite la propria [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]] e viceversa una variabile uniforme può essere trasformata in una variabile con distribuzione arbitraria applicando l'inversa della [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]]; questo risultato è alla base dei metodi di simulazione di [[Variabili Aleatorie (Casuali)|variabili aleatorie]] ed in particolare del **metodo della trasformata inversa**

