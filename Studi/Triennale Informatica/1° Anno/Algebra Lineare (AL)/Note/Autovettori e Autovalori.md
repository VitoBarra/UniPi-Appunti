---
Subject: Algebra Lineare
topic: nota
tags: AL
---

Prev: [[Algebra Lineare (AL)]]

# Autovettori e Autovalori
---
sua di uno [[Spazio Vettoriale|spazio vettoriale]] $V$ su $\mathbb{K}$ e $T:V \rightarrow V$ un [[Isomorfismo e Endomorfismo|endomorfismo]] , è chiamiamo _autovettore_ un vettore $v \in V,v \not= 0$  e un _autovalore_ di $T$ associato a $v$  un qualunque $\lambda \in \mathbb{K}$ tale che

$$
T(v)=\lambda v
$$

> [!tip]
> - tutti i vettori dello $Span(v)$ sono _autovettori_ con lo stesso _autovalore_
> - Gli _autovettori_ $v$ con _autovalore_ $\lambda =0$ sono i vettori $v \not =0 \land v \in ker(T)$
> - Gli _autovettori_ $v$ con _autovalore_ $\lambda =1$ sono i vettori $v \not =0$  che sono [[Punti Fissi]]


![[UniPi-Appunti/Studi/Triennale Informatica/1° Anno/Algebra Lineare (AL)/Media/Untitled 7.png]]

![[UniPi-Appunti/Studi/Triennale Informatica/1° Anno/Algebra Lineare (AL)/Media/Untitled 1 4.png]]

### Esistenza di autovettori
- se $dim(\mathbb{R}^n)$ é dispari esiste sempre almeno un _autovettore_ in $\mathbb{R}$ questo perché se $P_A(\lambda)$  ha grado dispari ha sempre una radice in $\mathbb{R}$
	- e  se c è una radice in $\mathbb{C}$ c è sempre anche il suo _coniugato_
- Esiste sempre un autovalore nel campo $\mathbb{C}$ questo perché il [[Calcolare autovalori e autovettori|polinomio caratteristico]] $P_A(\lambda)$ ha sempre una radice in $\mathbb{C}$


### Relazioni
$A$ e $A^{n}$: siano  $\lambda_{i}$ gli _autovalori_ di $A$ sono allora $\lambda_{i}^{n}$ sono autovalori di $A^{n}$
$A$ e $C=A+I$: siano  $\lambda_{i}$ gli _autovalori_ di $A$ sono allora $\lambda_{i}+1$ sono autovalori di $C$


>[!tip]
>spiegazione geometrica [qui](https://youtu.be/PFDu9oVAE-g?si=16LM0hSv0a3owhfw)