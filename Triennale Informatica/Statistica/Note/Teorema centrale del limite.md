---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Teorema centrale del limite
---
_sia_
- $X_{1},X_{2}\dots$ una successione di [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite (IDD)|variabili i.d.d.]] 
-  $-\infty \leq a < b \leq +\infty$  due numeri
_se_  $X_{i}$ è dotata di  [[Variabili aleatoria - Momenti|momento secondo]]  
_allora_ denotando $\mathbb{E}[X_{i}]=\mu$ e [[Variabili aleatorie - Varianza|varianza]] $\sigma^{2}(X_{i})=\sigma^{2}>0$ si ha $$\begin{array}{}
\displaystyle\lim_{ n \to \infty } \mathcal{P}\left( a \leq \frac{X_1+\dots+X_{n}-n\mu}{\sigma \sqrt{ n }}  \leq b\right)  & = \\
\displaystyle\cfrac{1}{\sqrt{2\pi}}\int ^b_a e^{-\frac{x^2}{2}}\, dx = \Phi(b)-\Phi(a) 
\end{array}$$equivalentemente  $\cfrac{X_1+\dots+X_{n}-n\mu}{\sigma \sqrt{ n }}$  [[Convergenza in distribuzione|converge in distribuzione]] ad una [[Variabili Aleatorie Notevoli - Gaussiane|variabile gaussiana standard]] 



#### Proposizione
_sia_ 
- $X_{1},X_{2}\dots$ una successione di [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite (IDD)|variabili i.d.d.]] 
 - $-\infty \leq a < b \leq +\infty$  due numeri
_se_ $X_{i}$ è dotata di [[Variabili aleatoria - Momenti|momenti secondo]] 
_allora_ denotando il valore atteso $\mathbb{E}[X_{i}]=\mu$  e [[Idd - varianza campionaria|varianza campionaria]] $S_{n}>0$ 
$$\begin{array}{}
\displaystyle\lim_{ n \to \infty } \mathcal{P}\left( a \leq \sqrt{n}\frac{\overline{X}_{n}-\mu}{ S_{n}}  \leq b\right)  & = \\
\displaystyle\cfrac{1}{\sqrt{2\pi}}\int ^b_a e^{-\frac{x^2}{2}}\, dx = \Phi(b)-\Phi(a) 
\end{array}$$
