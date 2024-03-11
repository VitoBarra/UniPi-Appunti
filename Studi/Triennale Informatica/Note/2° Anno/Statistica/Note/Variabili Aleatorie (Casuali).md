---
Subject: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Variabili Aleatorie (Casuali)
---
in [[Statistica (STAT)|statistica]] le _variabili aleatorie_ sono uno strumento matematico che ci permettono di dare un formalismo matematico piu agile rispetto al solo _[[Definizione di Probabilita|Spazzio di probabilita]]_ $(\Omega,\mathcal{F},\mathcal{P})$ che è associato ad un esperimento che vogliamo studiare.
Infatti spesso non ci c’interessa l esito specifico del esperimento ma la _variabilità_ tra gli esiti dello stesso esperimento.

le _variabili aleatorie_ ci permettono di studiare la _variabilità_ di tra gli esiti dello stesso esperimento, ovvero sullo stesso _spazio di probabilità_,  ripetuto piu volte e sono formalizzate con [[Funzioni|Funzioni]] di $\Omega$

### Variabili aleatore (Definizione)
_sia_ $(\Omega,\mathcal{F},\mathcal{P})$ uno _[[Definizione di Probabilita|spazio di probabiltia]]_ 
_allora_ una __variabile aleatoria__ è una funzione $$X:\Omega\rightarrow\mathbb{R}$$tale che $\forall A \subseteq \mathbb{R}$ ([[Insiemi Misurabili|misurabile]]) vale $$X^{-1}(A)=\{ \omega \in  \Omega: X(\omega) \in  A \} \in  \mathcal{F}$$
La definizione tiene conto del fatto che non sempre la $\sigma$-_algebra_ $\mathcal{F}$ degli eventi coincide con  tutto i sotto insiemi di $\Omega$  e scrivendola in questo modo ci assicuriamo di poter sempre calcolare la probabilità di eventi associati alla _variabile aleatoria_.

si usa la notazione $$
\begin{array}{}
\{ X\in  A \}=X^{-1}(A)= \{ \omega\in \Omega:X(\omega) \in  A \} \\
\mathcal{P}_{X}(A)=\mathcal{P}(X \in  A)= \mathcal{P}(X^{-1}(A))
\end{array}
$$ e $\mathcal{P}_X$ è detta [[Legge di Probabilita|Legge di Probabilita]] di $x$



 

#### Variabile aleatoria discreta
una _variabile aleatoria_ è detta discreta se la sua immagine $X(\Omega) \subset \mathbb{R}$ è un sotto insieme _finito_ o _numerabile_ di $\mathbb{R}$ o _equivalentemente_ se la sua _legge di probabilita_ è _discreta_

Conoscere la _[[Legge di Probabilita|legge di probabilita]]_ di una variabile aleatoria discreta equivale a conoscere quali sono i valori $\{ x_{1},x_{2},\dots \}$  ed i numeri $p(x_{i})=\mathcal{P}_{X}(x_{i})=\mathcal{P}(X=x_{i})$ ovvero bisogna conoscere la sua funzione di _massa_ o _densità discreta_


#### Variabile aleatoria con densita
una variabile aleatoria è detta con _densità_ (o _assolutamente continua_) se la sua _[[Legge di Probabilita|legge di probabilità]]_ è definita da una densità $f$, cioè se esiste una __densità di probabilità__ $f$ tale che valga $$\mathcal{P}_{X}(A)=\mathcal{P}\{ X \in  A \}= \int_{A} f(x)\, dx $$
in particolare se $A=[a,b]$ è un segmento,  per una variabile $X$ con densità $f$ vale$$ \mathcal{P}\{a \leq X \leq b)=\int ^{b}_{a}f(x) \, dx $$