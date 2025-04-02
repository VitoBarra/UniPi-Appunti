---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Conversione tra rappresentazioni di oggetti
---
un campionamento del dominio di una  [[Curve parametriche]] , 
campionamento regolare del domioneo non implica regolarità nella mesh, ovvero la mesh finale avrà delle zone con faccine piu piccole e zone con faccine piu grandi. 

Secondo me questo dipende dal fatto che la derivata in certi piu della funzione e piu grande e quindi una piccola variazione sposta di tanto sulla funzione e quindi in 3D punti piu distanti e faccine piu grandi.



convertire [[Superfici implicite]] in mash 
si utilizza il marching cube: compinamento regolare della funzione e interpolazione lineare tra gli spigoli per trovare l iso superficie. 2^4 casi in 3D 2^8 ma per simmetria ci si riduce a 15 casi

per passare da mesh a superi e implicita: 
campi di distanza campianati:  questo è utile in quanto è comodo fare operazioni con funzioni implicite come somma che resta un operazione implicita 


Teoria dei segnali: casino col campionamento. questo genera quindi un sacco di sampling artifact.


