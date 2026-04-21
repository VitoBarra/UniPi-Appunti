---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
Area:
topic:
SubTopic:
---

# Variabili aleatorie Notevoli - Negative Binomial
---
La **binomiale negativa** conta con quale probabilità bisogna aspettare un certo numero di eventi prima di ottenere l'$r$-esimo successo.

Può essere vista come una generalizzazione della [[Variabili Aleatorie Notevoli - Geometrica|variabile geometrica]], infatti la [[Variabili Aleatorie Notevoli - Geometrica|geometrica]] è il caso specifico in cui $r=1$.

Consideriamo quindi una prova ripetuta [[Indipendenza Stocastica|indipendentemente]] in cui ci interessano solo _due esiti_: chiamiamo uno dei due “_successo_”, con [[Definizione di Probabilita|probabilità]] $p\in(0,1)$, e l'altro “_insuccesso_”.

#### Variabile binomiale negativa
_sia_ $X$ la _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ che conta il numero di _insuccessi_ prima di ottenere l'$r$-esimo successo
**_se_** vale$$
\mathcal{P}\{X=h\}=\binom{h+r-1}{r-1}p^{r}(1-p)^{h}
\qquad h\in\mathbb{N}
$$**_allora_** $X$ è detta **variabile binomiale negativa** di parametri $r,p$ e si scrive$$X\sim NB(r,p)$$dove
- $p^{r}(1-p)^{h}$ è la probabilità di osservare $r$ successi e $h$ insuccessi in un ordine fissato
- $\binom{h+r-1}{r-1}$ è il numero di modi di [[Combinatoria|disporre]] i primi $r-1$ successi nelle prime $h+r-1$ prove, perché l'ultima prova deve essere per forza un successo

Infatti, se ci sono $h$ insuccessi prima dell'$r$-esimo successo, allora le prime $h+r-1$ prove contengono $h$ insuccessi e $r-1$ successi, mentre la prova finale è il successo numero $r$.

#### Versione come numero di prove
A volte la stessa distribuzione viene parametrizzata contando il numero totale di prove necessarie per ottenere $r$ successi.

In questo caso poniamo
$$
T=X+r
$$
e quindi $T$ assume valori $r,r+1,\dots$
La sua legge è
$$
\mathcal{P}\{T=n\}=\binom{n-1}{r-1}p^{r}(1-p)^{n-r}
\qquad n\geq r
$$
Questa è la stessa informazione vista in modo diverso:
- $X$ conta gli _insuccessi_ prima dell'$r$-esimo successo
- $T$ conta le _prove totali_ fino all'$r$-esimo successo

#### Relazione con la geometrica
La binomiale negativa può essere vista come somma di $r$ [[Variabili Aleatorie Notevoli - Geometrica|variabili geometriche]] [[Indipendenza di Variabili aleatorie|indipendenti]].

Infatti, se $T_i$ è il numero di prove che intercorre tra il successo $(i-1)$-esimo e il successo $i$-esimo, allora$$T=T_1+\dots+T_r$$con$$T_i\sim Geom(p)$$Quindi la binomiale negativa rappresenta un _tempo di attesa_ fino a un numero fissato di successi.

#### Momenti e varianza
_sia_ $X$ una _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ binomiale negativa $NB(r,p)$ che conta gli insuccessi prima di $r$ successi

allora$$\mathbb{E}[X]=\frac{r(1-p)}{p}$$e la [[Variabili aleatorie - Varianza|varianza]] è $$Var(X)=\frac{r(1-p)}{p^{2}}$$Se invece si usa la variabile $T=X+r$, che conta il numero totale di prove, allora$$\mathbb{E}[T]=\frac{r}{p}$$mentre la varianza resta$$Var(T)=\frac{r(1-p)}{p^{2}}$$La [[Funzione generatrice di momenti (MTF)|funzione generatrice dei momenti]] della variabile $X$ è$$M_X(t)=\left(\frac{p}{1-(1-p)e^{t}}\right)^r$$definita per $t<-\log(1-p)$.

#### Parametrizzazione sulla media
Una parametrizzazione molto usata è quella in funzione della media $\mu$ e di un parametro di dispersione. infatti per una variabile **binomiale negativa** $X\sim NB(r,p)$ che conta gli insuccessi prima di $r$ successi abbiamo che il [[Variabili aleatoria - Valore atteso|valore atteso]] è $$\mathbb{E}[X]=\frac{r(1-p)}{p} = \mu$$e che quindi la [[Variabili aleatorie - Varianza|varianza]] vale$$Var(X)=\frac{r(1-p)}{p^2}$$da qui si vede che $$\mu=\frac{r(1-p)}{p} \implies p=\frac{r}{r+\mu}$$e quindi$$Var(X)=\frac{r(1-p)}{p^2}=\mu\frac{1}{p}=\mu\frac{r+\mu}{r}=\mu+\frac{\mu^2}{r}$$questo mostra che come la [[Variabili Aleatorie Notevoli - Poisson|Poisson]],  la varianza della binomiale è definita in funzione della media ma mentre nella [[Variabili Aleatorie Notevoli - Poisson|Poisson]] vale$$\mathbb{E}[X]=Var(X)=\lambda$$Nella **binomiale negativa** la varianza è più grande della media perché compare il termine aggiuntivo$$\frac{\mu^2}{r}$$Per questo la binomiale negativa è utile quando abbiamo conteggi discreti con **overdispersion**, cioè quando$$Var(X)>\mathbb{E}[X]$$Spesso si scrive anche$$Var(X)=\mu+\phi\mu^2$$dove $\phi=\cfrac{1}{r}$ è il parametro di dispersione. In questa parametrizzazione si indica quindi$$X\sim NB(\mu,\phi)$$Nel [[limiti|limite]] al infinito in cui $r$ diventa grande e $\phi$ tende a $0$, il termine quadratico tende a sparire e la binomiale negativa si comporta come una [[Variabili Aleatorie Notevoli - Poisson|Poisson]] di media $\lambda=\mu$.
