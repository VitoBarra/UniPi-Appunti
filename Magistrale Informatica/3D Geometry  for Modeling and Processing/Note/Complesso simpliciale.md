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
__$k$-[[Complesso di celle (Cell Complex)|complesso]] simpliciale__ è una [[Insiemi Matematici|insieme]] di [[Simplex (Simplesso)|simplessi]] $(\sigma_1,\sigma_2,\dots,\sigma_n)\in  \Sigma$   
__tale che__
- $\forall \sigma_1,\sigma_2 \in \Sigma$ si ha che $\sigma_1 \cap \sigma_2 \not= \emptyset \implies \exists \sigma_3 \in \Sigma \mid \sigma_3=\sigma_1 \cap \sigma_2$
- $k$ è il massimo ordine dei [[Simplex (Simplesso)|simplessi]] in $\Sigma$
![[IMG - Complesso sempliciale.png]]
un $k$-__complesso simpliciale__ è detto __massimale__ se tutti i [[Simplex (Simplesso)|simplessi]] che lo compongono sono di ordine $k$. ![[IMG - Complesso sempliciale non massimo.png]]Geometricamente significa che non ci sono delle parti di dimensione minore di $k$ "*appese*".

###### Adiacenza e incidenza
Due [[Simplex (Simplesso)|simplessi]] $\sigma$ e $\sigma'$ si dicono __incidenti__ se $\sigma$ è una faccia propria di $\sigma'$ o viceversa.

Due $k$-simplessi $\sigma$ e $\sigma'$  al interno di una __complesso simpliciale__ si dicono $m$-__adiacenti__ con $m<k$ se esiste una $m$-simplesso che è una faccia propria sia sia di $\sigma$ che di $\sigma'$