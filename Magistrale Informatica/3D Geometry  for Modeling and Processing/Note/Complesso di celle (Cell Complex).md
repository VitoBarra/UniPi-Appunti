---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Complesso di celle (Cell Complex)
---
una __cella__ è un [[Politopo|politopo]] [[Convessita|convesso]] di dimensione $d$ e una faccia propria di una __cella__ è un sotto insieme della cella che è un  [[Politopo|politopo]] [[Convessita|convesso]] di dimensione $d-1$ 
![[IMG - Complesso di celle cella e facce proprie.png]]

una collezione di __celle__ sono __cell comlex__ **se**
- ogni faccia della cella appartiene al complesso 
- per ogni coppia di celle $C$  e $C'$ si ha che l intersezione o è vuota o è una faccia in comune tra le due.
Ad esempio in questa immagine sono rappresentate delle celle che **NON** sono **complessi di celle**
![[IMG - Complesso di celle esempio non cell complex.png]]
ogni cella ha un ordine associato è questo è il numero di vertici o lati della cella.  
Un complesso è detto $k$-complesso se ordine massimo delle celle è $k$  


Una cella è __massimale__ se non è una faccia di una altra __cella__
un __$k$-complesso__ è detto __massimale__ se tutte le celle massimali del complesso hanno grado $k$ , geometricamente significa che non ci sono edge appesi, ad esempio questa **NON** è massimale ![[IMG - Complesso di celle complesso non massimale.png]]

