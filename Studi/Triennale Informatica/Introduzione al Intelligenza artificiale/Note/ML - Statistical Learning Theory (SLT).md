---
Subject: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Statistical Learning Theory (SLT)
---
### Numero dei dati di input
Aumentando la __complessità__ del modello sono richiesti più dati per evitare l __[[ML - Overfitting e Underfitting|overfitting]]__. infatti l _overfitting_ è un fenomeno che dipende dalla complessità e dal numero dei dati. al aumentare dei dati il modello può essere anche più complesso senza andare in over fitting 

>[!example]- polinomio di grado 9
> ![[AD987627-2D22-47F8-B3ED-7EC8512A4295.jpeg]]
>![[11752980-DCE7-4DC2-8E9B-1C39288F32A0.jpeg]]



### Statitistical learning Theory
è una teoria matematica che unifica i concetti di [[Machine Learning|machine Learning]] 
1. Capacita di generalizare
	1. misurata come _rischio_ è _errore sul test_
	2. considerando le problematiche di [[ML - Overfitting e Underfitting|overfitting e underfitting]]
2.  il ruolo della complessità del modello 
3. il ruolo della quantità di dati


### setting Formale
- si cerca di stimare la [[Funzioni|funzione]] sconosciuta  $f(\boldsymbol x)=d$ 
- Si vuole minimizzare la funzione di rischio $R=\int L(d,h(\boldsymbol x))dP(\boldsymbol x,d))$ (il _vero errore su tutti i dati_ )
- dato
	- il valore dal theatcher ($d$) e la [[Distribuzione di probabilita|Distribuzione di probabilita]] $P(\boldsymbol x,d)$
	- una funzione di $Loss$ 
- si cerca una ipotesi $h \in H$ tale che $\min R$
	- dove $H$ è lo spazio delle possibili ipotesi 
- avendo pero solo una set finiti di dati $TR$ possiamo solo minimizzare il _rischio empirico_ $R_{emp}$ (gli errori sul $TR$) 

Possiamo utilizzare $R_{emp}$ per  approssimare $R$ ?

## Definizioni
- _VC-dimensio_: la _dimensione di Vapnik-Chervonenkis_ è una misura di complessità di $H$ 
- _VC-bounds_: garantisce con in una certa probabilità $1-\delta$ 
	- $$R \leq R_{emp}+\epsilon\left (\frac{1}{l},VC,\frac{1}{\delta}\right)$$
	- Dove 
		- $\epsilon$ è una funzione  detta _VC-confidece_ che cresce con il crescere di $VC$ e decresce al crescere di $l$ (numero di dati) e $\delta$ 
		-  $R_{emp}$ decresce con modelli complessi
		- $\delta$ è la [[Intervalli di fiducia|confidenza]] con cui si decide che la maggiorazione regga
- Intuizioni:
-  $l$ (data) più alto. $\rightarrow$ VC-confidence più bassa minorazione più vicina a $R$
- modello troppo semplice (VC-dim bassa) $\rightarrow$ $R_{emp}$ troppo alto (_undefitting_) 
- alto (VC-Dimension) $\rightarrow$ basso $R_{emp}$ ma $VC-conf$ si alza il che può portare ad $R$ alto. (_overfitting_)
- ![[2459D540-ACAE-42F0-BDFA-18BEEBFB6B4F.jpeg]]
- si utilizza quindi questa formula per trovare il giusto trade off tra l accuracy sul $TR$ e tra la complessità del modello $VC-dim$
 

>[!note]
>nonostante i [[ML - Modelli lineari (LMS)|modelli lineare]] e [[ML - Alberi di decisione|alberi di decisione]] siano stati formalizzati prima della SLT vedere come questi applicano entrambi i principi di questa teoria. che infatti è l astratto di quello che viene detto in questi modelli


> [!note]
> questo modello da i fondamenti giusti per il ML che è quindi ben fondato teoricamente






 