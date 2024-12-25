---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
Course 2: "[[Machine Learning (ML)]]"
topic: nota
tags:
  - IA
---

# K-Nearest Neighbor (K-NN)
---
il $K$-Nearest Neighbor è un algoritmo di __[[Algoritmi di Apprendimento NON supervisionato|learning supervisionato]]__ __[[Modelli di Macchine learning Instance-Based|instance-base]]__.  
Questo algoritmo si utilizza principalmente per la classificazione e si basa sul idea  che i nuovi punti siano simili a quelli "vicini".

Per valutare quando due punti siano vicini si utilizzano delle metriche una ad esempio è la __[[Distanza euclidea|distanza euclidea]]__ 


l'algoritmo per la classificazione binaria è il seguente. 
1. Scegli un valore $k \in \mathbb{N}$ arbitrario 
2. Mantenere i dati di training  in memoria come lista  di coppie $( \mathbf{x}_p, \mathbf{y}_p) \ \ P=1,\dots,l$ dove $\mathbf{x}_i\in \mathbb{R}^n$ e $y_i\in [0,1]$ ovvero una variabile binaria.
3. dato in un input $\mathbf{x}\in \mathbb{R}^n$ sconosciuto e $d(\mathbf{x},\mathbf{x}_i)$ una __distanza__ trova $k$ vicini tale che  $$N_k(\mathbf{x})= \arg_p \min d(\mathbf{x} ,\mathbf{x}_p) = \{(\mathbf{x}_1,y_1)\dots(\mathbf{x}_k,y_k)\}$$ ovvero i $k$  __dati di training__ più vicini al nuovo dati $\mathbf{x}$  
![[Pasted image 20241220211455.png]]

4. Calcola la classe media scelta, questo rappresenta un voto di maggioranza  $$avr_k(\mathbf{x})= \frac{1}{k}\sum_{x_i\in N_k(\mathbf{x} )} y_i$$
5. restituisci la classe che vince il voto di maggioranza, ovverods$$
\begin{cases}
1 & if & avg_k(\mathbf{x})>0.5 \\
0 & & \text{otherwise}
\end{cases}$$ 


con $K=1$ si ha un modello __molto flessibile__, non ha errori di classificazione su __training set__ e ha un decision boundry non lineare e molto inrregulare e rumoroso. Solitamente va in __[[Overfitting e Underfitting|overfitting]]__
![[Pasted image 20241225023553.png]]
con un $K$ più altro si ottiene un decision boundary comunque flessibile e non lineare ma un po meno rumoroso. Solitamente un valore alto ma non troppo porta a dei buoni risultati.
![[Pasted image 20241225023615.png]]
con $K=\ell$ abbiamo che il modello è molto rigido è siamo in [[Overfitting e Underfitting|underfitting]].

Questo algoritmo utilizza implicitamente i [[Diagramma di voronoi|diagrammi di voronoi]].


Per fare [[Algoritmi di apprendimento supervisionato|classificazione]] multi class invece si utilizza lo stesso algoritmo ma se ne cambia l output. Infatti si ha che ritorna la classe più comune tara i suoi $K$ Vicini$$h(\mathbf{x})= \arg_v \max \sum_{(\mathbf{x}_i,y_i)\in N_k(\mathbf{x})}\mathbf{1}_{v,y_i}$$dove $$\mathbf{1}_{v,y_i}=
\begin{cases}
1 & if & v=y_i \\
0 & &\text{otherwise} 
\end{cases}
$$ una variante di questo dove pero si da più peso a i punti più vicini e meno a quelli più lontani è la seguente $$h(\mathbf{x})= \arg_v \max \sum_{(\mathbf{x}_i,y_i)\in N_k(\mathbf{x})}\mathbf{1}_{v,y_i} \cdot \cfrac{1}{d(\mathbf{x},\mathbf{x}_i)^n}$$ e per gestire il caso limite $d(\mathbf{x},\mathbf{x}_i)=0$ si ritorna $y_i$ perché sono lo stesso punto.


Per fare [[Algoritmi di apprendimento supervisionato|regressione]] invece lo stesso algoritmo ma come output direttamente la media delle posizioni dei vicini.



### Discussione
In generale il al $k$ -Nearest Neighbor vengono attribuiti $\cfrac{\ell}{k}$ gradi di libertà  dove $\ell$  è il numero di dati a disposizione.
I __gradi di libertà__ son detti "parametri effettivi" del modello.

Al variare di questi cambiano le performance del algoritmo infatti abbiamo il seguente grafico che lo mostra:
![[Pasted image 20241225034737.png]]
Il classificatore $K$-NN  cerca di approssimare la soluzione di un __[[Classificatore Bayesiano|Classificatore Bayesiano]]__ mettendo in atto un'__approssimazione locale__ tramite i punti vicini al punto $\mathbf{x}$, della  __[[Probabilita condizionata|probabilità condizionata]]__ della classe di appartenenza. Questa probabilità condizionata ovvero ciò che il __classificatore Bayesiano__ utilizza per assegnare una classe al punto $\mathbf{x}$.

![[Pasted image 20241225034635.png]]
in questa immagine vediamo dei punti che vengono estratti  da due [[Variabili Aleatorie Notevoli - Gaussiane|gaussiane]] note. siccome sappiamo le distribuzioni è possibile calcolare la soluzione del __classificatore bayessiano__ direttamente (a sinistra)  e si puo vedere come  il $K$-NN con $K=15$ riesce ad approssimare questa soluzione (destra)



## Bias-induttivo
1. __Distanza e Similarità__:  La distanza scelta nell'algoritmo determina quali esempi sono considerati più simili. La classificazione di un nuovo esempio dipende dalla classificazione dei suoi vicini più prossimi, secondo la metrica usata.

2. __Smoothness Locale__: si basa sul assunzione che esempi vicini abbiano etichette simili, una sorta di "regolarità locale". 
>[!tip] 
>È _possibile imparare_ la metrica 


## Limiti

L'algoritmo presenta diversi limiti, che possono influire sulle sue prestazioni e sull'efficacia in determinati contesti.

- __Costo computazionale elevato durante la fase di predizione__: questo rappresenta uno svantaggio significativo, poiché il calcolo può diventare molto oneroso a seconda della quantità di dati presenti. Per ogni nuovo dato da predire, è necessario calcolare la distanza con __TUTTI__ i punti memorizzati nel modello. Il tempo richiesto è quindi proporzionale al numero di dati, anche se esistono algoritmi di prossimità "ad-hoc" che possono ottimizzare questo processo. Inoltre, l'algoritmo comporta un __alto costo in termini di spazio__, dato che ogni dato deve essere mantenuto in memoria.

- __Problemi con la crescita della dimensione dell'input__: quando la dimensione dell'input aumenta, l'algoritmo è spesso soggetto a errori. Questo fenomeno è noto come la "__curse of dimensionality__". Con l'aumento della dimensione dell'input, il volume dello spazio cresce in modo esponenziale (ad esempio, il volume è proporzionale a $side^n$), rendendo i dati sempre più sparsi.
	![[Pasted image 20241225061718.png]]
- __Influenza delle feature irrilevanti__: un altro problema, noto come "__curse of noisy__", si presenta nei casi in cui i dati dipendono da poche feature rilevanti, ma includono molte altre feature irrilevanti. Queste ultime possono dominare quelle rilevanti, portando a classificazioni errate.

Questi aspetti devono essere considerati attentamente quando si sceglie di utilizzare questo tipo di algoritmo, specialmente in contesti con dati di alta dimensionalità o con molte feature potenzialmente non significative.




 
 
  