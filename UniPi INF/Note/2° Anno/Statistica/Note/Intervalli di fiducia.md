---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Intervalli di fiducia
---
Gli _intervalli di fiducia_ sono spesso considerati come sotto insieme dei [[Test Statistici|test statistici]], questo perche ci sono alcuni test statistici che sono dimostrabilmente equivalenti agli intervalli di fiducia


Considerando un [[Campione Statistico]]  la cui legge dipende da un parametro $\theta$ incognito. il _[[Campione Statistico|campione]]_ essendo una [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite|idd]] abbiamo che questo hanno  la stessa [[Probabilita sui numeri Reali|legge di probabilita]] e quindi la stessa [[Funzione di Ripartizione|funione di ripartizione]] ovvero $$\mathcal{P}_{\theta}(X_{1}\leq t)= \dots=\mathcal{P}_{\theta}(X_{n}\leq t)= F_{\theta}(t), \ \ \ \ \ t \in  \mathbb{R}$$ovvero esiste una famiglia di probabilita $\{ \mathcal{P}_{\theta} \}_{\theta \in \Theta}$ tale che fissato $\theta$ le variabili aleatorie siano una [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite|idd]] 
è l obbiettivo della _analisi statistica_ e queslla di determinare il parametro $\theta$ nel modo piu preciso possibile.


#### Intervallo aleatorio o casuale (Definizione)
_sia_ $X_{1},\dots,X_{n}$ un [[Campione Statistico|campione statistico]] di legge $\mathcal{P}_{\theta}$con $\theta \in \Theta \subseteq \mathbb{R}$ si dice  _intervallo aleotorio_ $$I=[a( X_{1},\dots,X_{n}),b(X_{1},\dots,X_{n})]$$ dove $a,b: \mathbb{R}^{n} \rightarrow \mathbb{R}$ sono [[Funzioni|funzioni]] su insiemi [[Insiemi Misurabili|misurabili]] e ed essendo funzioni di [[Variabili Aleatorie (Casuali)|Variabili Aleatorie]] anche $a( X_{1},\dots,X_{n}),b(X_{1},\dots,X_{n})$ sono _variabili aleatorie_

#### Intervallo di fiducia
_sia_  $X_{1},\dots,X_{n}$ un [[Campione Statistico|campione statistico]] di legge $\mathcal{P}_{\theta}$con $\theta \in \Theta \subseteq \mathbb{R}$ e $\alpha \in (0,1)$ un numero e $I$ un _intervallo aleatorio_ 
_allora_ si dice $I$ è un _intervallo di fiducia_ per $\theta$ al livello $(1-\alpha)$
_se_ $\forall  \theta \in  \Theta$  è vero che$$
\begin{array}{}
\mathcal{P}_{\theta}(\theta \in  I) & = \\
 \mathcal{P}_{\theta}(a(X_{1},\dots,X_{n}) \leq \theta,b(X_{1},\dots,X_{n})\geq \theta)  & \geq \\
 1- \alpha
\end{array}
$$
la _scelta_ del parametro $\alpha$ è importante e soggetto a compromesso, Solitamente si scelgono valori piccolo come $0,05$ o $0,02$.
il _compromesso_ è tra la larghezza del intervallo che vorremmo piccolo, siccome più è piccolo piu ci indica con precisione dove è il valore di $\theta$ e il _livello di fiducia_ ($1-\alpha$) che vorremmo alto, siccome qusto ci indica quanto è probabilita che il valore $\theta$ sia effettivamente in quel intervallo.
al aumentare di $\alpha$ l _intervallo di fiducia_ si restringe ma allo stesso modo diminuisce anche il _livello di fiducia_ $(1-\alpha)$ 



