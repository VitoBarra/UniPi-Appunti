---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area: 
topic: 
SubTopic:
---
# Bagging (bootsrap aggregating)
---
 - Addestra $K$ classificatori su sottoinsiemi bootstrap del dataset.
 - Riduce la varianza mediando $h(x)$.


Tecnica di resampling z per stimare le proprietà di un modello quando i dati a disposizione sono pochi

Dato un dataset con $N$ esempi vengono creato un resample con $N$
esempi presi casualmente dal dataset originario.
Ciò vuol dire che ogni esempio può essere ripetuto o mai selezionato.
Il processo di resampling viene ripetuto molte volte per generare diverse versioni del dataset.

Per ogni resample si può allenare su di esso un modello e valutarne le performance con i dati che non sono stati utilizzati