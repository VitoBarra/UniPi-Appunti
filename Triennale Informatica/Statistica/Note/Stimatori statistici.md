---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Stimatori statistici
---
#### Stimatore (Definizione)
una __stimatore__ di una parametro $\theta$ è una [[Statistica campionaria|statistica campionaria]] ovvero è una _[[Funzioni|funzione]] del campione_  $g(X_{1}\dots X_{n})$ atta a stimare $\theta$ 

>[!tip] 
>siccome uno stimatore è una funzione di [[Variabili Aleatorie (Casuali)|variaibli aleatorie]] è anche esso una _variabile aleatoria_


#### Stimatore corretto (Definizione)
_sia_ $\theta$ un parametro della [[Probabilita sui numeri Reali|distribuzione]] di una [[Campione Statistico|campione statistico]] $X_{1}\dots X_{n}$
_allora_ una statistica $g(X_{1}\dots X_{n})$ si diede _stimatore corretto_ (o _non distorto_,_ubiased_) del parametro $\theta$ se questo ha [[Variabili aleatoria - Momenti|memento primo]] $$\mathbb{E}[g(X_{1}\dots X_{n})]=\theta$$cioe la _media_ dello stimatore è il parametro $\theta$


##### Proposizione
_sia_ $X_{1},\dots,X_{n}$ un [[Campione Statistico|campione statistico]] 
_se_ $X_{1}\dots,X_{n}$ hanno _[[Variabili aleatoria - Momenti|momento secondo]]_
e _siano_
- $\mu=\mathbb{E}[X_{}]$
- $\sigma^{2} =Var(X_{i})$
- $\overline{X}=\cfrac{X_{1}+\dots+X_{n}}{n}$
_allora_ vale che$$\begin{array}{}
\mathbb{E}[\overline{X}] & = & \mu \\
Var(\overline{X}) & = & \cfrac{\sigma^{2}}{n} \\
\end{array}$$ e vale $$\begin{array}{}
\mathbb{E}[S_{n}^{2}] & = & \mathbb{E}\left[ \cfrac{\sum^{n}_{i=1}(X_{i}-\overline{X})^{2}}{n-1} \right]  & = & \sigma^{2}
\end{array}
$$e questo ci dice che 
- [[Idd - varianza campionaria|varianza campionaria]] è uno _stimatore corretto_ della _varianza_
- la [[Idd - Media Campionaria|media campionaria]] è uno _stimatore corretto_ della _media empirica_


_Dimostrazione_:
	le prime due sono immediate dal ipotesi di _linearita_ del [[Variabili aleatoria - Momenti|valore atteso]] e dal ipotesi di _[[Indipendenza di Variabili aleatorie|indipendenza]]_ 
	per la terza e uguaglia invece vale che $$\sum^{n}_{i=1}(X_{i}-\overline{X})^{2}=\sum^{n}_{i=1}X^{2}_{i}-n\overline{X^{2}}$$e $\forall  i$$$\begin{array}{}
	\mathbb{E}[X_{i}^{2}] & =  & \mathbb{E}[X_{i}^{2}]-\mathbb{E}[X_{i}]^{2}+ \mathbb{E}[X_{i}]^{2}\\
  &  = & Var(X_{i})+\mathbb{E}[X_{i}]^{2}  \\
& = & \sigma^{2}+\mu^{2}
    \end{array}
	$$e quindi vale che $$
	\begin{array}{}
	\displaystyle\mathbb{E}\left[ \sum^{n}_{i=1}(X_{i}-\overline{X})^{2} \right] & = \\
    \sum^{n}_{i=1}\mathbb{E}[X_{i}^{2}]-n\mathbb{E}[\overline{X}^{2}] & = \\
    n(\sigma^{2}+\mu^{2})-n\left( \cfrac{\sigma^{2}}{n}+\mu^{2} \right) & = \\
    (n-1)\sigma^{2}
\end{array}
	$$da cui dividendo per $(n-1)$ si ottiene la tesi.


#### Stimatore consistente (Definizione)
_Sia_ $\theta$ un parametro della distribuzione $X_{1}\dots X_{n},\dots$ di infinita [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite (IDD)|idd]] di $X$ 
_allora_ la successione di statistiche $g_{n}(X_{1}\dots,X_{n})$ si dice uno _stimatore consistente_ di $\theta$ 
_se_ per $n \to \infty$ , $g_{n}(X_{1},\dots,X_{n}) \to \theta$ in [[Convergenza in probabilita|probabilita]] cioe se, $\forall \varepsilon>0$    $$\lim_{ n \to \infty }\mathcal{P}\{ |g_{n}(X_{1},\dots,X_{n})-\theta| > \varepsilon \} =0$$

ovvero al aumentare della taglia $n$ del [[Campione Statistico|campione]] la probabilità che lo stimatore si avvicini al parametro.



#### Efficenza stimatori
_Sia_ 
- $\theta$ un parametro della distribuzione e un [[Campione Statistico|campione statistico]]
-  $X_{1}\dots X_{n_{0}}$ una [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite (IDD)|famiglia idd]] di $X$ 
-  $n_{0}>n,m$  numeri
-  $g(X_{1},\dots,X_{n})$ e $h(X_{1},\dots,X_{m})$ due _stimatori corretti_ 
 _se_ $g(X_{1},\dots,X_{n})$ e $h(X_{1},\dots,X_{m})$ ammettono [[Variabili aleatoria - Momenti|momento secondo]] 
_allora_ diciamo che $g(X_{1},\dots,X_{n})$ è più efficiente di $h(X_{1},\dots X_{m})$ se $$Var(g(X_{1},\dots,X_{n}))\leq Var(h(X_{1},\dots,X_{m}))$$
ovvero la _dispersione_ attorno al valore $\theta$ è più bassa con $g$ rispetto a $h$


> [!tip]
> da un [[Campione Statistico|campione]] con [[Variabili aleatoria - Momenti|momento secondo]] finito, allora la media campionaria è sempre piu efficente al crescere di $n$: infatti $Var(\overline{X}_{n})=\frac{Var(X_{1})}{n}\xrightarrow{n \to \infty}0$ 



