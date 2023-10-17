---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Stima Campionaria
---
metodologie per scegliere un [[Statistica Parametrica#Stimatore| buon stimatore]].

_sia_ un [[Campione Statistico|campione statistico]] la cui [[Probabilita sui numeri Reali|legge di probabilita]] dipende da un _parametro_ $\theta \in \Theta$ nel quale le [[Variabili Aleatorie (Casuali)|variabili aleatorie]] possono essere discrete  con funzione di _massa_ $p_{\theta}(x_{})$ o con _denstia_ $f_{\theta}(x)$  
### Metodo di massima verosomiglianza
#### Funzione di massima verosomiglianza (Definizione)
si chiama _funzione di massima verosimiglianza_ la [[Funzioni|funzione]] $L(\theta;\dots)$  definita come
	_caso discreto_: $$L(\theta;x_{1},\dots,x_{n})=\prod^{n}_{i=1}p_{\theta}(x_{i})$$_caso continuo_:$$L(\theta;x_{1},\dots,x_{n})=\prod^{n}_{i=1}f_{\theta}(x_{i})$$
#### Stima di massima verosomiglianza (definizione)
si chiama _stima di massima verosomiglianza_ se esiste una [[Statistica Parametrica#Statistica campionaria (definizione)|statistica campionaria]] $\hat{\theta}=\widehat{\theta}(x_{1,\dots}x_{n})$ tale che $$L(\theta;x_{1},\dots x_{n})=\max_{\theta \in  \Theta}(\theta,x_{1},\dots,x_{n}) \ \ \ \forall  (x_{1},\dots,x_{n}) $$ 

Nel caso _discereto_ se $x_{1},\dots,x_{n}$  sono gli esiti  del campione questo metodo sceglie il parametro che massimizza la probabilita  degli esiti.
Nel caso _continuo_ l idea è la stessa ma la probabilita i congiunta $\not =$ allora probabilita di $x_{1},\dots,x_{n}$


### Metodo dei momenti
nel metodo dei momento si confronta i [[Variabili aleatoria - Momenti|mementi teorici]] in questo caso il valore atteso  $$m_{k}(\theta)=\mathbb{E}[X^{k}]$$con i _momenti empirici_ (la media campionaria)$$\sum^{n}_{i=1}\frac{x_{i}^{k}}{n}$$ la media campionaria è un [[Statistica Parametrica#Stimatore corretto (Definizione)|buon stimatore]]  del _valore atteso_ e quindi si puo scegliere  uno stimatore di $\theta$ un $\tilde{\theta}$ che realizzi l e uguaglianza tra momenti teorici e momenti empirici

#### Stima con il metodo dei momenti (Definizione)
si chiama _stima col metodo dei momenti_ se esiste una [[Statistica Parametrica#Statistica campionaria (definizione)|statistica campionaria]] $\tilde{\theta}=\tilde{\theta}(X_{1},\dots ,X_{n})$ che permetta di euguagliere alcuni _momenti teorici_ con alcuni _momenti empirici_ ovvero vale per 1 o piu $k$ positivi $$\mathbb{E}\left[X^{k}\right]=\frac{1}{n}\sum^{n}_{i=1}x^{k}_{i} \ \ \ \ \ \forall  (x_{1},\dots, x_{n})$$



>[!tip]
>questi due metodi si generalizzano bene al caso i parametri sono piu di uno e bisogna trovate $\theta=(\theta_{1},\dots,\theta_{n})$


	