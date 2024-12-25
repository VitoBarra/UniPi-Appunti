---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
tags:
  - IA
Area: "[[Concetti generali del Machine Learning]]"
topic: 
SubTopic:
---
# Linear Basis Expansion (LBE)
---
la __Linear Basis Expansion__ (LBE) è una tecnica utile per permettere ai modelli [[Modelli lineari con LMS|lineari]] di esprimere relazioni più complesse tra i dati.


### Relazioni non lineari 
notiamo che in $h_{\boldsymbol w}(\boldsymbol x)= \boldsymbol w^T\cdot \boldsymbol x$ la parte a cui si riferisce il termine _lineare_ non è ai valori di input ma ai coefficienti di regressione $\boldsymbol w$

detto cio si puo espandere il modello  con una relazione non lineare tra input e output. possiamo quindi scrivere 
$$h_{\boldsymbol w}(\boldsymbol x)=w_0+w_1x+w_2x^2+\dots+w_mx^m = \sum^m_{j=0}w_jx^j$$

### Linear basis expansion - generalizzazione
possiamo espandere questo concetto delle relazioni non lineari con qualsiasi tipo di funzione 
$$h_{\boldsymbol w}(\boldsymbol x)= \sum^K_{k=0}w_k\phi_k(\boldsymbol x)$$
dove $\phi_k: \mathbb{R}^n\rightarrow \mathbb{R}$ è una funzione per ogni indice $k$ dove $K>n$ è il numero di parametri  
esempi di  $\phi_k$
- _polinomiale_ : $\phi_k = x^2_j$ or $x_jx_i$ ro $\dots$
- _trasformazioni nonlineari_:
	- _input singolo_:  $\phi_k = log(x_j)$ or $root(x_j)$ ro $\dots$
	- _input vettoriale_ : $\phi_k = \|\boldsymbol x\|$



- _PRO_: è piu espressivo puo esprimere relazioni piu complicate
una buona flessibilità ci permette di dare una buona approssimazione della funzione che cerchiamo 
![[AC48AB1A-F82F-401F-8B56-89876D800471.jpeg]]
- _CONS_: con una larga base di funzioni abbiamo bisogno di metodi per tenere sotto controllo la _complessità_ del modello
troppa flessibilità ci puo portare al fenomeno di _[[Overfitting e Underfiting|overfitting]]_: ovvero si i dati di training abbiamo ridotto a 0. errore ma testando su dati casuali avremmo predizione sbagliate e quindi una bassa _accuracy_
- é molto suscettibile a errori poco perturbati
![[DA592E39-BE09-4F38-B38F-265D19B9C9BF.jpeg]]



Puo anche essere usate con tecniche di regolarizazione come la L2
![[F81A15DB-EA14-4C7D-A57B-E0C4601243E8.jpeg]]
