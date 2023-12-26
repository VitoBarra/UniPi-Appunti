---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Probabilità sui numeri Reali
---
sono probabilita mappate dai reali a valori che rispettano la definizione di [[Definizione di Probabilita|Definizione di Probabilita]]
#### Funzione di massa discreta (Definizione)
si parla di _probabilita discreta_ dove la probabilita è concentrata su una successione _finita_ o _finita e numerabile_ che è la stessa della [[Probabilita con distribuzione uniforme|Probabilita con distribuzione uniforme]] 
_siano_ $x_1, \dots,x_{n}$  una successione di punti, e posto che $p(x_{i})= \mathcal{P}(\{x_{i}\})$
_allora_ per oggi $A\subseteq \mathbb{R}$ vale $$\mathcal{P}(A)=\sum_{x_{i}\in  A}\mathcal{P}(\{   x_{i}\})=\sum_{x_{i}\in  A}p(x_{i})$$
>[!tip]
> è importante che la definizione si possa applicare a qualsiasi sottoinsieme di $\mathbb{R}$
##### Funzione di massa (Definizione)
si chiama _funzione di massa_ o anche _densita discreta_ della probabilita discrete $\mathcal{P}$ la funzione $p(x_{i})=\mathcal{P}(x_{i})$

per conoscere i valori della [[Funzioni|funzione]] di massa basta conoscere i valori della _probabilità_ dei singoli punti $x_{i}\dots, x_{n}$ e quindi abbiamo che $p_{i}=p(x_{i})=\mathcal{P}(x_{i})$. e la _funzione di massa_ si pio definire su tutto l insieme $\mathbb{R}$ mettendo tutti punti non prima elencati a $0$
Devono valere le proprietà della [[Definizione di Probabilita|probabilità]] per fa si sia una funzione di massa valida e quindi deve valere che
- $\forall p_{i} \geq 0$
- $\sum_{i}^{n}p_{i}=1$
se questo vale la probabilita è indicata dalla sola _funzione di massa_.

##### Esempio
Scegliere a caso un numero tra $0$ e $1$

l ”_universo_” più intuitivo è $\Omega=[0,1]$ e  posso definire gli _eventi_ come $A=[a,b] \subset \Omega$ e posso assegnare ad ogni vento una [[Definizione di Probabilita|Definizione di Probabilita]] $\mathcal{P}(A)=(b-a)$ ovvero la _lunghezza_ del insieme.

Inoltre la _probabilità_ non cambia per traslazioni $\mod  1$ infatti vale che $\mathcal{P}(A)=\mathcal{P}(A+c)$ dove $A+c$ si intende il traslatato $\mod 1$ di $A$

in questo caso si puo vedere che ci sono eventi _trasfucrabili_ ma non _impossibili_ infatti abbiamo che preso un $x \in [0,1]$ per ogni $n$ si ha che $\{x\} \subseteq \left[ x-\frac{1}{n},x+\frac{1}{n} \right]=A$ si ha che $\mathcal{P}(x) \leq \frac{2}{n}$ siccome la probabilità di prendere un elemento dal insieme $A$ è $\mathcal{P}(A)=\frac{2}{n}$ e $x$ ne è un [[Insiemi Matematici|sotto insieme]], in piu siccome ci sono _infinite_ scelte nel insieme abbiamo che $\mathcal{P}(x)=0$  e quindi l evento $\{x\}$ è un evento _trascurabile_ ma non _imposibile_ siccome un numero viene scelto

>[!tips] 
>estendere la _densità discrta_ a tutti i sottoinsieme dell intervallo $[0,1]$ e questo si dimostra con il [[Contro esempio di vitali|contro esempio di vitali]]
#### Densità di probabilità (Definizione)
Si chiama _densita di probabilita_ sulla retta reale una funzione a valori positivi $\mathcal{f}: \mathbb{R} \rightarrow [0,+\infty[$ [[Integrali|integrabile]] e tale che $\int^{+\infty}_{-\infty}f(x) \, dx=1$ ad essa è assicurala una probabilita mediante la formula $$\mathcal{P}(A)= \int _{A}f(x) \, dx $$per assicurarci che questa sia una _probabilita_ valida notiamo che 
$$\mathcal{P}(\mathbb{R})=\int_{\mathbb{R}} \, f(x)dx=1$$
e che presi due _eventi_ $A$ e $B$ se $A \cap B = \emptyset$ allora $$\mathcal{P}(A \cup B)= \int_{A}f(x) \, dx  \,+\int_{B} f(x) dx = \mathcal{P}(A)+\mathcal{P}(B)$$per controllare che sia _[[Definizione di Probabilita#$ sigma$-Algebra|numerabilmente additiva]]_ e che quindi rispetti la _definizione di probabilita assiomatica_  basta controllare che l integrale vade al limite siccome vale il $\iff$ con l essere _numerabilmente additiva_ e questo è verificato da un risultato chiamato  [[Teorema di Beppo-Levi|teorema di beppo levi]].

Le probabilita definite su _densità_ _non_ è definibile su tutti i sotto insimi di $\mathbb{R}$ ma solo su quelli che _sono misurabili_ che non è un problema siccome in statistica non capita mai insiemi _non misurabili_ 

##### Esempio
il caso di scegliere un numero $x\in [0,1]$ è un caso particolare di _probabilita_ associata ad una _densità_. abbiamo che$$f(x)=\begin{cases}
1  &  0 \leq x \leq 1 \\
0  & altrimenti 
\end{cases}$$
e vale come il caso discreto $$\mathcal{P}(x)=\int_{\{ x \}}f(x)  \, dx=0 $$ è trascurabile 






