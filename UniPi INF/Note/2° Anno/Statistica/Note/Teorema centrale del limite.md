---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Teorema centrale del limite
---
_sia_ $X_{1},X_{2}\dots$ una successione di [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite|variabili i.d.d.]] dotate di [[Variabili aleatoria - Momenti|momenti secondo]] e valore atteso $\mathbb{E}[X_{i}]=\mu$ e [[Variabili aleatorie - Varianza|varianza]] $\sigma^{2}(X_{i})=\sigma^{2}>0$ presi $-\infty \leq a < b \leq +\infty$ si ha $$\begin{array}{}
\displaystyle\lim_{ n \to \infty } \mathcal{P}\left( a \leq \frac{X_1+\dots+X_{n}-n\mu}{\sigma \sqrt{ n }}  \leq b\right)  & = \\
\displaystyle\cfrac{1}{\sqrt{2\pi}}\int ^b_a e^{-\frac{x^2}{2}}\, dx = \Phi(b)-\Phi(a) 
\end{array}$$equivalentemente  $\cfrac{X_1+\dots+X_{n}-n\mu}{\sigma \sqrt{ n }}$  [[Convergenza in distribuzione|converge in distribuzione]] ad una [[Variabili Aleatorie Notevoli - Gaussiane|variabile gaussiana standard]] 



#### Proposizione
_sia_ $X_{1},X_{2}\dots$ una successione di [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite|variabili i.d.d.]] dotate di [[Variabili aleatoria - Momenti|momenti secondo]] e valore atteso $\mathbb{E}[X_{i}]=\mu$  e [[Variabili aleatorie - Varianza|varianza]] $\sigma^{2}(X_{i})=\sigma^{2}>0$ presi $-\infty \leq a < b \leq +\infty$ si ha $$\begin{array}{}
\displaystyle\lim_{ n \to \infty } \mathcal{P}\left( a \leq \sqrt{n}\frac{\overline{X}_{n}-\mu}{ S_{n}}  \leq b\right)  & = \\
\displaystyle\cfrac{1}{\sqrt{2\pi}}\int ^b_a e^{-\frac{x^2}{2}}\, dx = \Phi(b)-\Phi(a) 
\end{array}$$
