---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili Aleatorie Notevoli
---
alcune [[Variabili Aleatorie (Casuali)|variabili aleatorie]] importanti e molto usate in [[Statistica (STAT)|statistica]] sono le seguenti

#### Variabile Binoiale
Consideriamo il caso in cui ci interessano solo due esiti di una prova ripetuta $n$ volte 
chiamiamo solo una due due esiti “successo”  e questa ha probabilita $p\in (0,1)$
e _sia_ $X$ la _variabile aleatoria_ che _conta_ il numero di _successi_ ha quindi valori $\{ 0,1,\dots,n \}$ 
_allora_ questa è scritta come$$\mathcal{P}(X=h)=\begin{pmatrix}n \\ h\end{pmatrix} p^{h}(1-p)^{n-h} \ \ \ \ , 0 \leq h\leq n$$
dove 
- $p^{h}(1-p)^{n-h}$ è la probabilità che compaia u risultato con $h$ _successi_ e $(n-h)$ _insuccessi_. e questo vale per l _indipendenza_ dei risultati
- $\begin{pmatrix}n \\h \end{pmatrix}$ è il numero di modi di [[Combinatoria|disporre]] gli $h$ _successi_ e $(n-h)$ _insuccessi_

la [[Probabilita|probabilità]] totale è $1$ come conseguenza dell _binomiale_.

una variabile _aleatoria_ $X:\Omega \rightarrow\{ 1,\dots,n\}$ per cui $\mathcal{P}\{ X=h \}$ è data da questa formula con un qualsiasi $p \in (0,1)$ allora è detta _variabile binomiare_ di parametri $n,p$ indicata con $B(n,p)$ se $n=1$ allora viene detta _variabile di bernulli_ $B(p)$

#### variabili geometriche
Consideriamo il caso in cui ci interessano solo due esiti di una prova ripetuta $n$ volte 
chiamiamo solo una due due esiti “successo”  e questa ha probabilita $p\in (0,1)$
e _sia_ $X$ la _variabile aleatoria_ tale che $X=h$ indica  indica dopo quanti tentativi otteniamo il _primo successo_ 
_allora_ questa è scritta come$$\mathcal{P}\{ X=h \} = (1-p)^{h-1}p \ \ \ \ h \in  \mathbb{N}_{0}$$
infatti dato l evento $A_{i}$ successo alla privo $i$-esima$$ \begin{array}
\mathcal{P}(X=h) & = & \mathcal{P}(A_{1}^{c}\cap A_{2}^{c}\cap \dots \cap A_{h}) & = \\
\mathcal{P}(A_{1}^{c})\mathcal{P}(A_{2}^{c})\dots \mathcal{P}(A_{h}) & = & (1-p)^{h-1}p
\end{array}
$$
La variabile _aleatoria geometrica_ ha la proprietà di essere _senza memoria_ ovvero $$\mathcal{P}\{X=n+h|X>n\}=\mathcal{P}\{X=h\}$$
dove il $|$ è la [[Probabilita condizionata|probabilita condizionata]]

#### Variabile di Poisson
_sia_ un $\lambda>0$ un numero e $X:\Omega \rightarrow\mathbb{N}$ una  _variabile aleatoria_ nei naturali
_allora_ è $X$ una _variabile di Poisson_ 
_se_ vale $$\mathcal{P}(X=h)=e^{-\lambda}\frac{\lambda^{h}}{h!}$$
questa è una [[Probabilita|probabilità]] valida dobbiamo vedere che la probabilita totale è 1 ma e deve quindi valere $$\sum^{+\infty}_{h=0}\mathcal{P}(X=h)=1$$ ma questa è una conseguenza dello sviluppo esponenziale $$e^{\lambda}=\sum^{+\infty}_{h=0}\frac{\lambda^{h}}{h!}$$

questa _variabile aleatoria_ a prossima bene la variabile _[[#Variabile Binoiale|binomiale]]_ $B(n,p)$ quando $n$ è grande e $p$ e piccolo e quando vale $np \approx \lambda$. Overo quando il numero delle prove è alto e la probabilita di successo molto bassa, infatti la _variabile di poisson_ è anche detta _degli aventi rari_

#### Variabili uniformi su intervalli
dati due numeri reali $a <b$ la densita uniforme sul intervallo $[a,b]$ è costate sul intervallo e nulla al di fuori $$f(x)= \begin{cases}
	\frac{1}{1-b} & if  & a <x <b \\
0  & else & 
\end{cases}$$
#### Variabili esponenziali
la _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ con densita esponenziale di parametro $\lambda>0$ è definita come $$f(x)=\begin{cases}
	\lambda e^{-\lambda x} &  x>0 \\
    0  & x \leq 0
\end{cases}$$
e si vede che la densita è effettivamente una [[Probabilita|probabilità]] con l espressone $$  \left .\int_{0}^{+\infty} \lambda e^{-\lambda x}  \, dx =-e^{-\lambda x}\right|_{0}^{+\infty}=1$$
poiché la densita prende valori diversi da $0$ solo per $x$ positivi si ha che $\mathcal{P}\{X \leq 0  \}=0$

>[!tip]
>la variabile esponenzioale descrive _ad esempio_ il tempo di attesa tra due eventi aleatori

la _variabile esponenziale_ è _senza memoria_ e vale perciò che $$\mathcal{P}\{ X\leq s+t \mid X>s\} = \mathcal{P}\{ X \leq t \}$$
dove il $\mid$ è il simbolo per la [[Probabilita condizionata|probabilita condizionata]]




