---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area: 
topic: "[[Variabili Aleatorie (Casuali)]]"
SubTopic:
---

# Legge di Probabilita
---
la __legge di probabilita__ è definita come
_sia_  
- $(\Omega,\mathcal{F},\mathcal{P})$ uno _[[Definizione di Probabilita|spazio di probabiltia]]_
- $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] 
_allora_ la funzione di insiemi $\mathcal{P}_{X}(A)=\mathcal{P}(X \in  A)= \mathcal{P}(X^{-1}(A))$ è una [[Probabilita sui numeri Reali|Probabilità]] su $\mathbb{R}$  ed è detta __legge di pobabilità__ di $X$ 

_dimostrazione_ per mostrare che è una _probabilità_ bisogna dimostrare la $\sigma$-additivita: se $(A_{n})_{n \geq 1}$ è una successione di sotto insiemi di $\mathbb{R}$ a due a due disgiunti, anche le immagini inverse sono disgiunte e si ha$$\mathcal{P}_{X}\left(\bigcup_{n=1}^{+\infty}A_{n}\right)=\mathcal{P}\left(X^{-1}\left(\bigcup_{n=1}^{+\infty}A_{n}\right)\right) = \sum^{+ \infty}_{n=1}\mathcal{P}_{X}(X^{-1}(A_{n}))=\sum^{+ \infty}_{n=1}\mathcal{P}_{X}(A_{n})$$
se due variabili aleatorie hanno la stessa _legge di probabilità_ sono dette _equidistribuite_ o isonome.


Nelle applicazioni pratiche spesso non vengono definite lo _spazio di probabilita_ $\Omega$ e la variabile $X:\Omega \rightarrow \mathbb{R}$ ma solo la _legge di probabilita_ $\mathcal{P}_{X}$ questo avviene siccome si puo dimostrare che assegnata una probabilita $\mathcal{Q}$ a sotto insiemi di $\mathbb{R}$  è possibile costruire un sotto insieme $\Omega$ una probabilità $\mathcal{P}$ sui sotto insiemi di $\Omega$  ed una _variabile aleatoria_ $X:\Omega \rightarrow \mathbb{R}$ tale che $\mathcal{P}_{X}=\mathcal{Q}$.  infatti abbiamo che la sola _legge di probabilita_ descrive tutta l informazione in gioco se le variabili aleatore che stiamo considerando è una sola, altrimenti bisogna definirle piu accuratamente.



