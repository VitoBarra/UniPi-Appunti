---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili Aleatorie Notevoli - Binomiale
---
Consideriamo il caso in cui vogliamo trovate la _[[Probabilita sui numeri Reali|legge di probabilità]]_  della situazione in cui ci interessano solo _due esiti_ di una prova ripetuta $n$ volte _con rimpiazzo_
chiamiamo solo una due due esiti “_successo_”  e questa ha [[Definizione di Probabilita|probabilita]] $p\in (0,1)$

>[!tip]
>lo stesso caso _senza rimpiazzo_ è modellizzato dalla variaible [[Variabili Aleatorie Notevoli - Ipergeometrica|ipergiometrica]]
#### Variabile Binoiale
_sia_ $X:\Omega \rightarrow\{ 1,\dots,n\}$ la _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ che _conta_ il numero di _successi_ 
_se_ vale che $$\mathcal{P}(X=h)=\begin{pmatrix}n \\ h\end{pmatrix} p^{h}(1-p)^{n-h} \ \ \ \ , 0 \leq h\leq n$$
_allora_ è detta _variabilie binomiale_ di parametri $n,p$ indicata con $B(n,p)$ 
dove 
- $p^{h}(1-p)^{n-h}$ è la probabilità che compaia un risultato con $h$ _successi_ e $(n-h)$ _insuccessi_. e questo vale per l _[[Indipendenza Stocastica|indipendenza]]_ dei risultati
- $\begin{pmatrix}n \\h \end{pmatrix}$ è il numero di modi di [[Combinatoria#Disposizioni|disporre]] gli $h$ _successi_ e $(n-h)$ _insuccessi_

la [[Definizione di Probabilita|probabilità]] totale è $1$ come conseguenza dell _binomiale_.


> [!tip] Variabile di bernulli 
>con $n=1$ diventa la _[[Variabili Aleatorie Notevoli - Bernulli|variabile di bernulli]]_ 
