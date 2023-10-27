---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili aleatorie Gaussiane
---
 
#### Variabile Gausiana
la funzione $f(x)=e^{-x^{2}/{2}}$ è una funzione molto regolare siccome è infinitamente [[Derivate|derivabile]] e tende velocemente a 0. infatti è [[Integrali|integrabile]], ma non si puo rappresentare la  _primitiva_ di $\int^{t}_{0} e^{-x^{2}/2}   \, dx$  per un qualunque valore di $t$ con _funzioni elementari_ tranne per alcuni _casi particolari_ come $$\int^{+\infty}_{-\infty} e^{-\cfrac{x^{2}}{2}} \, dx  = \sqrt{ 2\pi }$$ e da qui dividendo abbiamo la _[[Definizione di Probabilita|densista di probabilita]]_ $$\varphi(x)=\frac{e^{-\cfrac{x^{2}}{2}}}{\sqrt{ 2 \pi }}$$ e la sua [[Funzioni di ripartizione di variabili aleatorie|funzioni di ripartizione]] è $$\Phi(x)=\frac{1}{\sqrt{ 2\pi }}\int^{+\infty}_{-\infty} e^{-\cfrac{t^{2}}{2}} \, dx$$
questa _variabile gaussiana standard_ indicata con $N(0,1)$ è cosi importante in [[Statistica (STAT)|statistica]] che gli sono stati riservati dei simboli 
- $\varphi(x)$ la _densita gaussiana_
- $\Phi(x)$ la _funzione di ripartizione_ 
- $q_{\alpha}$ il $a$-[[Quantili e Percentili|quantile]]



#### Proprieta sulla guassiana
ci sono dei casi in cui vorremmo sapere il valore di $$\mathcal{P}\{ a < X <b \}=\int ^{b}_{a} \varphi(x) \, dx=\Phi(a) - \Phi(b)$$ ma questo non è possibile siccome non possiamo esprimere con funzioni semplici $\Phi(x)$ allora ci sono delle approssimazioni numeriche che possiamo usare $$\begin{array}{}
\mathcal{P}\{-1\leq X \leq 1\}  & \approx  & 0,68  \\
\mathcal{P}\{-2\leq X \leq 2\}  & \approx  & 0,94  \\
\mathcal{P}\{-3\leq X \leq 3\}  & \approx &  0,997  
\end{array}$$
#### Teoria
_sia_  
- $X$ una  _variabile aleatoria gaussiana standard_ 
- $\sigma$  un numero positivo
- $m \in \mathbb{R}$ un numero 
- $Y=\sigma X+m$
la _[[Funzione di Ripartizione|funzoine di ripartizione]]_ di $Y$ $F_{Y}$ è data da $$\begin{array}{}
F_{Y}(t) & = & \mathcal{P}\{ Y \leq t \} & = &  \mathcal{P}\{ \sigma X + m \leq t \} & = \\  &  & 
\mathcal{P}\left\{ X \leq \frac{t-m}{\sigma}   \right\} & = & \Phi\left( \frac{t-m}{\sigma} \right)
\end{array}
$$e la sua densita si puo ottenere [[Derivate|derivando]] $F_{Y}$ o applicando la regola di [[Trasformazioni di variabili con densita#Regola del cambio di variabile|cambio di variabile]] si ottiene $$f_{Y}(t)=\frac{1}{\sigma}fx \left( \frac{t-m}{\sigma} \right)=\frac{1}{\sqrt{ 2\pi \sigma }}e^{- \frac{(t-m)}{2\sigma^{2}}}$$
e questa è chiamata _densita gaussiana_(o normale) $N(m,\sigma^{2})$  e diciamo che $Y$ è gaussiana $N(m,\sigma^{2})$ se la sua densita ha questa forma.

si possono ricondurre tutti i calcoli relativi alla _funzione di ripartizione_ di una  generica variabile guassiana a quelli sulla _funzione di ripartizione_ della _gaussiana standard_ $\Phi$ sostituendo ad $Y$ l espressione $\sigma X + m$

un esempio di questo si vede con 
$$\mathcal{P}\{a <Y <b  \}= \mathcal{P}\left\{  \frac{a-m}{\sigma} < X \frac{b-m}{\sigma}  \right\}$$
e le approssimazioni numeriche diventano $$\begin{array}{}
\mathcal{P}\{m-\sigma\leq X \leq m+\sigma\}  & \approx  & 0,68  \\
\mathcal{P}\{m-2\sigma\leq X \leq m+2\sigma\}  & \approx  & 0,94  \\
\mathcal{P}\{m-3\sigma\leq X \leq m+3\sigma\}  & \approx &  0,997  
\end{array}$$

![[IMG_0660.jpeg]]

