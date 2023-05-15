---
type: nota
course: Calcolo Numerico
topic: 
tags: CN
---

Prev: [[Calcolo Numerico(CN)]]

# Calcolare gli zeri di una funzione
---

voglio studiare per quali input una data funzione $f$ sia $f(\boldsymbol{x})=0$. questi non si possono calcolare esattamente quindi si calcano delle approssimazioni.

### metodo della bisezione
questo metodo per carcere gli _zeri_ di una [[Funzioni|funzione]] $f:[a,b]\rightarrow \mathbb{R}$ si può applicare sotto le _ipotesi_ che 
- $f(a)f(b) < 0$. ovvero che i segni agli estremi del intervallo siano discordi.
- $f \in C^{0}([a,b])$ ovvero che $f$ sia _[[Continuità di una funzione|continua]]_ 
questo ci dice che _esiste almeno_ una soluzione dove $f(x)=0$. non possiamo dire quante. 
invece se la funzione è [[Funzione Monotona|Funzione Monotona]] esiste un unica soluzione.

il metodo consiste di fare una [[ricerca binaria]] su i valori di una funzione. si parte quindi da 
$a_{0} = a ,b_{0} = b$ e si calcola $c_{0}=\cfrac{a_{0}+b_{0}}{2}$ e si procede con il normale algoritmo di _ricerca binaria_
![[Pasted image 20230512163407.png]]

```pseudo
    \begin{algorithm}
    \caption{binary Serch}
    \begin{algorithmic}
      \Procedure{BinarySerch}{$a,b,c$}
        \For{k}
			\State $c_k = \cfrac{a_k+b_k}{2}$
	        \If{$f(a)f(b)\leq 0$}
	        \State$a_{k+1} = a_k$
	        \State $b_{k+1} = c_k$
	        \Elif{}
	        \State $a_{k+1} = c_k$
	        \State $b_{k+1} = b_k$
	        \EndIf
        \EndFor
      \EndProcedure
      \end{algorithmic}
  \end{algorithm}
```
questo metodo trova _una sola soluzione_ dipendentemente da i parametri di inizio che si scelgono. non ci da informazioni sulle altre soluzioni.

si utilizza un $for$ siccome posso calcolare esattamente il numero di _passi_ $k$ che mi servono per riuscire ad _approssimare_ il risultato con una tolleranza $tol$ scelta a piacere. questo sfruttando il fatto che posso sempre sapere la grandezza del intervallo che sto analizzando facendo $b_{k}-a_{k} = \cfrac{b-a}{2^{k}}$ e posso limitare questo intervallo dalla mia _tolleranza_ e avere quindi $\cfrac{b-a}{2^{k}} \leq tol$. risolvendo questa disequazione ottengo il numero di passi necessari.
$$
\begin{array}
\cfrac{b-a}{2^{k}}  & \leq &  tol \iff  \\
2^{k}\cdot tol  & \geq &  b-a  \\
2^{k}\cdot tol  & \geq &  \cfrac{b-a}{tol}  \\
k  & \geq & \left\lceil \log_{2}\left( \cfrac{b-a}{tol} \right) \right\rceil 
\end{array}$$
anche se va con il logaritmo $k$ nella pratica può crescere molto

sapendo che lo _zero_ della funzione è necessariamente al interno di questo intervallo possiamo dire che l errore di _approssimazione_ è limitato da   $|\alpha -c_{k}|\leq \frac{tol}{2}$  
dove  $c_{k}$ è lo _zero calcolato_ dal algoritmo e $\alpha$ lo _zero vero_.
![[Pasted image 20230512171901.png]]
questo algoritmo funziona siccome $b \geq a_{k+1} \geq a_{k}$ e $b_{k+1}\leq b_{k} \leq a$
ovvero che i vari $a_{k}$ e $b_{k}$ si spostano internamente e non si superano mai.



### Metodo di dei punti fissi
si trasforma il problema in un problema _equivalente_ 
si fa trasformando il calcolo degli zero di $f$ nel calcolo dei punti fissi di $g$
$$f(x)=0 \rightarrow  g(x)-x=0$$
e si dicono equivalenti quando l insieme delle soluzioni di $f(x)=0$ è uguale a quello di $g(x)-x=0$ che equivale a calcolare i [[Punti Fissi|punti fissi]] di $g$
$$f(\alpha)=0 \iff g(\alpha)=\alpha$$

conviene fare questa trasformazione siccome possiamo calcolare un punto fisso con i metodo interativi.
$$\begin{cases}
x_{0} \in [a,b] \\
k_{k+1} = g(x_{k})
\end{cases}$$
#### Teorema
se $g\in C^{0}$ quindi [[Continuità di una funzione|continua]] ,$x_{k} \in [a,b]\ \ \forall k>0$ e $\lim_{ k \to \infty }x_{k} = \alpha$ allora $\alpha = g(\alpha)$
##### Dimostrazione
$$\alpha =\lim_{ k \to \infty }x_{k+1} = \lim_{ k \to \infty }g(x_{k}) = g(\lim_{ k \to \infty }x_{k}) = g(\alpha) $$

#### Convergenza locale
questo metodo può solo _convergere localmente_ quindi ci sono degli intorni di $\alpha$ con convergono e altri che potrebbero non farlo. 
formalmente la convergenza locale è definita come

sia $g:[a,b]\rightarrow \mathbb{R} , \ \ \alpha = g(\alpha), \ \ \ \alpha \in (a,b)$ il metodo
$$\begin{cases}
x_{0} \in [a,b] \\
k_{k+1} = g(x_{k})
\end{cases}$$
_converge localmente_ se $\exists \rho>0: \forall x_{0}\in [\alpha-\rho,\alpha+\rho]$.
se scelgo un puto in questo intervallo ottengo che
1. $x_{k}\in [\alpha-\rho,\alpha+\rho]$ ovvero, _tutti_ i valori della successione restano nel intervallo
2. $\lim_{ k \to \infty }x_{k}=\alpha$ 


#### Teorema del punto fisso
sia $g:[a,b]\rightarrow \mathbb{R}, \ \ g \in C^{1}([a,b])$ ovvero che sia [[Continuità di una funzione|continua]] e _derivabile con derivata continua_.  $g(\alpha) = \alpha , \ \ \alpha \in (a,b)$
se $\exists \rho>0:|g'(x)|<1 \ \ \forall x \in [\alpha-\rho,\alpha +\rho] \implies$ 
- ovvero se il coefficiente angolare è tra -1 e 1 (cresce o decresce _poco_ in ogni punto)
$\forall x_{0} \in [\alpha-\rho,\alpha +\rho]$ _vale che_ il metodo [[#^51dd7d|converge localmente]] 

questo ci da un criterio per determinare se il metodo _converge localmente_.

##### Dimostrazione
si prende il massimo $\lambda \in \max_{x\in [\alpha -\rho,\alpha +\rho] }|g'(x)|<1$ so che questo $\lambda$ esiste al [[Teorema di approssimazione di Weierstrass|teorema di approssimazione di Weierstrass]] .
per dimostrare _la tesi_ dobbiamo dimostrare che 
$$|x_{k}-\alpha| \leq \lambda^{k}\rho \ \ \ \forall k \geq 0$$
1. siccome $\lambda$ è $<1$ possiamo dire che $\lambda^{k}\rho\leq\rho$ e quindi possiamo affermare che $$|x_{k}-\alpha| \leq \rho \implies x_{k}\in [\alpha-\rho,\alpha +\rho]$$
	- dove $|x_{k}-\alpha|$ è la _distanza_ di $x_{k}$ da $\alpha$ 
2.  si dimostra la convergenza siccome con $$ 0 \leq |x_{k}-\alpha|\leq $$
	- con il _limite_ $k\to \infty$ la _distanza_ viene schiacciata a $0$ per il [[Teorema del confronto dei carabinieri|teorema del confronto]] e quindi $x_k = \alpha$

si [[Tipi di dimostrazione|dimostra quindi induttivamente]] $|x_{k}-\alpha| \leq \lambda^{k}\rho \ \ \ \forall k \geq 0$
- $k=0$ si ha subito per le _ipotesi_ che $|x_{0}-\alpha| \leq \lambda^0\rho = \rho$. 
	- questo viene dal fatto che scegliamo $x_{0}\in [\alpha-\rho,\alpha +\rho]$ 
- assumo che la _diseguaglianza valga_ per $k$ e dimostro per $k+1$
	-  $|x_{k+1}-\alpha| = |g(x_{x_{k}})-g(\alpha)|= |g'(\eta)(k_{k}-\alpha)|=|g'(\eta)||k_{k}-\alpha|$ utilizzando il [[Teorema di Lagange]] che posso applicare per l ipotesi che per _l ipotesi_ $g \in C^1$ e allora posso scrivere
	- $|g'(\eta_{k})||k_{k}-\alpha| \leq|g'(\eta_{k})|\lambda^{k}\rho$ maggioro per  _ipotesi induttiva_ 
	- $|g'(\eta_{k})|\lambda^{k}\rho \leq\lambda\lambda^{k}\rho$ posso fare questa maggiorazione siccome  $\eta_{k} \in [\alpha-\rho,\alpha +\rho]$ e $\lambda$ è il massimo di quel intervallo
		- $\eta_{k} \in [\alpha-\rho,\alpha +\rho]$  siccome $x_{k} \in [\alpha-\rho,\alpha +\rho]$ per _ipotesi induttiva_  e $|\eta_k-\alpha| \leq |x_{k}-\alpha| \leq \rho$
	- e da qui troviamo $|x_{k+1}-\alpha| \leq \lambda ^{k+1}\rho$ _come volevasi dimostrare_

#### Corollario
sia $g:[a,b]\rightarrow \mathbb{R}, \ \ g \in C^{1}([a,b]) , \ \ g(\alpha) = \alpha , \ \ \alpha \in (a,b)$
_se_  $|g'(\alpha)| <1 \implies$  allora il metodo è _localmente convergente_
##### Dimostrazione
$h(x)= |g'(x)|-1$, e per composizione di funzioni continue si ha $h \in C^{0}([a,b])$
e quindi si ha che $h(\alpha)=|g'(x)|-1<0$ e per [[Teorema della permanenza del segno|teorema della permanenza del segno]] ho che $\implies \exists\rho>0:\forall x \in [\alpha-\rho,\alpha +\rho]$ e quindi vale il [[#Teorema del punto fisso|teorema del punto fisso]]

### Ordine di convergenza 
gli _ordini di convergenza_ servono a confrontare i metodi del punto fossi con $g$ diverse

sia una successione $\{x_{k}\}$ _convergente_ a $\alpha$ punti fisso per $g(x)$. 
se $x_{k} \not= \alpha \ \ \forall x_{k}$ e se esiste una valore $p\geq 1$ tale che. 
$$
\begin{array}{}
\lim_{ k \to \infty } \cfrac{|x_{k+1}-\alpha|}{|x_{k}-\alpha|^{p}}  = \gamma  & \text{with}  &  \begin{cases}
0 < \gamma \leq 1  &  \text{if} &  p=1 \\
\gamma>0  & \text{if} & p>1
\end{cases}
\end{array}
$$
si dice che la successione _converge con ordine_ $p$
questo significa che per $k \to \infty$ ho che 
$$e_{k+1}=|x_{k+1}-\alpha| \approx \gamma \cdot |x_{k}-\alpha|^p$$
questo significa che 
- per $p=1$ vuol dire che l errore si riduce solo di un fattore $\gamma$ 
- per $p>1$ vuol dire che l errore si riduce più velocemente
- non ha senso di parlare di $p<1$ siccome non vedo una riduzione del errore ovvero la successione non sta convergendo

nomenclature
- con $p=1$ e $0<\gamma<1$ si dice _convergenza lineare_
- con $p=1$ e $\gamma =1$ si dice _convergenza sublineare_ 
	- converge molto lentamente
- con $p=2$ e $\gamma>0$ si dice _convergenza quadratica_
	- il metodo converge molto velocemente verso un errore vicino alla [[Aritmetica di Macchina#Precisione di macchina|precisione di macchina]]

### Metodo delle tangenti o di newton
è un metodo per cercare gli _zero_ di una funzione $f\in C^1$ é un metodo nella forma
$$\begin{cases}
x_{0}  \in \mathbb{R}  \\
x_{k+1}=x_{k}-\cfrac{f(x_{k})}{f'(x_{k})}
\end{cases}$$
è si basa sul idea di far passare una _[[retta tangente|retta tangente]]_ al punto $(x_k,f(x_k))$ e di prendere come prossima $x_{i+1}$ il punto di intersezione della tangente al asse delle $x$.
per trovare il _prossimo punto del interazione_ si calcola risolvendo il seguente sistema$$
\begin{cases}
y-f(x_{0})=f'(x_{0})(x-x_{0}) \\
y = 0
\end{cases}$$
dove 
- la prima espressione è la _retta tangente_
- la seconda espressione é l intersezione con l asse $x$

questo metodo funziona finche non arriviamo ad un [[Minimi e Massimi|minimo o ad un massimo]] in quei punti la [[derivata|derivata]] è pari a $0$ e il metodo non è definito. _geometricamente_ la tangente è parallela e non tocca l asse delle $x$.


questo metodo può essere visto sotto forma del _[[#Metodo di dei punti fissi|metodo del punto fisso]]_ prendendo in particolare $g(x) =x_{k}-\cfrac{f(x_{k})}{f'(x_{k})}$

##### Radici semplici 
preso $\alpha:f(\alpha)=0$ è detta _radice semplice_ per $f\in C^{1}([a,b])$  se $\alpha \in (a,b)$ e $f'(\alpha)\not=0$
#### Teorema
_sia_ $f:[a,b]\rightarrow\mathbb{R}, \ \ f\in C^{2}([a,b]), \ \ f(\alpha)=0$ e $\alpha \in (a,b)$ 
_se_ $\alpha$ è _semplice_ cioè se $f'(\alpha) \not =0$
_allora_ il metodo $x_{k+1}=x_{k}-\cfrac{f(x_{k})}{f'(x_{k})}$ è _localmente convergente_ ad $\alpha$ e
_se_ la successione ${x_k}$ con $x_k \not=\alpha$ 
_allora_ la convergenza è almeno _quadratica_ ovvero
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
 e a questo punto ho quasi finito siccome mi basta dimostrare che $|g'(\alpha)|<1$ e usare il _[[#Corollario|corollario del punto fisso]]_. siccome $f'(\alpha) \not = 0$  allora $g'(x)$ é ben definita e siccome $f(\alpha) = 0$ $g'(\alpha) =0$ quindi ho che $|g'(\alpha)|<1$ e di conseguenza il metodo _converge localmente_
##### Dimostrazione di convergenza quadratica
dobbiamo dimostrare che $$\lim_{ k \to \infty } \cfrac{|x_{k+1}-\alpha|}{|x_{k}-\alpha|^{2}}  = \ell \in \mathbb{R}$$
tenda ad un numero. quindi bisogna risolvere il [[Limiti|limite]] si fa lo [[Sviluppi di Taylor|sviluppo di Taylor]] applicato ad $f(x)$ nel punto $x_k$
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
_si ha che_ il metodo delle tangenti con $x_{0}\in S$ genera _successioni monotone decrescenti_ e convergenti ad $\alpha$

##### Dimostrazione
si osserva che $f'(x)$ ha segno costante in $S$  prendendo il caso $f'(x)>0$ si ha che $f(x)>0$ e$f''(x)>0$ si ha allora che
$$x_{1} = x_{0}-\frac{f(x_{0})}{f(x_{0})} \leq x_{0}$$
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
