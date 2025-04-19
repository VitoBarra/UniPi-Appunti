---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Manifolds (Varieta)
---
un __Manifolds__ (in italiano __variatà__) è uno [[Spazio Topologico|spazio topologico]] che localmente sembra uno [[Spazio Euclideo|spazio euclideo]]. Più formalmente abbiamo che 

__Sia__ $S$ uno [[Spazio Topologico|spazio topologico]]
__se__ $\forall p \in S$ si cha che il [[Vicinato topologico|vicinato]] di $p$ è [[OmomorfismI|Omomorfo]] ad uno [[Spazio Euclideo|spazio euclideo]] di dimensione $n$
__Allora__ si cha che $S$ è $n$-Manifold



###### 2-manifolds
una __superfice__ si dice un $2$-manifold se il vicinato di ogni punto di $\boldsymbol{p}$ sulla superfice esiste una [[OmomorfismI|omomorfismo]] ad uno [[Spazio Euclideo|spazio euclideo]] di dimensione $2$. 
Visivamente si ha che preso un disco o un semi disco (nel caso di bordi), possiamo centrarlo in un qualsiasi in qualsiasi punto $p$ sulla superfice e farlo aderire a tutta la superfice stessa.

una esempio di superfice non manifold è il seguente
![[IMG - Manifoldnes con punti non manifold.png]]
Sul punto di dove c è una stretta non si puo definire una vicinato per quanto infinitesimale che è totalmente contenuto nella superfice, in generale i casi di non manifoldnes  2
![[IMG - oggetti non Manifolds.png]]



#### Manifoldness
una __mesh poligonale__ può essere un $2$-[[Manifolds (Varieta)|manifold]] 
![[Pasted image 20240220034236.png]]
Per controllare che la __mesh__ sia un $2$-manifold se valgono le due seguenti proprietà:
1. __Edge Manifold__ ogni spigolo (edge) é condiviso da massimo due triangoli
2. __Vertex Manifold__ : prese un numero arbitrario di facce $f_i$ che condividono un vertice $v_i$ (anche dette le facce incidenti a $v_i$) allora partendo dal vertice $v_i$ esiste una percorso sugli edge delle facce $f_i$ tale che questo tocchi tutti i vertici di tutte le facce $f_i$ senza ripassare per $v_i$. 
due esempi di mesh che non sono manifold sono
![[Pasted image 20240220034225.png]]
