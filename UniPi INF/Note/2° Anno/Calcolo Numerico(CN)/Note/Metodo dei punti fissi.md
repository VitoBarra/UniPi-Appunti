---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Metodo dei punti fissi
---
è un _metodo iterativo funzionale_ usato per calcolare gli zeri di un funzione. 
Si trasforma il problema del [[Metodi iterativi funzionali (calcolo degli zeri)|calcolo degli zeri]] in un problema _equivalente_ ovvero invece di calcolare gli zeri di  $f$ si calcolano i _punti fissi_ di  $g$
$$f(x)=0 \rightarrow  g(x)-x=0$$
e si dicono _equivalenti_ quando l insieme delle soluzioni di $f(x)=0$ è uguale a quello di $g(x)-x=0$ che equivale a calcolare i [[Punti Fissi|punti fissi]] di $g$
$$f(\alpha)=0 \iff g(\alpha)=\alpha$$

conviene fare questa trasformazione siccome possiamo calcolare un punto fisso con i metodo interativi.
$$\begin{cases}
x_{0} \in [a,b] \\
x_{k+1} = g(x_{k})
\end{cases}$$
questo metodo può  _[[Convergenza locale per metodi interativi funzionali|convergere localmente]]_ quindi ci sono degli [[Intorno|intorni]] di $\alpha$ con convergono e altri che potrebbero non farlo. 

#### Teorema
_sia_ la funzione $g$ la funzione di un metodo
_se_ $g\in C^{0}$ quindi [[Continuità di una funzione|continua]] ,$x_{k} \in [a,b]\ \ \forall k>0$ e $\lim_{ k \to \infty }x_{k} = \alpha$
_allora_ $\alpha = g(\alpha)$
##### Dimostrazione
$$\alpha =\lim_{ k \to \infty }x_{k+1} = \lim_{ k \to \infty }g(x_{k}) = g(\lim_{ k \to \infty }x_{k}) = g(\alpha) $$

#### Teorema del punto fisso
_Sia_ $g:[a,b]\rightarrow \mathbb{R}, \ \ g \in C^{1}([a,b])$ ovvero che sia [[Continuità di una funzione|continua]] e _derivabile con derivata continua_.  $g(\alpha) = \alpha , \ \ \alpha \in (a,b)$
_Se_ $\exists \rho>0:|g'(x)|<1 \ \ \forall x \in [\alpha-\rho,\alpha +\rho] \subseteq [a,b]$ 
- ovvero se il coefficiente angolare è tra -1 e 1 (cresce o decresce _poco_ in ogni punto del _insieme circolare_ intorno al punto $\alpha$)
_Allora_ 
1. $x_{k} \in [\alpha-\rho,\alpha +\rho] \ \ \ \ \forall k \geq 0$ 
2. Il metodo [[Convergenza locale per metodi interativi funzionali|converge localmente]] 

questo ci da un criterio per determinare se il metodo _converge localmente_.

##### Dimostrazione
si prende il massimo $\lambda = \max_{x\in [\alpha -\rho,\alpha +\rho] }|g'(x)|<1$ so che questo $\lambda$ esiste al [[Teorema di Weierstrass|teorema di Weierstrass]].

dimostrare la seguente diseguaglianza ci permette di dimostrare _la tesi_
$$|x_{k}-\alpha| \leq \lambda^{k}\rho \ \ \ \forall k \geq 0$$
siccome
1.  $\lambda$ è $<1$ possiamo dire che $\lambda^{k}\rho\leq\rho$ e quindi possiamo affermare che $$|x_{k}-\alpha| \leq \lambda^{k}\rho\leq\rho \implies x_{k}\in [\alpha-\rho,\alpha +\rho]$$questa implicazione vale siccome $|x_{k}-\alpha|$ è la _distanza_ di $x_{k}$ da $\alpha$ 
2.  si dimostra la convergenza siccome con $$ 0 \leq |x_{k}-\alpha|\leq \lambda^{k}\rho$$con il _limite_ $k\to \infty$ la _distanza_ viene schiacciata a $0$ per il [[Teorema del confronto dei carabinieri|teorema del confronto]] e quindi $x_k = \alpha$


si [[Tipi di dimostrazione|dimostra quindi induttivamente]]
vogliamo quindi dimostrare che  
$$|x_{k}-\alpha| \leq \lambda^{k}\rho \ \ \ \forall k \geq 0$$
casa base abbaiamo
$k=0$ si ha subito per le _ipotesi_ che $$|x_{0}-\alpha| \leq \lambda^0\rho = \rho$$e questo è vero siccome scegliamo $x_{0}\in [\alpha-\rho,\alpha +\rho]$ 

ora assumo che la _diseguaglianza valga_ per $k$ 
$$|x_{k}-\alpha| \leq \lambda^k\rho \leq \rho$$
e dimostro  per $k+1$ 

Utilizzando il [[Teorema di Lagrange]] che posso applicare   siccome _per ipotesi_ vale $g \in C^1([a,b])$  posso scrivere
$$\begin{array}{}
|x_{k+1}-\alpha| &=& |g(x_{k})-g(\alpha)| & =\\ |g'(\eta_{k})(x_{k}-\alpha)|&=&|g'(\eta_{k})||x_{k}-\alpha|
\end{array}$$
un conseguenza di _Lagrange_ e anche che $$|\eta_{k}-\alpha| \leq |x_{k}-\alpha| \leq \rho$$ovvero la distanza di $\eta_{k}$ da $\alpha$ è minore rispetto alla distanza tra $x_k$ e $\alpha$ è importante notare che per utilizzare _Lagrange_ dobbiamo avere la garanzia che $x_k$ siano tutti in $C^{1} ([a,b])$ ma questo è vero per _ipotesi induttiva_

ora e quindi ho da dimostrare che $$|x_{k+1}-\alpha| =|g'(\eta_{k})||x_{k}-\alpha| \leq \lambda^{k+1}\rho$$
per _ipotesi induttiva_ é vero che
$$\begin{array}{}
|x_{k}-\alpha|  & \leq & \lambda^{k}\rho \\

|g'(\eta_{k})||x_{k}-\alpha|  & \leq &  |g'(\eta_{k})|\lambda^{k}\rho
\end{array}
$$
da qui posso scrivere $$|g'(\eta_{k})||x_{k}-\alpha|\leq|g'(\eta_{k})|\lambda^{k}\rho \leq\lambda\lambda^{k}\rho$$ essendo $\lambda$ il valore massimo la maggiorazione è valida e quindi abbiamo che $$|x_{k+1}-\alpha| \leq \lambda ^{k+1}\rho$$ _come volevasi dimostrare_

#### Corollario
sia $g:[a,b]\rightarrow \mathbb{R}, \ \ g \in C^{1}([a,b]) , \ \ g(\alpha) = \alpha , \ \ \alpha \in (a,b)$
_se_  $|g'(\alpha)| <1 \implies$  allora il metodo è _localmente convergente_
##### Dimostrazione
$h(x)= |g'(x)|-1$, e per composizione di funzioni continue si ha $h \in C^{1}([a,b])$
e quindi si ha che $h(\alpha)=|g'(\alpha)|-1<0$ e per [[Teorema della permanenza del segno|teorema della permanenza del segno]] ho che $\implies \exists\rho>0:\forall x \in [\alpha-\rho,\alpha +\rho]$ e quindi vale il [[#Teorema del punto fisso|teorema del punto fisso]]