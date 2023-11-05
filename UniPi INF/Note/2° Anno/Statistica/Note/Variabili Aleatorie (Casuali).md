---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili Aleatorie (Casuali)
---
in [[Statistica (STAT)|statistica]] le _variabili aleatorie_ sono uno strumento matematico che ci permettono di dare un formalismo matematico piu agile rispetto al solo _[[Definizione di Probabilita|Spazzio di probabilita]]_ $(\Omega,\mathcal{F},\mathcal{P})$ che è associato ad un esperimento che vogliamo studiare.
Infatti spesso non ci c’interessa l esito specifico del esperimento ma la _variabilita_ tra gli esiti dello stesso esperimento.

le _variabili aleatorie_ ci permettono di studiare la _variabilità_ di tra gli esiti dello stesso esperimento, ovvero sullo stesso _spazzio di probabilita_,  ripetuto piu volte e sono formalizzate con [[Funzioni|Funzioni]] di $\Omega$

### Variabili aleatore (Definizione)
_sia_ $(\Omega,\mathcal{F},\mathcal{P})$ uno _[[Definizione di Probabilita|spazio di probabiltia]]_ 
_allora_ una _variabile aleatoria_ è una funzione $$X:\Omega\rightarrow\mathbb{R}$$tale che $\forall A \subseteq \mathbb{R}$ ([[Insiemi Misurabili|misurabile]]) vale $$X^{-1}(A)=\{ \omega \in  \Omega: X(\omega) \in  A \} \in  \mathcal{F}$$
La definizione tiene conto del fatto che non sempre la $\sigma$-_algebra_ $\mathcal{F}$ degli eventi coincide con  tutto i sotto insiemi di $\Omega$  e scrivendola in questo modo ci assicuriamo di poter sempre calcolare la probabilta di eventi associati alla _variabile aleatoria_.

si usa la notazione $$
\begin{array}{}
\{ X\in  A \}=X^{-1}(A)= \{ \omega\in \Omega:X(\omega) \in  A \} \\
\mathcal{P}_{X}(A)=\mathcal{P}(X \in  A)= \mathcal{P}(X^{-1}(A))
\end{array}
$$

#### Proposizione
la funzione di insiemi $\mathcal{P}_{X}$ è una [[Probabilita sui numeri Reali|Probabilità]] su $\mathbb{R}$ detta _legge di pobabilità_ di $X$ 

_dimostrazione_ per mostrare che è una _probabiltia_  bisogna dimostrare la $\sigma$-additivita: se $(A_{n})_{n \geq 1}$ è una successione di sotto insiemi di $\mathbb{R}$ a due a due disgiunti, anche le immagini inverse sono disgiunte e si ha$$\mathcal{P}_{X}\left(\bigcup_{n=1}^{+\infty}A_{n}\right)=\mathcal{P}\left(X^{-1}\left(\bigcup_{n=1}^{+\infty}A_{n}\right)\right) = \sum^{+ \infty}_{n=1}\mathcal{P}_{X}(X^{-1}(A_{n}))=\sum^{+ \infty}_{n=1}\mathcal{P}_{X}(A_{n})$$
se due variabili aleatorie hanno la stessa _legge di probabilità_ sono dette _equidistribuite_ o isonome.


Nelle applicazioni pratiche spesso non vengono definite lo _spazzio di probabilita_ $\Omega$ e la variabile $X:\Omega \rightarrow \mathbb{R}$ ma solo la _legge di probabilita_ $\mathcal{P}_{X}$ questo avviene siccome si puo dimostrare che assegnata una probabilita $\mathcal{Q}$ a sotto insiemi di $\mathbb{R}$  è possibile costruire un sotto insieme $\Omega$ una robabilita $\mathcal{P}$ sui sotto insiemi di $\Omega$  ed una _variabile aleatoria_ $X:\Omega \rightarrow \mathbb{R}$ tale che $\mathcal{P}_{X}=\mathcal{Q}$.  infatti abbiamo che la sola _legge di probabilita_ descrive tutta l informazione in gioco se le variabili aleatoree che stiamo considerando è una sola, altrimenti bisogna definirle piu accuratamente.




#### Variabile aleatoria discreta
una _variabile aleatoria_ è detta discreta se la sua immagine $X(\Omega) \subset \mathbb{R}$ è un sotto insieme _finito_ o _numerabile_ di $\mathbb{R}$ o _equivalentemente_ se la sua _legge di probabilita_ è _discreta_

Conoscere la _legge di probabilita_ di una variabile aleatoria discreta equivale a conoscere quali sono i valori $\{ x_{1},x_{2},\dots \}$  ed i numeri $p(x_{i})=\mathcal{P}_{X}(x_{i})=\mathcal{P}(X=x_{i})$ ovvero bisogna conoscere la sua funzione di _massa_ o _densità discreta_


#### Variabile aleatoria con densita
una variabile aleatoria è detta con _densità_ (o _assolutamente continua_) se la sua _legge di probabilità_ è definita da una densita $f$, cioè se esiste una _densita di probabilita_ $f$ tale che valga $$\mathcal{P}_{X}(A)=\mathcal{P}\{ X \in  A \}= \int_{A} f(x)\, dx $$
in particolare se $A=[a,b]$ è un segmento,  per una variabile $X$ con densità $f$ vale$$ \mathcal{P}\{a \leq X \leq b)=\int ^{b}_{a}f(x) \, dx $$