---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Stima Parametrica - Metodo di Massima Verosomiglianza
---


#### Metodo di massima verosomiglianza

##### Funzione di massima verosomiglianza (Definizione)
_sia_ $X_{1},\dots,X_{n}$ un [[Campione Statistico|campio statistico]] 
si chiama _funzione di massima verosimiglianza_ la [[Funzioni|funzione]] $L(\theta;\dots)$  definita come
	_caso discreto_: $$L(\theta;x_{1},\dots,x_{n})=\prod^{n}_{i=1}p_{\theta}(x_{i})$$_caso continuo_:$$L(\theta;x_{1},\dots,x_{n})=\prod^{n}_{i=1}f_{\theta}(x_{i})$$
##### Stima di massima verosomiglianza (Definizione)
_sia_ $X_{1},\dots,\dots$[[Campione Statistico|campione statistico]] la cui [[Probabilita sui numeri Reali|legge di probabilita]] dipende da un _parametro_ $\theta \in \Theta$ nel 
_allora_ si chiama _stima di massima verosomiglianza_ _se_ esiste una [[Statistica Parametrica#Statistica campionaria (definizione)|statistica campionaria]] $\hat{\theta}=\widehat{\theta}(x_{1,\dots}x_{n})$ tale che $$L(\theta;x_{1},\dots x_{n})=\max_{\theta \in  \Theta}(\theta,x_{1},\dots,x_{n}) \ \ \ \forall  (x_{1},\dots,x_{n}) $$
Nel caso _discreto_ se $x_{1},\dots,x_{n}$  sono gli esiti  del campione questo metodo sceglie il parametro che massimizza la probabilità degli esiti.
Nel caso _continuo_ l idea è la stessa ma la probabilita i congiunta $\not =$ alla probabilita di $x_{1},\dots,x_{n}$


#### Criterio per trovare il massimo
per trovare il [[Massimi e minimi|massimo]] della la [[Funzioni|funzione]] di _Massimaverosomigliaza_ bisogna controllare dove si annulla la [[Derivate|derivata]] per $\theta$ e quindi bisogna trovare quando $$L’_{\theta}(\theta,x_{1},\dots,x_{n})=0$$ma per fare ciò per semplificare i conti conviene calcolare la _derivata_ del [[Funzione logaritmica|logaritmo]] della funzione di _massima verosomiglianza_, fare ciò non cambia il la posizione del massimo perchè il _logaritmo_ è una funzione [[Crescenza e Decrescenza di una funzione#Funzioni monotona crescente (Definizione)|monotona crescente]]  e  quindi 
_sia_ $\Theta$ lo spazio dei valori possibili 
_se_  $L(\theta)>0 \ \ \ \ \forall \theta \in \Theta$ e $L(\theta)$ _derivable_ in tutto $\Theta$
_allora_$$L’(\theta)=0 \iff \frac{d}{d\theta}\log L(\theta)=0$$ infatti vale che la [[Derivate fondamentali|derivata  del logaritmo]] è $$\frac{d}{d\theta}\log L(\theta)=\frac{L’(\theta)}{L(\theta)}$$che si _annulla_ solo quando $L’(\theta)$ si _annulla_
 
 

