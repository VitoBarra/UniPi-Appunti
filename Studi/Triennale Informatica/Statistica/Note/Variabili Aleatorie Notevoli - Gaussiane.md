---
Subject: "[[Statistica (STAT)]]"
tags:
  - STAT
---
# Variabili aleatorie Gaussiane
---
la [[Funzioni|funzione]] $f(x)=e^{-x^{2}/{2}}$ è una funzione molto regolare siccome è infinitamente [[Derivate|derivabile]] e tende velocemente a $0$. infatti è [[Integrali|integrabile]], ma non si può esprimere la  _primitiva_ di $\int^{t}_{0} e^{-x^{2}/2}   \, dx$  per un qualunque valore di $t$ con _[[Funzioni analitiche|funzioni elementari]]_, fanno eccezioni alcuni _casi particolari_ come $$\int^{+\infty}_{-\infty} e^{-\cfrac{x^{2}}{2}} \, dx  = \sqrt{ 2\pi }$$ e da qui dividendo abbiamo la _[[Definizione di Probabilita|densista di probabilita]] gaussiana_ $$\varphi(x)=\frac{1}{\sqrt{ 2 \pi }}e^{-x^{2}/2}$$ che è una funzione _[[Funzioni|pari]]_ e quindi $\varphi(x)=\varphi(-x)$ 
e la sua [[Variabili aleatorie - Funzione di ripartizione|funzioni di ripartizione]] è $$\Phi(x)=\frac{1}{\sqrt{ 2\pi }}\int^{x}_{-\infty} e^{-\cfrac{t^{2}}{2}} \, dt$$questa _variabile gaussiana standard_ indicata con $N(0,1)$ è cosi importante in [[Statistica (STAT)|statistica]] che gli sono stati riservati dei simboli 
- $\varphi(x)$ la __densita gaussiana__
- $\Phi(x)$ la _funzione di ripartizione_ 
- $q_{\alpha}$ il $a$-[[Quantili e Percentili|quantile]]



##### Proprieta
essendo $\varphi(x)$ una _[[Funzioni#Funzini pari| funzione pari]]_ si ha che dato $x \in \mathbb{R}$ e $0< \alpha <1$ si ha $$\Phi(-x)=1-\Phi(x)$$e che $$q_{1-\alpha}=-q_{\alpha}$$una conseguenza di questo è $$\mathcal{P}\{-t \leq X \leq t\}=\Phi(t)-\Phi(-t)=2\Phi(t)-1$$

>[!tip]
>queste proprieta vale per qualsiasi tipo di _guassiana_ siccome tutte sono [[Funzioni#Funzini pari|funzioni pari]]




#### Proprieta sulla guassiana
ci sono dei casi in cui vorremmo sapere il valore di $$\mathcal{P}\{ a < X <b \}=\int ^{b}_{a} \varphi(x) \, dx=\Phi(b) - \Phi(a)$$ ma questo non è possibile siccome non possiamo esprimere con funzioni semplici $\Phi(x)$ allora ci sono delle approssimazioni numeriche che possiamo usare $$\begin{array}{}
\mathcal{P}\{-1\leq X \leq 1\}  & \approx  & 0,68  \\
\mathcal{P}\{-2\leq X \leq 2\}  & \approx  & 0,94  \\
\mathcal{P}\{-3\leq X \leq 3\}  & \approx &  0,997  
\end{array}$$ e la tabella di valori precalcolati per tutto il resto 
. ![[IMG_0736.png]]
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
$$e la sua densita si puo ottenere [[Derivate|derivando]] $F_{Y}$ o applicando la regola di [[Trasformazioni di variabili con densita#Regola del cambio di variabile|cambio di variabile]] si ottiene la densuita $$f_{Y}(t)=\frac{1}{\sigma}f_{X} \left( \frac{t-m}{\sigma} \right)=\frac{1}{\sigma\sqrt{ 2\pi  }}e^{- \frac{(t-m)^{2}}{2\sigma^{2}}}$$
e questa è chiamata _densita gaussiana_(o normale) $N(m,\sigma^{2})$  e diciamo che $Y$ è gaussiana $N(m,\sigma^{2})$ se la sua densità ha questa forma.

si possono ricondurre tutti i calcoli relativi alla _funzione di ripartizione_ di una  generica variabile guassiana a quelli sulla _funzione di ripartizione_ della _gaussiana standard_ $\Phi$ sostituendo ad $Y$ l espressione $\sigma X + m$

un esempio di questo si vede con 
$$\mathcal{P}\{a <Y <b  \}= \mathcal{P}\left\{  \frac{a-m}{\sigma} < X <\frac{b-m}{\sigma}  \right\}$$
e le approssimazioni numeriche diventano $$\begin{array}{}
\mathcal{P}\{m-\sigma\leq X \leq m+\sigma\}  & \approx  & 0,68  \\
\mathcal{P}\{m-2\sigma\leq X \leq m+2\sigma\}  & \approx  & 0,94  \\
\mathcal{P}\{m-3\sigma\leq X \leq m+3\sigma\}  & \approx &  0,997  
\end{array}$$

![[IMG_0660.jpeg]]



#### Momenti e varianza
per la _variabile_ $Z$ _gaussiana standard_ $N(0,1)$ si ha che siccome le  [[Funzione esponenziale| funzioni esponenziali]] (in questo caso $e^{x^{2}/2}$) crescono più velocemente di qualsiasi altra potenza vale _sempre_ che  $$ \frac{1}{\sqrt{ 2\pi}}\int ^{+\infty}_{\infty} \frac{|x|^{n}}{e^{x^{2}/2}}\, dx < +\infty
$$e quindi la _gaussiana standard_ ha sempre tutti i [[Variabili aleatoria - Momenti|momenti]].
Se $n=2h+1$ ovvero è un numero _dispari_ vale che $$\begin{array}{}
\mathbb{E}[Z^{n}] & = &\displaystyle \frac{1}{\sqrt{ 2\pi }}\int ^{+\infty}_{-\infty}\frac{x^{n}}{e^{x^{2}/2}} \, dx \\
 & = &\displaystyle \lim_{ M \to \infty }\int ^{+M}_{-M} \frac{x^{n}}{e^{x^{2}/2}}\, dx    & =0
\end{array}$$questo siccome $x^{n}$ diventa una [[Funzioni#Funzioni Dispari|funzione dispari]] e quindi vale che le due aree tra $[-M,0]$ e $[0,+M]$ siano uguali ma una delle due è _negativa_, motivo per cui nel [[Integrali|integrale]] questa risulti zero  

se invece $n$ è un _numero pari_ utilizzando l [[Integrazione per parti|integrazione per parti]] si ottiene  $$\begin{array}{}
\mathbb{E}[Z^{2}] & = & \displaystyle \frac{1}{\sqrt{ 2\pi}}\int^{+\infty}_{-\infty} \frac{x^{2}}{e^{x^{2}/2}} \, dx \\
 & = & \displaystyle\left. \frac{-x}{e^{x^2/2}\sqrt{ 2\pi }  }\right|^{+\infty}_{-\infty}+\frac{1}{\sqrt{ 2\pi }}\int ^{+\infty}_{-\infty} \, \frac{1}{e^{x^2/2}}\,dx  \\
 & = & 0+1 \\& = & 1
\end{array}$$dove si usa il fatto che $-xe^{-x^{2}/2}$ è la [[Derivate|derivata]] di $e^{-x^{2}/2}$ 
in _generale_ con conti simili vale che con $n=2h+2$ ovvero pari vale che $$\mathbb{E}[Z^{2h+2}]=(2h+1)\mathbb{E}[Z^{2h}]$$e vale che la [[Variabili aleatorie - Varianza|varianza]] è $$Var(Z)=1$$
##### Gaussiana non standard
Considerando invece una _variabile_ $X$ _gaussiana_ generica $N(m,\sigma^{2})$ si ha che si può riportare $X$ ad una _gaussiana standard_ e usare poi le proprietà dei [[Variabili aleatoria - Momenti|momenti]] ottenendo $$\mathbb{E}[X]=\mathbb{E}[\sigma Z+m]=\sigma\mathbb{E}[Z]+m=m$$e con le proprietà della [[Variabili aleatorie - Varianza|varianza]] si ottiene $$Var(X)=Var(\sigma Z+m)=\sigma^{2}Var(Z)=\sigma^{2}$$