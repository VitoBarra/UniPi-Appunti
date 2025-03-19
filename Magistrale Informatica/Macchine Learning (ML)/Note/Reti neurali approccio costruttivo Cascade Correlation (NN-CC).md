---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic: 
Bib: "[[NIPS-1989-the-cascade-correlation-learning-architecture.pdf]]"
---
# Reti neurali approccio costruttivo Cascade Correlation (NN-CC)
---
L'algoritmo __Cascade Correlation__ è un __approccio costruttivo__ per allenare una [[Reti Neurali (NN)|rete neurale]] in modo [[Algoritmi di learning supervisionato|supervisionato]].
Sia il __numero di unita__ e i pesi vengono scelti  dal algoritmo di learning. 

Partendo da una rete minimale incrementalmente si aggiungono unità durante il training fino a quando non si raggiunge convergenza dell'errore.


## Descrizione dell'algoritmo

Si parte con una rete neurale $N_0$, ovvero una rete che collega gli input esterni direttamente agli output.

Si procede nel seguente modo:
1. Addestramento di $N_0$: si calcola l'errore per la rete $N_0$ Se $N_0$ non è in grado di risolvere il problema, si passa alla rete $N_1$.
2. In $N_1$, viene aggiunta un'unità nascosta con un collegamento in input da tutti gli input esterni e da tutti le altre unita nascoste. I pesi di questi collegamenti sono scelti in modo che la __correlazione__ (ovvero la [[Variabili aleatorie - Covarianza e correlazione|covarianza]]) tra l'__output dell'unità che viene aggiunta__ $o_{p,h}$ e l'__errore residuo__ $E_{p,k} = (o_{p,k}-d_{p,k})$ al unita di output $k$ della rete $N_0$ sia massimizzata. Denominando $S$ la covarianza $$S=\sum_{k}\left|\sum_{p}(o_{p,h}-\overline{o}_h)(E_{p,k}-\overline{E_{k}})\right|$$con $p$ un indice per indicare un singolo pattern. massimizziamo $S$ tramite [[Tecnica di ottimizzazione Gradient Descent|salita di gradiente]] e perciò la regola di aggiornamento è la seguente$$\begin{array} {}
\displaystyle \frac{\partial S}{\partial w_{hj}} = \sum_k sign(S_k)\sum_p \left(E_{p,k} - \overline{E_k} \right) f'(net_{p,h}) In_{p,j}\\ 
w_{hj} = w_{hj} + \cfrac{\partial S}{\partial w_{hj}}
\end{array}
$$dove $f'(net_{p,h})$ è la derivata della [[Funzioni di attivazione|funzione di attivazione]] del $net$ del unita aggiunta e  $In_{p,j}$  è l input proveniente da unita $j$ per il patter $p$. L allenamento continua finché i miglioramenti finiscono e al termine i pesi vengono congelati, ovvero non possono essere modificati nei passi successivi. 
3. Vengono addestrati i pesi rimanenti in $N_1$ dello strato di output tramite ad esempio [[BackPropagation|Back Propagation]] o una sua variante con [[last Mean Squere (LMS)|LMS]] come funzione di __loss__
4. Se la rete ottenuta $N_1$ non risolve il problema, si aggiungono progressivamente nuove unità nascoste collegandole a tutti gli input e a tutte unità nascoste precedentemente aggiunte.
5. Il processo continua fino a quando gli errori residui dello strato di output soddisfano un criterio di arresto specificato. 

L'algoritmo costruisce dinamicamente una rete neurale e termina quando è stato trovato un numero sufficiente di __unità nascoste__ per risolvere il problema.
![[Schermata del 2025-02-26 22-19-07.png]]

Ogni unità aggiunta serve per ridurre l'errore residuo dell'output e per risolvere un "sotto problema". Quindi un'unità diventa un "__feature-detector__" permanente.

Per evitare i __massimi locali__ durante l addestramento dei pesi di ingresso della nuova unita da aggiungere si usa il __Pooling__ ovvero vengono allenate diverse unita e poi tra queste viene scelta la migliore.

questo algoritmo può essere considerare un algoritmo greedy in quanto arriva a convergenza con un numero minimi di unità ma può portare ad overfitting e si deve quindi [[Regularization|regolarizzare]].
