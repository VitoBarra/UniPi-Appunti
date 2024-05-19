---
Subject: "[[Computer Grafica (CG)]]"
tags:
  - CG
Area: 
topic: "[[Illuminazione nella Computer Grafica]]"
SubTopic: "[[Illuminazione - Ombre]]"
---

# Illuminazione - Aliasing nelle Ombre
---
il concetto di [[Aliasing e Anti-Aliasing|aliasing]] colpisce anche le [[Illuminazione - Ombre|ombre]] con lo shadow mapping. Infatti a tutti gli effetti uno shadow map è una metodologia basta su lockup di una tabella (lo z-buffer) e quindi il suo effetti dipende dalla dimensione di questa tabella.
Il problema finale che si ottiene con risoluzioni basse e che piu frammenti vengono mappati nella stessa cella generando quindi l __aliasing__ e vedendo la tabella come un [[Texture|texture]] si ha che stiamo avendo __magnification__ ovvero un texel viene mappato a piu frammenti ottenendo quindi.
![[Pasted image 20240308025859.png]]
#### Percentage closer filtering (PCF)
il  __Percentage closer filtering__ è una metodologia per mitigare il problema del __aliasing__ nelle ombre infatti questo serve ad ammorbidirla.

_siano_
- $f$ il frammento che si vuole renderizare
- $K$  l insieme dei suoi vicini chiamato __kernel__ 
![[Pasted image 20240308041604.png]]
_allora_ si calcola se  $f$ è in ombra eseguendo il test dello shadow mapping su $f$ per ogni suo vicini in $K$  ottenendo per ogni frammento testato un valore booleano e facendo la [[Statistica descrittiva - Dati Numerici#Media (definizione)|media]]  con la formula $$lit=1-\cfrac{1}{|K|}\sum (z_{ij}<z_r)=\cfrac{1}{|K|}\sum (z_{ij}>z_r)$$dove $|K|$ è la [[Cardinalità di un insieme|cardinalita]] del [[Insiemi Matematici|insieme]] $K$  __lit__ è  un valore tra $[0,1]$  questo valore si utilizza per calcolare l ombra
![[Pasted image 20240308034946.png]]

Non si prende la media dei punti siccome altrimenti staremo andando a fare il sample di superfici inesistenti
![[Pasted image 20240308034915.png]]

##### Variance Shadow Maps (VSM) 
il valore $lit$ dell PCF puo essere visto come una [[Definizione di Probabilita|probabilita]] che ogni texel $z\in K$ contenga una profondata maggiore del valore di riferimento $$\mathcal{P}(z_{hk}>z_r)=lit=\cfrac{1}{|K|}\sum(z_{ij} \geq z_r)$$ quindi abbiamo una [[Distribuzione di probabilita|distribuzione]] di $\mathcal{P}$ ignota ma possiamo approssimare il suo [[Variabili aleatoria - Momenti|momento primo e secondo]].

Quando li renderizza la scena dalla __[[Illuminazione - Ombre|light-camera]]__ si calcolano 2 mappe. uno per la dept $z$ e un altra per la depth $z^2$. 
In questo modo si possono ottenere i momenti $E[z]$ e $E[z^2]$ facendo la [[Variabili aleatoria - Momenti|media]] con i valori nel kernel 
![[Pasted image 20240308051923.png]]
e quindi si puo calcolare la [[Variabili aleatorie - Varianza|varianza]] come $$\sigma^2 = E[z^2]-E[z]^2$$  dalla [[Diseguaglianza di Chebyshev|Diseguaglianza di Chebyshev]] si ottiene il risultato che 
_sia_ con $\mu = E[z]$
$$\begin{align}
 & if \  z_r > \mu: \\
 & \mathcal{P}(z_{hk}>z_r) \leq \cfrac{\sigma^2}{\sigma^2+(z_r-\mu )^2}
\end{align}$$ e quindi abbiamo un valore superiore alla probabilita.
In VSM possiamo usare questo bound superiore come valore per PC, in questo utilizzando il [[Texture Filtering|filtering]] si puo evitare di fare piu accessi alla shadow map in run time  
