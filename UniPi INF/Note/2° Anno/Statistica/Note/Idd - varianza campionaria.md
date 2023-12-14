---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Idd - varianza campionaria
---
#### Varianza campionaria (Definizione)
_sia_ $X_{1},\dots X_{n}$ una [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite|i.d.d]] 
_se_ $X_{1}\dots ,X_{n}$ è un [[Campione Statistico|campione]] 
_allora_ $$S_{n}^{2}:= \frac{\sum^{n}_{i=1}(X_{i} - \overline{X}_{n})^{2}}{n-1}$$ $S_{n}^{2}$ rapresenta la _varianza campionaria_, e il comportamento di questa variabile determinato dal [[Teorema debole dei grandi numeri|teorema dei grandi numeri]]


##### Convergena della varianza
_sia_ $X_{1},\dots X_{n},\dots$ una _successione_ [[Famiglia di variabili aleatorie Indipendenti e identicamente distribuite|i.d.d]] 
_se_ $X_{i}$ ha [[Variabili aleatoria - Momenti|momento quarto]] 
_sia_ $\sigma^{2} = Var(X_{i})$ la [[Variabili aleatorie - Varianza|varianza]]
_allora_ la _varianza campionaria_ $S_n$ per $n \to \infty$ [[Convergenza in probabilita|converge in probabilita]] a $\sigma$ ovvero $\forall \varepsilon> 0$ vale $$\lim_{ n \to \infty }\mathcal{P}\left(\left|S_{n}^{2}-\sigma^{2}\right|>\varepsilon\right)=0 $$

_Dimostrazione_ 
	 Premettiamo questo fatto (senza dimostrazione), 
	_se_ $(Y_n)_n$ tende a $Y$ in probabilità e $(Z_n)_n$ tende a $Z$ in probabilità
	_allora_ 
		- $(Y_nZ_n)_n$ tende in probabilità a $YZ$
		- $(Y_n +Z_n)_n$ tende in probabilità a   $Y +Z$. 
	da qui procediamo sviluppando i quadrati nella definizione di $S^2_n$, si vede che $$S_n^2=\frac{n}{n-1}\left( \frac{1}{n}\sum^{n}_{i=1}X_{i}^{2}-\overline{X}_n^2 \right)$$ per $\cfrac{n}{(n-1)} \xrightarrow{n \to \infty} 1$ e poiché $X_{i}$ hanno _momento quarto_ vale che $X^2_i$ ha _momento secondo_
	e per la [[Teorema debole dei grandi numeri|legge dei grandi numeri]]  vale $$\frac{1}{n} \sum^n_{i=1}X_{i}^{2} \to \mathbb{E}[X_1^{2}]$$ dove la [[Convergenza in probabilita|convergenza è in probabilità]] 
	vale che $$\overline{X}_{n}\to \mathbb{E}[X_{1}]$$ e quindi vale la [[Convergenza in probabilita|convergenza in probabilita]]  $$S^2_n\to \mathbb{E}[X^2_1]- \mathbb{E}[X_1]^2=\sigma^{2}$$