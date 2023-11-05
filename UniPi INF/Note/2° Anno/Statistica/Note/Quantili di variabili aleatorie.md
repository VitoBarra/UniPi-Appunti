---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Quantili di variabili aleatorie
---

#### Quantile (Definizione)
_sia_ $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria]] e $\beta\in(0,1)$ un _numero_ si chiama $\beta$_-quantile_ un numero $r$ tale che $$\mathcal{P}(X\leq r)\geq \beta \ \ \ \ \ \ \ e \ \ \ \ \ \  \mathcal{P}(X \geq r) \geq 1 - \beta$$questo quantile non è sempre _unico_
Se la [[Funzione di ripartizione di variabili aleatorie|funzione di ripartizione]]  $F_{X}$ di $X$ è _strettamente_ crescente il _quantile_ $r_{\beta}$ è unico $\forall \beta \in (0,1)$ e $r_{\beta} = F_{X}^{-1}(\beta)$. Questo non puo accadere nelle [[Variabili Aleatorie (Casuali)|variabili aleatorie]] _discrete_ 



#### Scegliere il $\beta$-quantile in variabili aleatorie discrete 
_sia_ $X$ una [[Variabili Aleatorie (Casuali)|variabile aleatoria discreta]] e $x_{1},x_{2},\dots$  i valori che assume e _supponiamo_ di poterli ordinare $x_{1} < x_{2}< \dots$  (potrebbe non essere vero in caso la successione tenda ad $-\infty$ e quindi non esiste un $x_{i}$ piu piccolo)
_Se_  $\exists x_{j}. F_{X}(x_{j})=\beta \implies$ ogni numero $r$ con $x_{j} \leq r \leq x_{j+1}$ soddisfa la _definizione_ di quantile e si sceglie per convenzione $r_{\beta}=\cfrac{x_{j}+x_{j+1}}{2}$
_altrimenti_ $r_{\beta}$ è il più piccolo $x_{j}.F_{X}(x_{j}\geq \beta)$



#### Calcolare il $\beta$-quantili con la funzione di ripartizione
dalla definizione di quantile si ha che $$\mathcal{P}(X\leq r)\geq \beta \ \ \ \ \ \ \ e \ \ \ \ \ \  \mathcal{P}(X \geq r) \geq 1 - \beta$$ e quindi puo essere calcolato utilizzando la [[Funzione di ripartizione di variabili aleatorie|funzione di ripartizione]]  $$F(r)\geq \beta  \ \ \ \ \ \ \ e \ \ \ \ \ \ 1-F(r) \geq 1-\beta $$e quindi $$\begin{cases}
F_{X}(r) \geq \beta \\
F_{X}(r) \leq \beta
\end{cases} \implies F_{X}(r)=\beta$$

