---
Course: "[[3D Geometry for Modeling and Processinga (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Cadmur-Clark
---



L algoritmo di suddivisione clad in-Clark puo essere nche fatto in due passi utilizzando un algoritmo “half dual” che ha anche delle proprietà comode da solo siccome rende la mesh comporta solo da quadriilati, che in certi contesti è comodo.

La libreria è face center e solitamente funziona per triangolo ma ha qualche utilità anche per i poligoni.

Si possono calcolare i baricentri delle facce con CalcolatePolyBaricenter()


La libreria tende a non aggiornare i puntatori interni qundi conviene usare altre cose come male (int, int), int
