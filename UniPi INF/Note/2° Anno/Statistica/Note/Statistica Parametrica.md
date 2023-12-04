---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Statistica Parametrica
---
#### Stime parametriche
Avendo un [[Campione Statistico|campione statistico]] $X_{1}\dots X_{n}$ se non si hanno informazioni in piu non si puo arrivare a nessuna conclusione, al meno di usare la [[Statistica non parametrica|statistica non parametrica]].
Esistono pero i casi in cui la  [[Probabilita sui numeri Reali|legge di probabilita]] $\mathcal{P}_{X}$ è _parzialmente specificata_ ovvero si conosce a quale _famiglia di leggi_ ( ovvero di che tipo di _variabile aleatoria notevole_ è) la _legge di probabilita_ appartiene ma questa è _dipendente_ da un _parametro_ incognito. 
Il parametro in generale è indicati con $\theta$ o con  $\theta_{1} \dots \theta_{n}$ se i parametri sono multipli.


l _obbiettivo_  della _stima parametrica_ è stimare il _parametro incognito_  $\theta$ o dai _parametri incogniti_ $\theta_{1} \dots \theta_{n}$ a partire dalle osservazioni fatte sul _campione statistico_ 

##### Statistica campionaria (definizione)
una funzione $g(X_{1}\dots X_{n})$ è detta _statistica campionaria_ un scempio di questo sono la [[Idd - Media Campionaria|Media campionaria]] e la [[Idd - varianza campionaria|varianza campionaria]]

#### Stimatore
una _stimatore_ di una parametro $\theta$ è una [[#Statistica campionaria (definizione)|statistica]] ovvero è una _funzione del campione_  $g(X_{1}\dots X_{n})$ atta a stimare $\theta$ 

>[!tip] 
>siccome uno stimatore è una funzione di [[Variabili Aleatorie (Casuali)|variaibli aleatorie]] è anche esso una _variabile aleatoria_


##### Stimatore corretto (Definizione)
_sia_ $\theta$ un parametro della [[Probabilita sui numeri Reali|distribuzione]] di una [[Campione Statistico|campione statistico]] $X_{1}\dots X_{n}$
_allora_ una statistica $g(X_{1}\dots X_{n})$ si diede _stimatore corretto_ (o _non distorto_,_ubiased_) del parametro $\theta$ se questo ha [[Variabili aleatorie multivariate - Momenti|memento primo]] $$\mathbb{E}[g(X_{1}\dots X_{n})]=\theta$$cioe la media dello stimatore è il parametro $\theta$




#### Proposizione
_sia_ $X_{1},\dots,X_{n}$ un [[Campione Statistico|campione statistico]] 
_se_ $X_{1}\dots,X_{n}$ hanno [[Variabili aleatoria - Momenti|momento]] _secondo_
e _siano_
- $\mu=\mathbb{E}[X_{}]$
- $\sigma^{2} =Var(X_{i})$
- $\overline{X}=\cfrac{X_{1}+\dots+X_{n}}{n}$
_allora_ vale che$$\begin{array}{}
\mathbb{E}[\overline{X}] & = & \mu \\
Var(\overline{X}) & = & \cfrac{\sigma^{2}}{n} \\
\mathbb{E}\left[ \cfrac{\sum^{n}_{i=1}(X_{i}-\overline{X})^{2}}{n-1} \right]  & = & \sigma^{2}
\end{array}$$
e questo ci dice che 
- [[Idd - varianza campionaria|varianza campionaria]] è uno _stimatore corretto_ della _varianza_
- la [[Idd - Media Campionaria|media campionaria]] è uno _stimatore corretto_ della _media empirica_


_Dimostrazione_:
	le prime due sono immediate dal ipotesi di _linearita_ del valore atteso e dal ipotesi di _[[Indipendenza di Variabili aleatorie|indipendenza]]_ 
	per la terza e uguaglia invece vale che $$\sum^{n}_{i=1}(X_{i}-\overline{X})^{2}=\sum^{n}_{i=1}X^{2}_{i}-n\overline{X^{2}}$$
	e $$\forall  i \ \mathbb{E}[X_{i}^{2}]=Var(X_{i})+\mathbb{E}[X_{i}]^{2}=\sigma^{2}+\mu^{2}$$e quindi vale che $$
	\begin{array}{}
	\displaystyle\mathbb{E}\left[ \sum^{n}_{i=1}(X-\overline{X})^{2} \right] & = \\
    \sum^{n}_{i=1}\mathbb{E}[X_{i}^{2}]-n\mathbb{E}[\overline{X}^{2}] & = \\
    n(\sigma^{2}+\mu^{2})-n\left( \cfrac{\sigma^{2}}{n}+\mu^{2} \right) & = \\
    (n-1)\sigma^{2}
\end{array}
	$$da cui dividendo per $(n-1)$ si ottiene la tesi.


#### Stimatore consistente (Definizione)
_Sia_ $\theta$ un parametro della distribuzione $X_{1}\dots X_{n},\dots$ di infinita [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite|idd]] di $X$ 
_allora_ la successione di statistiche $g_{n}(X_{1}\dots,X_{n})$ si dice uno _stimatore consistente_ di $\theta$ 
_se_ per $n \to \infty$ , $g_{n}(X_{1},\dots,X_{n}) \to \theta$ in [[Convergenza in probabilita|probabilita]] cioe se, $\forall \varepsilon>0$    $$\lim_{ n \to \infty }\mathcal{P}\{ |g_{n}(X_{1},\dots,X_{n})-\theta| > \varepsilon \} =0$$

ovvero al aumentare della taglia $n$ del campione la probabilità che lo stimatore si avvicini al parametro.



#### Efficenza stimatori
_Sia_ $\theta$ un parametro della distribuzione e un [[Campione Statistico|campione statistico]] $X_{1}\dots X_{n_{0}}$ di [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite|idd]] di $X$ con $n_{0}>n,m$ e siano $g(X_{1},\dots,X_{n})$ e $h(X_{1},\dots,X_{m})$ due _stimatori corretti_ che ammettono [[Variabili aleatoria - Momenti|momento secondo]] 
_allora_ diciamo che $g(X_{1},\dots,X_{n})$ è piu efficente di $h(X_{1},\dots X_{m})$ se $$Var(g(X_{1},\dots,X_{n}))\leq Var(h(X_{1},\dots,X_{m}))$$
ovvero la dispersione attorno al valore $\theta$ è piu bassa con $g$ rispetto a $h$


> [!tip]
> da un [[Campione Statistico|campione]] conb [[Variabili aleatoria - Momenti|momento secondo]] finito, allora la media campionaria è sempre piu efficente al crescere di $n$: infatti $Var(\overline{X}_{n})=\frac{Var(X_{1})}{n}\xrightarrow{n \to \infty}0$ 



