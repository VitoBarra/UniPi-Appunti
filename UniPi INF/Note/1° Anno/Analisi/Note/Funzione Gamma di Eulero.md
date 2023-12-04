---
type: nota
course: Analisi
topic: 
tags:
  - Analisi
Parent MOC: "[[Analisi]]"
---
# Funzione Gamma di Eulero
---
è una [[Funzioni|funzione]] che stende la nozione di [[ƒattoriale|fattoriale]] ai numeri $\mathbb{R}$  
#### Funzione $\Gamma$ di eulero
la _funzione_ è definita come $$\Gamma(r)=\int^{+\infty}_0 x^{r-1}e^{-x}  \, dx \ \ \ \ \ \ \ \ \ \ r>0$$ per un generico $r$ l integrale esiste ma non ha _rappresentazione_ in funzioni elementari. 
_vale_ per $r>1$ la relazione $$ \Gamma(r)=(r-1)(\Gamma(r-1))$$ e questo viene dalla definizione [[Integrali|integrando]] per parti $$\begin{array}{}
\displaystyle\int ^{+\infty}_{0} x^{r-1}e^{-x}\, dx  & = \\
\left . x^{r-1}e^{-x} \right|^{+\infty}_{0}+ (r-1)\displaystyle\int ^{+\infty}_{0} x^{r-2}e^{-x}\, dx  &   
\end{array}$$
e poiché $\Gamma(1)=1$, ne segue che per $n$ intero positivo si ha $\Gamma(n)=(n-1)!$ e dunque la _funzione Gamma_ puo essere vista come a numeri non interi del fattoriale 
