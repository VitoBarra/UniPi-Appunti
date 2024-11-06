---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Relazioni di adiacenza in una mesh
---
Le __relazioni di adiacenza__ in una [[Mesh Poligonali|mesh]] sono delle relazioni che si utilizzano per costruire strutture dati utili a conservare e fare operazioni sulle __mesh__ stesse.

Queste sono matematicamente ben fondate siccome si basano sui concetti di [[Complesso simpliciale|adiacenza e incidenza]] dei [[Complesso simpliciale#Adiacenza e incidenza|complessi di celle]]. Questo ha senso perché le __mesh polinomiali__ sono in generale [[Complesso di celle (Cell Complex)|complessi di celle]] e le __mesh polinomiali ben formate__ sono $2$-[[Complesso simpliciale#Complesso simpliciale massimale|complessi simpliciali massimali]]

Per rappresentare delle relazioni di adiacenza di una [[Mesh Poligonali|mesh pologonale]] si denota, per __convenzione__, utilizzando una __coppia ordinata__ di lettere. ogni lettera indica  
- $E$: Edge 
- $V$: Vertex
- $F$: Face
in totale le relazioni sono 9 una per ogni possibile coppia 
![[Pasted image 20241026182722.png]]
1. $FF$ è la $1$-[[Complesso simpliciale#Adiacenza e incidenza|adiacenza]] di tutte l'facce ovvero gli edge condivisi tra le facce
2. $EE$ è la $0$-[[Complesso simpliciale#Adiacenza e incidenza|adiacenza]] di tutte l'facce ovvero i vertici condivisi tra le facce
3. $FE$ è l'insieme di sotto facce proprie di  $F$ di dimensione $1$ 
4. $FV$ è l'insieme di sotto facce proprie di  $F$ di dimensione $0$ 
5. $EV$ è l'insieme di sotto facce proprie di  $E$ di dimensione $0$ 
6. $VF$ è l'insieme delle facce $F \in \Sigma$ tale che il vertice $V$ è una faccia propria di $F$ 
7. $VE$ è l'insieme dei edge  $E \in \Sigma$ tale che il vertice $V$ è una faccia propria di $E$
8. $EF$ è l'insieme delle facce  $F \in \Sigma$ tale che l'edge $E$ è una faccia propria di $F$
9. $VV$ è l'insieme di vertici $V' \in \Sigma$ tale che  $\exists$ un edge $E$ tra $V$ e $V'$



Solitamente queste rappresentazioni non si tengono __interamente__ ma __parzialmente__ ad esempio invece di tenere la relazione intera $VF$ per ogni vertice si tiene un unica faccia e le altre vengono ritrovate usando l'adiacenza $FF$  questo si fa principalmente per motivi di efficienza siccome comunque le  facce incidenti ad un vertice ha numero variabile mentre per la relazione $FF$ sono al massimo $2$.
in questo tipo di casi per ricostruire correttamente tutto quello che si poteva raggiungere con la $VF$ c è bisogno che la mesh sia $2$-[[Manifolds|manifold]] infatti ad esempio non è possibile nel immagine seguente.
![[Pasted image 20241026230440.png]]

In generale per un [[Complesso simpliciale|complesso simpliciale]] $2$-[[Manifolds|manifold]] la cardinalità di queste adiacenze sono quasi tutti limitate infatti si ha che 
- $|FV|=|FE|= 3$
- $|EV|=2$
- $|FF|\leq 3$ (a me torna $3$ ma  nelle c è scritto $2$)
- $|EF|\leq 2$
mentre le altre hanno grado variabile ma sono stimabili. Infatti mediamente si ha che
- $|VV|\approx|VE|\approx|VF|\approx6$
- $|EE|\approx10$
- $F\approx 2V$
