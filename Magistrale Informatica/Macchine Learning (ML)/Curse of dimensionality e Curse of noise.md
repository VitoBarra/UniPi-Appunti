---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Curse of dimensionality e Curse of noise
---
Al crescere della **dimensionalità** $n$ dell'input il modello è sempre meno capace di costruire una buona generalizzazione e questo è noto come __Curse of dimensionality__.  Questo avviene principalmente dal fatto che in dimensionalità alta è molto probabile che i $K$ dati piu vicini siano spazialmente lontani e che quindi quindi la stima non sia piu "locale".
Assumendo che ogni variabile sia nel range $[0,1]$, questo fenomeno può essere notato partendo da un cubo unitario e mostrando quale è la frazione del range di range necessaria per ogni variabile per coprire una certa percentuale del volume.

Abbiamo infatti che $n$ dimensioni per coprire una frazione $r$ del volume abbiamo bisogno del $r^{1/n}$ range di ogni variabili
![[Pasted image 20241225061718.png]]
In più la densità di sampling scende infatti la densità è calcolata come $\cfrac{\ell}{volume}$ che è proporzionale a $\ell^{1/n}$



 La  "__curse of noisy__", si verifica quando i dati dipendono da poche feature rilevanti, ma includono molte feature irrilevanti. Queste ultime possono dominare quelle rilevanti, portando a classificazioni errate e riducendo l'efficacia dell'algoritmo. Questo problema si può mitigare pesando le feature in base alla rilevanza oppure facendo __feature Selection__, ovvero eliminando alcune variabili.