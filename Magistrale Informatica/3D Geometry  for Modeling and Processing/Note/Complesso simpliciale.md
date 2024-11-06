---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Complesso simpliciale
---
una collezione di [[Simplex (Simplesso)|simplessi]] $(\sigma_1,\sigma_2,\dots,\sigma_n)\in  \Sigma$  è detto __$k$-[[Complesso di celle (Cell Complex)|complesso]] simpliciale__ 
__se__
- $\forall \sigma_1,\sigma_2 \in \Sigma$ si ha che $\sigma_1 \cap \sigma_2 \not= \emptyset \implies \sigma_1 \cap \sigma_2$ è un __[[Simplex (Simplesso)|simplesso]]__ $\in \Sigma$
- $k$ è il massimo ordine dei simplessi in $\Sigma$
![[Pasted image 20241019180447.png]]

###### Complesso simpliciale massimale
un $k$-__complesso simpliciale__ è detto __massimale__ se tutti i simplessi massimali che lo compongono sono di ordine $k$. Geometricamente si ha che non ci sono delle parti di dimensione minore di $k$ appese.
![[Pasted image 20241019181816.png]]

###### Adiacenza e incidenza
Due [[Simplex (Simplesso)|simplessi]] $\sigma$ e $\sigma'$ si dicono __incidenti__ se $\sigma$ è una faccia propria di $\sigma'$ o viceversa.

Due $k$-simplessi $\sigma$ e $\sigma'$  al interno di una __complesso simpliciale__ si dicono $m$-__adiacenti__ con $m<k$ se esiste una $m$-simplesso che è una faccia propria sia sia di $\sigma$ che di $\sigma'$