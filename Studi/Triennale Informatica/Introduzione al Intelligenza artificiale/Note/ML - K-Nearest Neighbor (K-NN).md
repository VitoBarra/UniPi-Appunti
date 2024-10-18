---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# K-Nearest Neighbor (K-NN)
---
un algoritmo _supervisionato_ di [[Machine Learning|ML]] 

un algoritmo molto semplice che non fornisce un modello ma direttamente una classificazione o curva di regressione

## Classificazione binaria
### Algoritmo 
1. mantenere i training data come $<\boldsymbol x_p, y_p> \ \ P=1,\dots,l$
2. dato in un input $\boldsymbol x$ di dimension $n$
	1. trova il _dato di training_ piu vicino  
	2. per trovare il dato piu vicino si definisce una distanza una distanza $d(\boldsymbol x,\boldsymbol x_i)$
	3. e si cerca  $i(x)= \arg_p \min d(\boldsymbol x,\boldsymbol x_p)$ ovvero si cerca l indice $i$ dove la distanza è minima
		1. $d=\sqrt{\sum^n_{t=1}(x_t-x_{p,t})^2}=\|\boldsymbol x -\boldsymbol x_p\|$
		2. devo $\boldsymbol x_{p,t}$ è il componente $t$ del pattern $p$
3. output $y_i$

_ovvero_: cerca il dato di training più vicino  al dato che si vuole classificare e lo classifica uguale a questo

il numero di nodi a cui deve essere vicino è un parametro del algoritmo $K$ quindi 
1-nn siginifica che si cosidera il nodo più vicino 5-nn i primi 5 nodi più vicini
![[CA1D12E4-FCD5-4707-BA60-168BA72B5893.jpeg]]
con $K$ basso la classificazione appare  molto nervosa poco _Smooth_  e questo puo essere un indice di _overfitting_ . per fare _smoothing_ $K$ puo essere aumentato 

con $K>1$ si prendere la _media_ dei valori dei $K$ punti piu vicini
$$avr_k(\boldsymbol x)= \frac{1}{k}\sum_{x_i\in N_k(\boldsymbol x)} y_i$$
dove  $N_k(\boldsymbol x)$ soni i $k$ punti  piu vicini in accodo allo distanza $d$ 
la classificazione funziona con la maggioranza, ovvero se ci sono piu punti che che sono classificati in un certo modo allora il dat $\boldsymbol x$ verra classificato in quel modo 
$$
\begin{cases}
1 & if & avg_k(\boldsymbol x)>0.5 \\
0 & & otherwise
\end{cases}$$
>[!tip]- puo essere usato anche per la regressione
>in questo caso si usa direttamente la media

![[6978EBCC-2081-4D85-B788-3F2D329BC584.jpeg]]

#### proprietà
- $K = 1$ estremamente flessibile _overfitting_
- $K=l$ estremamente rigido _underfitting_

## Classificazione multi-classe
ritorna la classe più comunate tara i suoi $K$ Vicini
$$h(\boldsymbol x)= \arg_v \max \sum_{\boldsymbol x\in N_k(\boldsymbol x)}\boldsymbol 1_{v,y_i}$$
$$\boldsymbol 1_{v,y_i}=
\begin{cases}
1 & if & v=y_i \\
0 & &otherwise 
\end{cases}
$$

## Proprieta generali
- _NON_ un ipotesi globale dobbiamo $\rightarrow$ non c è un modello
	-  memorizzare ogni input d esempio
	-  non parametro in $\boldsymbol w$
- Stima locale 
- è un _metodo basta sulla distanza_

## Limiti 
- il costo computazionale è _ritardato_ alla fase di predizione il che è uno _svantaggio_ siccome questo puo essere molto alto a seconda dai dati presenti 
	- per ogni nuovo dato da predire  va calcolata la distanza con _TUTTI_ i punti mantenuti nel modello
		- tempo proporzionale al numero di dati
		- ottimizzabile come algoritmi di prossimità ”_ad-hoc_”
	- alto costo in spazio. ogni dato va mantenuto in memoria
- quando la _dimensione del input_ cresce spesso l algoritmo è prono ad errori 
	- questo è dato dalla _curse of dimensionality_
	- quando la dimensione del input cresce il volume ($side^n$) dello spazio aumenta e cosi i dati si trovano sempre piu sparsi. la crescita è _esponenziale_
- _feature in rilevanti: the curse of noisy_
	- in casi di dati che dipendono da poche feature ma ne hanno molte di piu si puoi sbagliare la classificazione considerando quelle in rilevanti che possono dominare su quelle rilevanti


## Bias-induttivo
tutto l algoritmo si basa sul concetto di distanza. la metrica che si utilizza è il _[[ML - Bias Induttivo|Bias]]_ che utilizziamo per la generalizzazione
- questo dipende prettamente dal campo, campi di versi potrebbero avere $d$ definita diversamente
è _possibile imparare_ la metrica  
 
  