---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Potenza o Zipf
---
La _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ **a legge di potenza** e' una variabile discreta definita sui naturali positivi la cui [[Legge di Probabilita|legge di probabilità]] decresce come una potenza del valore assunto. _Sia_ $X:\Omega\to\mathbb{N}_{\geq 1}$ una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ e $\gamma>1$ un parametro reale. _Allora_ $X$ ha **legge di potenza** _se_ vale $$\mathcal{P}(X=h)=\frac{1}{\zeta(\gamma)}\frac{1}{h^{\gamma}},\qquad h=1,2,3,\dots$$ dove $\zeta(\gamma)$ è la [[Funzione Zeta di Riemann|Funzione Zeta di Riemann]] definita come $$\zeta(\gamma)=\sum_{h=1}^{+\infty}\frac{1}{h^{\gamma}}$$ e' la serie che normalizza la probabilità. La condizione $\gamma>1$ e' necessaria perché la [[Serie|serie]] $\sum_{h=1}^{+\infty}h^{-\gamma}$ converga, quindi perché la probabilità totale valga $1$. 

Senza questo fattore di normalizzazione, una scrittura del tipo $$\mathcal{P}(X=h)\propto h^{-\gamma}$$ indica solo la forma asintotica della distribuzione.

Questa distribuzione assegna probabilità relativamente elevate anche a valori molto grandi rispetto a distribuzioni con decadimento esponenziale, per questo viene detta distribuzione a **coda pesante**.

La [[Variabili aleatorie - Funzione di ripartizione (CDF)|funzione di ripartizione]] è $$F(x)=\mathcal{P}(X\leq x)=\sum_{h=1}^{\lfloor x\rfloor}\frac{1}{\zeta(\gamma)}\frac{1}{h^{\gamma}},\qquad x\geq 1$$ mentre per $x<1$ vale $$F(x)=0$$

#### Momenti e varianza
La legge di potenza non ammette sempre tutti i [[Variabili aleatoria - Valore atteso|momenti]]. In generale il momento di ordine $r$ esiste se e solo se $$\sum_{h=1}^{+\infty}h^{r}\mathcal{P}(X=h)=\frac{1}{\zeta(\gamma)}\sum_{h=1}^{+\infty}\frac{1}{h^{\gamma-r}}<+\infty$$ e questo accade se e solo se $$\gamma-r>1\iff \gamma>r+1$$

In particolare:
- il [[Variabili aleatoria - Valore atteso|momento primo]] esiste solo se $\gamma>2$;
- il [[Variabili aleatorie - Varianza|momento secondo]] esiste solo se $\gamma>3$;
- la [[Variabili aleatorie - Varianza|varianza]] esiste solo se $\gamma>3$.

Quando $\gamma>2$ si ha $$\mathbb{E}[X]=\frac{\zeta(\gamma-1)}{\zeta(\gamma)}$$

Quando $\gamma>3$ si ha $$\mathbb{E}[X^2]=\frac{\zeta(\gamma-2)}{\zeta(\gamma)}$$ e quindi $$Var(X)=\frac{\zeta(\gamma-2)}{\zeta(\gamma)}-\left(\frac{\zeta(\gamma-1)}{\zeta(\gamma)}\right)^2$$

La legge di potenza e' particolarmente importante quando si studiano grandezze discrete con distribuzione molto sbilanciata, in cui pochi valori grandi coesistono con moltissimi valori piccoli. In questi casi una quantita' del tipo $$P(k)\sim k^{-\gamma}$$ descrive il comportamento asintotico della distribuzione e non sempre una legge di probabilita' esatta.
