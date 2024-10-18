---
Course: Calcolo Numerico
topic: nota
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Metodo delle tangenti o di Newton
---
è un [[Metodi iterativi funzionali (calcolo degli zeri)|metodo]] per cercare gli _zero_ di una funzione $f\in C^1$ é un metodo nella forma
$$\begin{cases}
x_{0}  \in \mathbb{R}  \\
x_{k+1}=x_{k}-\cfrac{f(x_{k})}{f'(x_{k})}
\end{cases}$$
è si basa sul idea di far passare una _[[Retta tangente|Retta tangente]]_ al punto $(x_k,f(x_k))$ e di prendere come prossima $x_{i+1}$ il punto di intersezione della tangente al asse delle $x$.
per trovare il _prossimo punto del interazione_ si calcola risolvendo il seguente sistema$$
\begin{cases}
y-f(x_{0})=f'(x_{0})(x-x_{0}) \\
y = 0
\end{cases}$$dove 
- la prima espressione è la _retta tangente_
- la seconda espressione é l intersezione con l asse $x$
questo metodo funziona finche non arriviamo ad un [[Massimi e minimi|minimo o ad un massimo]] in quei punti la [[Derivate|Derivate]] è pari a $0$ e il metodo non è definito. _geometricamente_ la tangente è parallela e non tocca l asse delle $x$.


> [!tip]
> questo metodo può essere visto sotto forma del _[[Metodo dei punti fissi|metodo del punto fisso]]_ prendendo in particolare $g(x) =x_{k}-\cfrac{f(x_{k})}{f'(x_{k})}$

#### Radici semplici 
preso $\alpha:f(\alpha)=0$ è detta _radice semplice_ per $f\in C^{1}([a,b])$  se $\alpha \in (a,b)$ e $f'(\alpha)\not=0$
#### Teorema
_sia_ $f:[a,b]\rightarrow\mathbb{R}, \ \ f\in C^{2}([a,b]), \ \ f(\alpha)=0$ e $\alpha \in (a,b)$ 
_se_ $\alpha$ è _radice semplice_ cioè se $f'(\alpha) \not =0$
_allora_ il metodo $x_{k+1}=x_{k}-\cfrac{f(x_{k})}{f'(x_{k})}$ è _[[Convergenza locale per metodi interativi funzionali|localmente convergente]]_ ad $\alpha$ e
_se_ la successione ${x_k}$ con $x_k \not=\alpha$ 
_allora_ l [[Ordine di convergenza|ordine di convergenza]] è almeno _quadratico_ ovvero
	$$\lim_{ k \to \infty } \cfrac{|x_{k+1}-\alpha|}{|x_{k}-\alpha|^{2}}  = \ell \in \mathbb{R}$$
- se $\ell \not = 0$ é quadratica altrimenti se $\ell = 0$ è più che quadratica siccome il numeratore va a $0$ _più velocemente_ del denominatore 


##### Dimostrazione di convergenza locale
poiché $f'(\alpha) \not = 0$ allora $f'(\alpha)$ avrà un segno e dal [[Teorema della permanenza del segno|Teorema della permanenza del segno]] possiamo dire $\exists \eta>0: \forall x \in [\alpha-\eta,\alpha+\eta] \ \ \ \ \ f'(x)\not =0$ 
mi definisco una funzione 
$$ \begin{cases}
g: [\alpha-\eta,\alpha+\eta] \rightarrow \mathbb{R}  \\
g(x)=x-\cfrac{f(x)}{f'(x)}
\end{cases}$$
$g$ è ben definita siccome $f'(x)$ non si annulla mai nel intervallo $[\alpha-\eta,\alpha+\eta]$. in più $g \in C^{1}$ siccome _per ipotesi_ $f \in C^{2}$ posso derivare almeno una volta $g$
$$
\begin{array}{}
g'(x) & = &  1- \cfrac{f'(x)f'(x) -f''(x)f(x)}{[f'(x)]^{2}} \\
& =& 1 - \cfrac{[f'(x)]^{2}}{[f'(x)]^{2}} +\cfrac{f''(x)f(x)}{[f'(x)]^{2}}  \\
& = & \cfrac{f''(x)f(x)}{[f'(x)]^{2}}
\end{array}
$$
 e a questo punto ho quasi finito siccome mi basta dimostrare che $|g'(\alpha)|<1$ e usare il _[[#Corollario|corollario del punto fisso]]_. siccome $f'(\alpha) \not = 0$  allora $g'(x)$ é ben definita e siccome $f(\alpha) = 0 \implies g'(\alpha) =0$ quindi ho che $|g'(\alpha)|<1$ e di conseguenza il metodo _converge localmente_

##### Dimostrazione di convergenza quadratica
dobbiamo dimostrare che $$\lim_{ k \to \infty } \cfrac{|x_{k+1}-\alpha|}{|x_{k}-\alpha|^{2}}  = \ell \in \mathbb{R}$$
tenda ad un numero. quindi bisogna risolvere il [[Limiti di una funzione|limite]] si fa lo [[Sviluppi di Taylor|sviluppo di Taylor]] applicato ad $f(x)$ nel punto $x_k$
$$f(x) = f(x_{k})+f'(x_{k})(x-x_{k})+f''(\xi_{x}) \frac{(x-x_{k})^{2}}{2!}$$
e so che $$|\xi_{x}-x| \leq |x_{k}-x|$$
questa formula vale per qualsiasi punto nello specifico vale per $x=\alpha$ e quindi ho
$$0=f(\alpha) = f(x_{k})+f'(x_{k})(\alpha-x_{k})+f''(\hat{\xi_{x}}) \frac{(\alpha-x_{k})^{2}}{2!}$$
siccome il mio _obbiettivo_ è riscrivere il numeratore $|x_{k+1}-\alpha|$ come qualcosa di diverso e sapendo che $|x_{k+1}-\alpha| = x_{k}-\alpha-\cfrac{f(x)}{f'(x)}$ cerco di ricavarmi questa espressione dalla _espansione di Taylor_
$$\begin{array}{}
0 &  = &  f(x_{k})+f'(x_{k})(\alpha-x_{k})+f''(\hat{\xi_{x}}) \cfrac{(\alpha-x_{k})^{2}}{2!} \\ 
-f(x_{k})-f'(x_{k})(\alpha-x_{k})  & =  & f''(\hat{\xi_{x}}) \cfrac{(\alpha-x_{k})^{2}}{2!} \\
-\cfrac{f(x_{k})}{f'(x_{k})}-\cfrac{f'(x_{k})}{f'(x_{k})}(\alpha-x_{k})  & =  & \cfrac{f''(\hat{\xi_{x}})}{f'(x_{k})} \cfrac{(\alpha-x_{k})^{2}}{2!} \\
x_{k}-\alpha -\cfrac{f(x_{k})}{f'(x_{k})}  & =  & \cfrac{f''(\hat{\xi_{x}})}{f'(x_{k})} \cfrac{(\alpha-x_{k})^{2}}{2!} \\
x_{k+1}-\alpha  & = & \cfrac{f''(\hat{\xi_{x}})}{f'(x_{k})} \cfrac{(\alpha-x_{k})^{2}}{2!} \\
x_{k+1}-\alpha  & = & \cfrac{f''(\hat{\xi_{x}})}{2f'(x_{k})} (x_{k}-\alpha)^{2}
\end{array}$$
nel ultimo passaggio ho invertito $(x_{k}-\alpha)$ siccome essendo al quadrato il risultato _non cambiata_ e torna comodo dopo
e allora il limite diventa. 
$$\begin{array}{}
\lim_{ k \to \infty } \cfrac{|x_{k+1}-\alpha|}{|x_{k}-\alpha|^{2}}   & =  \\
\lim_{ k \to \infty } \cfrac{\cfrac{|f''(\hat{\xi_{x})}|}{|2f'(x_{k})|} |\alpha-x_{k}|^{2}}{|x_{k}-\alpha|^{2}}  & =  \\
\lim_{ k \to \infty } \cfrac{|f''(\hat{\xi_{x})}|}{|2f'(x_{k})|} 
\end{array}$$
e ora si può risolvere il limite. sappiamo che con $k\to \infty$
- $x_k \to \alpha$
- $f'$ é continua
- $f''$ è continua
- $0 \leq |\hat{\xi_{x}}-\alpha| \leq |x_{k}-\alpha|$
	- $\hat{\xi_{x}} \to \alpha$
quindi per ipotesi di _radice semplice_ $|2f'(x_{k})| \not = 0$ e quindi il limite è finito $= \ell$. e se $f''(\alpha) =0$ _allora_ la convergenza è _più che quadratica_



#### Teorema di convergenza in largo (o in grande)
_sia_ $f:[a,b]\rightarrow \mathbb{R}, \ \ f \in C^{2}([a,b]),\ \ f(\alpha) =0, \ \ \alpha\in(a,b)$ 
_se_ 
1. $\exists \delta>0: \forall x \in S,\ S=(\alpha,\alpha+\delta] \subset (a,b)$
2. $f'(x)\not = 0 \ \ \ \forall x \in S$
3. $f(x) f''(x)>0$ (hanno cioè segno concorde)
_si ha che_ il __metodo delle tangenti__ con $x_{0}\in S$ genera _successioni monotone decrescenti_ e convergenti ad $\alpha$

##### Dimostrazione
si osserva che $f'(x)$ ha segno costante in $S$  prendendo il caso $f'(x)>0$ si ha che $f(x)>0$ e$f''(x)>0$ si ha allora che
$$x_{1} = x_{0}-\frac{f(x_{0})}{f'(x_{0})} \leq x_{0}$$
inoltre
$x_1-\alpha=g(x_{0})-g(\alpha)=g'(\eta_{0})(x_{0}-\xi)=\cfrac{f(\eta_{0})_{}f''(\eta_{0})}{(f'(\eta_{0}))^{2}}(x_{0}-\alpha)>0$
e quindi
$$\alpha < x_{1}\leq x_{0}\leq\alpha + \delta$$
In modo analogo si dimostra per induzione che per i termini della successione vale
$$\alpha<x_{k+1}\leq x_{k} \leq \alpha+\delta, \ \ \ \ k>0$$
ne segue che 
$$\\lim_{ n \to \infty } x_{k}= \xi \in [\alpha,\alpha+\delta]$$
e dunque
$$\xi=g(\xi) \implies f(\xi)=0 \implies \xi = \alpha$$
