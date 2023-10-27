---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili Aleatorie Notevoli - Poisson
---

#### Variabile di Poisson
_sia_ $X:\Omega \rightarrow\mathbb{N}$ una  _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ nei naturali e $\lambda>0$ un numero 
_allora_ è $X$ una _variabile di Poisson_ 
_se_ vale $$\mathcal{P}(X=h)=e^{-\lambda}\frac{\lambda^{h}}{h!}$$
questa è una [[Definizione di Probabilita|probabilità]] valida dobbiamo vedere che la probabilita totale è 1 ma e deve quindi valere $$\sum^{+\infty}_{h=0}\mathcal{P}(X=h)=1$$ ma questa è una conseguenza dello sviluppo esponenziale $$e^{\lambda}=\sum^{+\infty}_{h=0}\frac{\lambda^{h}}{h!}$$
questa _variabile aleatoria_ a prossima bene la variabile _[[Variabili Aleatorie Notevoli - Binomiale|binomiale]]_ $B(n,p)$ quando $n$ è grande e $p$ e piccolo e quando vale $np \approx \lambda$. Overo quando il numero delle prove è alto e la probabilita di successo molto bassa, infatti la _variabile di poisson_ è anche detta _degli aventi rari_
