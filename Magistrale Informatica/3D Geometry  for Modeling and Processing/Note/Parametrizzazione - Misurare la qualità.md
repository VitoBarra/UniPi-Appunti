---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Parametrizzazione - Misurare la qualità
---
La valutazione della qualità di una [[Parametrizzazione|parametrizzazione]]  si valuta tramite una metrica denominata ***sbriciolosità*** (in inglese ***crumbliness***) per quantificare l'efficacia di un atlas. Tale metrica è definita come il rapporto tra la somma dei perimetri delle isole dell’atlante e il perimetro di un cerchio ideale con la stessa area della superficie da parametrizzare:

$$
\text{sbriciolosità} = \frac{\sum_i P_i}{2 \sqrt{\pi A}}
$$

dove $P_i$ è il perimetro dell’isola $i$ e $A$ è l’area totale della superficie. Tale definizione corrisponde intuitivamente alla nozione di un atlas eccessivamente frammentato, dove molte piccole regioni aumentano il perimetro complessivo rispetto a una distribuzione più compatta.
![[IMG - qualita di una parametrizzazione crumblenes.png]]