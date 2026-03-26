---
Course: "[[Statistica (STAT)]]"
tags:
  - STAT
---
# Variabili Aleatorie Notevoli - Gaussiana multivariata
---
La **gaussiana multivariata** e una [[Distribuzione di probabilita|distribuzione di probabilita]] continua su vettori reali $X\in\mathbb{R}^d$ e generalizza la [[Variabili Aleatorie Notevoli - Gaussiana|gaussiana]] univariata al caso in cui le osservazioni abbiano piu componenti. Essa e parametrizzata da un vettore delle medie $\mu\in\mathbb{R}^d$ e da una [[Matrici quadrate|matrice quadrata]] di [[Variabili aleatorie - Covarianza e correlazione|covarianza]] $\Sigma\in\mathbb{R}^{d\times d}$ simmetrica e [[Matrici Definite|definita positiva]].

Se $X\sim\mathcal{N}(\mathbf{\mu,\Sigma})$, la sua densità e$$p(x)=\frac{1}{(2\pi)^{d/2}|\mathbf{\Sigma}|^{1/2}}\exp\left(-\frac{1}{2}(\mathbf{x-\mu})^T\mathbf{\Sigma}^{-1}(\mathbf{x-\mu})\right)$$I parametri hanno il seguente significato:
- $\mathbf{\mu}$: determina la posizione del centro della distribuzione
- $\mathbf{\Sigma}$: descrive la dispersione della distribuzione lungo ciascuna coordinata e la dipendenza lineare tra coppie di coordinate
- gli elementi diagonali di $\mathbf{\Sigma}$ sono le varianze delle singole componenti
- gli elementi fuori diagonale di $\mathbf{\Sigma}$ sono le covarianze tra componenti diverse

La matrice $\mathbf{\Sigma}$ determina quindi non solo quanto la distribuzione sia dispersa, ma anche la sua forma geometrica e il suo orientamento nello spazio. Il fatto che sia [[Matrici Definite|definita positiva]] garantisce che ogni combinazione lineare non banale delle componenti abbia varianza strettamente positiva, questo serve siccome una varianza negativa non ha significato.
Alcuni casi particolari sono:
- se $\mathbf{\Sigma}=\sigma^2 I$, la distribuzione e **isotropa**
- se $\mathbf{\Sigma}$ è [[Matrici quadrate|diagonale]], le componenti sono incorrelate e la densità si fattorizza come prodotto di [[Variabili Aleatorie Notevoli - Gaussiana|gaussiane univariate]]
- se $d=1$, la gaussiana multivariata coincide con la [[Variabili Aleatorie Notevoli - Gaussiana|gaussiana univariata]] 
La gaussiana multivariata e uno dei modelli continui fondamentali nelle [[Variabili Aleatorie Multivariate|variabili aleatorie multivariate]].
![[IMG - Gaussiana multivariata.png]]
