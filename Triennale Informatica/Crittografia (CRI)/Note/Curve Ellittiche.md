---
Course: "[[Crittografia (CRI)]]"
topic: nota
tags:
  - CRI
---

# Curve Ellittiche
---
è un tipo di cifrario a [[Cifrari a chiave Asimmetrica|chiave asimmetrica]] quindi abbiamo il concetto di _chiave pubblica_ e _chiave privata_.

nella forma generale una _curva ellittica_ $E$  su un [[Campi|campo]] $\mathcal{K}$ 
è l insieme dei punti $(x,y) \in \mathcal{K}^{2}$ definito dal equazione

$$y^{2}+axy+by=x^{3}+cx^{2}+dx+e$$
dove $a,b,c,d,e \in \mathcal{K}$.

Se la [[Campi#Caratteristica|Caratteristica]] di $\mathcal{K}$ è _diversa_ da $2,3$ allora l equazione si può ridurre nella _forma normale di Weierstrass_. Abbiamo quindi
$$y^{2}=x^{3}+ax+b$$

In crittografia si utilizza questa forma siccome gli si può attribuire la struttura algebrica di un [[Gruppo abeliano|gruppo abeliano additivo]]

Una Curva ellittica è quindi l insieme dei punti $(x,y) \in \mathcal{K}$ tale che sia soddisfatta l equazione nella forma _normale di Weierstrass_ oltre ad avere il punto neutro



### Curve Ellittiche sui Reali
per avere una visualizzazione delle curve ellittiche si possono utilizzare i numeri reali.
Sia quindi $\mathcal{R}$ il [[Campi|campo]] dei _Numeri reali_ con elemento neutro $O$ il punto al infinito sul asse delle ordinate.
La curva ellittica sarà quindi definita da 
$$E(a,b)=\{(x,y) \in \mathcal{R}^{2}\mid y^{2}=x^{3}+ax+b \}$$
dove $a,b \in \mathcal{R}$ 
la curva $E(a,b)$ contiene il punto $O$ in direzione del asse $y$ siccome c è un asintoto verticale
![[Pasted image 20230810135800.png]]
le curve che soddisfano l equazioni sono di due tipi, una a due componenti quando le radici reali sono 3 e una ad un solo componente quando le radici reali è unica.

per far funzionare questa definizione dobbiamo aggiungere il vincolo $$4a^{3}+27b^{2} \not = 0$$per evitare che il [[Polinomi|polinomio]] $x^{3}+ax+b$ abbia radici multiple e di conseguenza la curva non avrà [[Funzioni differenziabili|punti di inderivabilita o derivate non univoche]] come cuspidi o nodi
![[Pasted image 20230811205047.png]]

in entrambi le tipologie di curve vale sempre la simmetria rispetto al asse del ascisse e quindi vale che se $$P=(x,y) \in E(a,b) \implies -P=(x,-y) \in E(a,b)$$Mentre per il punto al infinito $O$ il suo _speculare_ è $O$ stesso.

per le applicazioni crittografiche ci interessa la proprietà di intersezione con una retta di questa curva. 
infatti intersecando una curva di terzo grado e una di primo (una [[Rette|retta]]) otteniamo che e soluzioni _reali_ sono al più 3.
Infatti avremmo un _unica soluzione reale_ quando  
- si interseca la curva con una _retta orizzontale_ con _ordinata_ abbastanza _elevata_ o abbastanza _bassa_
- si interseca la curva con una _retta verticale_  con un _ascissa_ abbastanza _elevata_ o abbastanza _bassa_, questa interseca la curva solo nel punto $O$. 
Negli altri casi le _soluzioni reali_ sono sempre 3.

nel caso di 3 punti di intersezione _reali_ indicati con $P,Q,R$ abbiamo che : 
- se $Q=P$ la _retta_ è una [[Retta tangente|retta tangente alla curva]] mentre $R$ sarà un terzo punto della curva
- se $Q = -P$ la _retta_ sarà verticale e eventualmente tangente, Il punto $R$ sarà il punto al infinito $O$ 
- Altrimenti i 3 punti sono distinti e sono sulla curva

![[IMG_0629.jpeg]]

#### Somma su curve ellittiche reali
per definire l addizione sulle curve ellittiche si sfrutta la proprietà del numero di intersezioni infatti è definita come 
_sia_ una $E(a,b)$ _curva ellittica_  e $P,Q,R$ tre punti sulla curva
_se_ questi sono disposto su una retta
_allora_ la loro somma è il punto al infinito$$P+Q+R =O$$e da qui ricordando che $O$ è l elemento _neutro_ del operazioni si può ricavare la regola di somma come $$
 \begin{array}{}
 P+Q  & = &  -R+O \\
 P+Q  & = & -R 
\end{array}
 $$Questa [[Operazioni algebriche|operzione]] è _ben definita_ in quanto essendo la _curva simmetrica_ rispetto al asse del asciasse abbiamo che $-R\in E(a,b)$ e nel caso particolare della tangente abbiamo che $R=O$ ma questo non è un problema siccome lo speculare di $O$ resta $O$ e quindi $-R=O$ quindi è ancora un punto della _curva ellittica_.
![[IMG_0627.jpeg]]


Questa operazioni insieme alla curva permette di costruire la struttura algebrica di un [[Gruppo abeliano|gruppo abeliano]] siccome soddisfa le proprietà necessarie infatti abbiamo che 
_Chiusura_: $\forall P,Q \in E(a,b), P+Q \in E(a,b)$ 
_Elemento neutro_: $\forall P \in E(a,b). P +O = O +P =P$ 
	abbiamo che $Q =O$  e la retta che passa tra $P$ e $Q$ è una retta _verticale_ interseca nel punto $R=-P$ e sostituendo abbiamo che $P+O=-(-P)$
_Inverso_: $\forall P \in E(a,b)\exists!Q=-P \in E(a,b). P+Q=Q+P=O$ 
rispetta _[[Proprietà del operazioni - Associativa|Associativà]]_ e _[[Proprietà del operazioni - Commutativita|Commutatività]]_

possiamo anche definire $P+Q$ partendo della coordinate stesse di $P$ e $Q$ 
_siano_ $P=(x_{P},y_{P})$ e $Q =(x_{Q},y_{Q})$ 
_allora_ si può trovare il punto $-R=S=(x_{S},y_{S})$ come 
$$
\begin{array} {}
x_{S} & = & \lambda^{2} -x_{P} & -x_{Q} \\
y_{S}  & = &   \lambda(x_{P}-x_{S})  & -y_{P}
\end{array}$$
con $\lambda= \cfrac{y_{Q}-y_{P}}{x_{Q}-x_{P}}$ nel caso $Q \not= \pm P$
	 dove $\lambda$ è il [[Rette|coefficiente angolare]] della _retta_ passante per i punti $P$ e $Q$
con $\lambda =\cfrac{3x^{2}_{P}+a}{2y_{P}}$ nel caso $Q = P$. 
	 dove $\lambda$ è il _coefficiente angolare_ della [[Retta tangente|retta tangente]] a $P$ e il punto che stiamo calcolando è $S = P+Q = 2P$ e questa viene dalla [[Differenziazione Implicita|differenziazione Implicita]] della equazione della curva
	 _Se_ $y_{P}=0$ _allora_ $S =2P= O$
 nel caso $Q = -P$
	 si ha che $S=P +(-P)=O$
	 
>[!note]- Da dave viene?
>questi risultati vengono dalla [[Rette#Retta passante per 2 punti|formula della retta passante per i punto]] $P$ e $Q$ e poi mettendo a sistema con l equazione della _curva ellittica_, trovate queste coordinate bisogna invertire il sengno della $y$ per trovare il punto speculare (ovvero stiamo prima calcolando $R$ e poi $S=-R$)

>[!warning]
>Le curve ellittiche su reali non sono adatte ad applicazioni crittografiche, questo perchè la crittografia ha bisogno di fare conti veloci e precisi e questo non è possibile con i reali  per via degli [[Tipi di Errore nel calcolo numerico|errori di approssimazione]] introdotto dalla _rappresentazione_ e dal _calcolo_

### Curve ellittiche su campi finiti
sono _curve ellittiche_ definite su _[[Campi|campi]] finiti_  
Come campi finiti per le _curve ellittiche_ preso un [[Numeri primi|primo]] $p$  si può utilizzare l [[Insieme dei coprimi|insieme]] $\mathcal{Z}_{p}$. Siccome la [[Campi#Caratteristica|caratteristica]] di $\mathcal{Z}_{p}$ è sempre $p$ possiamo scegliere $p>3$ per poter usare la _forma normalizzata di Weierstrass_ 

Se restringiamo i coefficienti e le variabili ad essere al interno di $\mathcal{Z}_{p}$ abbiamo le _curve ellittiche prime_ 
dunque prendo $a,b \in\mathcal{Z}_{p}$ una _curve ellittiche prima_ è definita come
$$
\begin{array} {}
E_{p}(a,b)  =   \\
\{(x,y)\in \mathcal{Z}_{p}^{2}\mid y^{2} \mod p = (x^{3}+ax+b)\mod p\} \cup \{O\}
\end{array}
$$
dalla definizione vediamo subito che non stiamo piu parlando di una curva ma di una _nuvola di punti_.

notiamo che tutti i punti sono compresi tra 
$$
\begin{array} {}
0  & \leq  & x  & \leq  & q-1  \\
0  & \leq  & y &  \leq & q-1
\end{array}$$
e siccome vale che $-y \mod p = p-y$ abbiamo che non ci sono più valori negativi e la simmetria si è spostata dal asse delle ascisse al asse _orizzontale_ $y =\cfrac{p}{2}$
![[Pasted image 20230811105325.png]]
	con $p = 67$
abbiamo quindi che il punto speculare è definito come 
$$
\begin{array}{}
P &  = &  (x,y)  & \\
-P & = & (x,-y \mod  p) & =  & (x,p-y)
\end{array}
$$sotto l assunzione che  $x^{3}+ax+b \mod  p$ non ha _radici multiple_ _ovvero vale_ che  $$4a^{3}+27b^{2} \mod p\not=0$$alla curva _ellittica prima_  $E_{p}(a,b)$  si può associare la [[Strutture algebriche|struttura algebrica]] del [[Gruppo abeliano|Gruppo abeliano]] _finito_ rispetto al operazione di addizione

Le regole per calcolare $P+Q$ si possono riadattare dalla _versione continua_ facendo le operazioni in modulo quindi
_siano_ $P=(x_{P},y_{P})$ e $Q =(x_{Q},y_{Q})$ 
_allora_ vale 
$$\begin{array} {}
x_{S} & = & \lambda^{2} -x_{P} & -x_{Q}  & \mod  p \\
y_{S}  & = &   \lambda(x_{P}-x_{S})  & -y_{P}   &  \mod  p
\end{array}$$
con $\lambda= \cfrac{y_{Q}-y_{P}}{x_{Q}-x_{P}} \mod  p$ nel caso $Q \not= \pm P$
con $\lambda =\cfrac{3x^{2}_{P}+a}{2y_{P}} \mod  p$ nel caso $Q = P$. 
	in questo caso $S = 2P$ 
	si deve calcolare l [[Inverso di un numero in algebra modulare|inverso]] in modulo del denominatore che _esiste unico_ [[Inverso di un numero in algebra modulare#Teorema esistenza ed unicità del inverso|perche]] $p$ [[Numeri primi|primo]] se $y_{p}=0$ allora l inverso non è definito e  $S=O$  
nel caso $Q = -P$
	 si ha che $S=P +(-P)=O$


#### Ordine della curva
l _ordine della curva_  è il numero di punto che una curva $E_{p}(a,b)$ contiene

si può dimostrare che una _curva ellittica prima_  $E_{p}(a,b)$ può contenere al massimo $2p+1$ punti.
dove $2p$ sono le coppie $(x,y),(x,-y)$ che soddisfano le equazione e il $+1$ viene dal punto al infinito 
>[!question]- da capire
>perchè solo $p$ punti?

Si può dimostrare che ci sono esattamente $\cfrac{p-1}{2}$ _[[Residui quadratici in modulo|residui quadratici]]_  tra gli elementi di  $\mathcal{Z}_{p}$ oltre allo 0 

da qui possiamo dire che in _generale_ la curva $E(a,b)$ contiene $\Theta(p)$ _punti_ considerando che i _[[Residui quadratici in modulo|residui quadratici]]_ in $\mathcal{Z}_{p}$ sono $\cfrac{p-1}{2}$ e che per simmetria si moltiplica per 2 il numero di punti.


In generale non tutti i valori di $x \in \mathcal{Z}_{p}$ danno luogo ad un _[[Residui quadratici in modulo|residuo quadratico]]_ presente nel campo infatti ci sono esattamente  $\cfrac{p-1}{2}$ punti che non hanno un _residuo quadratico_, ragionando sulla definizione della curva e notato che l espressione $y^{2}\mod p$ avrà sempre e solo valori che sono residui quadratici in $\mathcal{Z}_{p}$ possiamo dire che non ci sarà mai un punto sulla curva che abbia come _ordinata_ un numero che non è un _residuo quadrato_ 

Valori diversi di $x$ possono generare più volte _stesso residuo quadratico_
![[Pasted image 20230812035526.png]]
	i valori sulla sinistra sono i valori di $y^{2}\mod 7$ che come si vede sono solo i _[[Residui quadratici in modulo]]_, e questi si ripetono per simmetria.
	mentre i valori in altro sono i valori di $x^{3}+x \mod  7$ $a=1,b=0$ 
	come si vede valori diversi di $x$ possono dare piu volte lo stesso _scarto quadratico_ 
	riga e colonna dove scarto quadratico e valore del equazione sono uguali sono segnati con una $X$ e indicano un punto nella curva ellittica $E_{p}(a,b)$


##### Teorema di Hasse
_Sia_ $E(a,b)$ una curva ellittica 
_Allora_ L ordine $N$ di $E(a,b)$ verifica la diseguaglianza
$$|N-(p+1)| \leq 2 \sqrt{ q }$$


#### ordine di un punto
l ordine di un punto su una _curva ellittica_ è il più piccolo intero positivo $n$ tale che $nP=O$  
alcune proprietà del ordine dei punti sono
- $n < N$ dove $N$ è l ordine della curva.
	- il numero di salti su punti distinti è minore del numero di punti
> [!question]-
> si potrebbe tonare in un punto e generare un ciclo? capire se è possibile che succeda 
### Curva ellittica binaria
sono curve ellittiche dove coefficienti e valori vengono dal [[Campi|campo]] $GF(2^{m})$ dove $GF$ sta per [[Campo di Galois|Campo di Galois]]. Costituito da $2^{m}$ elementi che si possono pensare come tutti gli interi binari di $m$ cifre.

La [[Campi#Caratteristica|Caratteristica]] di questo campo è 2 di conseguenza non si può utilizzare la _forma normale di Weierstrass_ e avremmo che la curva ellittica è definita come
$$E_{2^{m}}(a,b)\{(x,y)\in  GF(2^{m})^{2}\mid y^{2}+xy=x^{3}+ax^{2}+b\} \cup \{O\}$$
con $a,b \in GF(2^{m})$ 

#### Definizione di somma curva binaria
se $b \not = 0$ possiamo dire che $E_{2^{m}(a,b)}$ è un [[Gruppo abeliano|gruppo abeliano additivo]] con la addizione definita come

- $\forall P =(x_{p},y_{p}) \in E_{2^{m}}(a,b) : P+O =P$ e $-P = (x_{P},x_{P}+y_{P})$
- $\forall P,Q \in E_{2^{m}(a,b)}$ con $P \not = \pm Q$ si ha che $P+Q=S$ dove $$\begin{array}{}
	x_{S}  & =  & \lambda^{2}+\lambda+x_{P}+x_{Q}+a  \\
	y_{P} &  =  & \lambda(x_{P}+x_{S})+x_{S}+y_{P}
\end{array}$$ dove $\lambda = \cfrac{y_{P}+y_{Q}}{x_{P}+x_{Q}}$
- $\forall P =(x_{p},y_{p}) \in E_{2^{m}}(a,b), 2P=O$ se $x_{P}=0$ altrimenti $2P=S$ con $$\begin{array}{}
x_{S}  & =  & \lambda^{2}+\lambda +a \\
y_{S}  & =   & x^{2}_{P}+(\lambda+1)x_{S}
\end{array}$$dove $\lambda = \cfrac{x_{P}+y_{P}}{x_{P}}$


#### Ordine della curva
Anche per la _curva ellittica binaria_ vale il _teorema di hassel_ e quindi abbiamo che l ordine della curva $E_{2^{m}}(a,b)$ soddisfa l equazione  
$$|N -(2^{m}+1)| \leq 2 r\sqrt{2^{m}}$$


### Confronto curve prime e curve binarie
per come sono fatte le _curve binarie prime_ sono più adatte al software mentre le _curve ellittiche binarie_ sono più adatte al hardware

