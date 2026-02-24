---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Caual Bayesian Network
---
Il un **_Causal bayesian Network_** o (**causal network** o **causal diagram**) è un classe [[Bayesian network|Bayesian Networks]] piu restrittiva dove si impone che la direzione delle frecce rifletta necessariamente la struttura **causale** sottostante ai **fenomeni modellati**. In un modello causale, l’ordinamento dei nodi deve essere compatibile con la direzione della causalità. Ciò significa che se un evento $A$ causa un evento $B$, allora l’arco viene tracciato come $A \to B$, e non viceversa. Sebbene una rete con l’arco invertito $A \leftarrow B$ possa descrivere la stessa [[Full Joint Distribution (FJD)|distribuzione congiunta]] delle [[Variabili Aleatorie (Casuali)|variabili]], essa perde la capacità di rappresentare l’asimmetria causale che distingue il meccanismo generativo del fenomeno. Questa distinzione è cruciale, poiché la causalità implica una direzione di influenza: agire su $A$ può modificare $B$, ma non necessariamente l’inverso.

**Formalmente**  una **rete causale** è definita dal ***equazione strutturale***. che afferma che Ogni variabile $X_i$ è definita come risultato di una [[Funzioni|funzione]] deterministica dei suoi genitori nel modello, ossia$$
x_i = f_i(\text{OtherVariables}),
$$dove la funzione $f_i(\cdot)$ rappresenta il meccanismo naturale che assegna il valore di $X_i$ in base alle variabili da cui dipende. Un arco $X_j \to X_i$ viene tracciato se e solo se $X_j$ compare tra gli argomenti della funzione $f_i$. 
Questa rappresentazione non è puramente probabilistica: le equazioni strutturali descrivono meccanismi che rimangono invarianti rispetto a modifiche locali dell’ambiente, contrariamente alle sole relazioni probabilistiche che possono variare in seguito a cambiamenti osservativi o interventi esterni.

Tale proprietà di ***stabilità locale*** costituisce il principale vantaggio delle **reti causali**. Ad esempio, in un modello che rappresenta la relazione tra pioggia, irrigatore e erba bagnata, la disattivazione dell’irrigatore si traduce semplicemente nella rimozione degli archi incidenti sul nodo corrispondente. ad esempio, la copertura del prato con una tenda può essere modellata eliminando solo l’arco $Rain \to WetGrass$ mentre se la rete non fosse stata causale ci sarebbe stato bisogno di molte piu modifiche. Questa capacità di adattare la struttura della rete con modifiche minime riflette la robustezza dei meccanismi causali rispetto a perturbazioni locali del sistema.
![[IMG - Caual Bayesian Network stabilita strutturale.png]]
