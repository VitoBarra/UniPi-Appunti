---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: "[[Reti Neurali (NN)]]"
topic: 
SubTopic:
---
# Reti neurali Feed-Forward (FF)
---
Una __[[Reti Neurali (NN)|reti neurale]] Feed Forward__ è un tipo di __[[Modelli Parametrici|modello parametrico]]__ di [[Concetti generali del Machine Learning|machine leanring]]  e viene solitamente allenato con [[Algoritmi di learning supervisionato|algoritmi supervisionati]].


__Le unità sono connesse tramite collegamenti pesi__ e organizzate in _layers_ con la seguente struttura:
- __Input Layer__: Copia i pattern esterni $x$ sugli ingressi (non calcola $\text{net}$ né $f$).
- __Hidden Layer__: Il livello nascosto proietta sul livello di output (o su un altro livello nascosto).
- __Output Layer__ : ultimo layer del modello che ne calcola l output 

Ogni neurone è un __unità__ definito in modo molto simile al [[Rete di Percettroni|percettrone]] ma se ne cambia la [[Funzioni di attivazione|funzione di attivazione]].
![[Pasted image 20241229014328.png]]
Una __Feed Forward__ può anche essere vista come come un __ipotesi flessibile__ $h$. Per questa $h$ è vale che ad ogni input è associato un solo output e quindi è una [[Funzioni|funzione]] 

considerando un __input layer__ un __hidden layer__ e un __output layer__ l ipotesi è la seguente funzione: $$h_\mathbf{W}(\mathbf{x})=f_k\left(\sum_jw_{kj}f_j\left(\sum_iw_{ji}x_i\right)\right)$$Dove
- $\mathbf{W}$ è la matrice dei __parametri__ ovvero i pesi 
- $\mathbf{x}$ il vettore di __input__.

se almeno una delle [[Funzioni di attivazione|funzioni di attivazioni]] $f$ è una funzione NON lineare allora $h$ è funzione NON è [[Equazioni Lineari e Lineari omogenee|lineare]] nei parametri $W$, nel caso in cui queste invece siano lineari allora l'ipotesi diventa uguale ad avere un solo layer e si ritorna ad un [[Modelli lineari con LMS|modello lineare]].

con $h$ NON lineare si ha che il problema di ottimizzazione per imparare i parametri diventa un problema non lineare.

alcuni esempi di architetture sono le seguenti:
![[Pasted image 20241229014458.png]]
Quando una Feed-Forward è __Totalmente connessa__ e la funzione di attivazione $f$ non è lineare allora si parla di __Multy layer perceptron__ (__MLP__)



#### Flessibilità delle Feed-Forward 

lo __spazio delle ipotesi__ $\mathcal{H}$ delle feed-Forward dipende dal __architettura__ ovvero: 
 - __Numero di unità__: Quantità di nodi nei vari strati della rete.
 - __Topologia__: Come sono organizzati e connessi i nodi in questo caso il __numero di layer__.
ed è lo spazio continuo di tutte le [[Funzioni|funzioni]] che possono essere espresse cambiando i valori dei parametri $\mathbf{W}$ e questo il  __[[Algoritmi di Machine Learning|bias di linguaggio]]__

lo __spazio delle ipotesi__ $\mathcal{H}$ è considerato a __[[Statistical Learning Theory (SLT)|VC-dimension]] variabile__, e la dimensione dipende dal numero di parametri $w$ e dal loro valore. Infatti abbiamo che
- $w$ vicino a zero, si è generalmente nella parte lineare delle [[Funzioni di attivazione|funzioni di attivazione]] e quindi la VC-dimesion è bassa
- $w$ più grandi ci portano in regioni sempre meno lineare e quindi VC-dimension più alta.
 per questo motivo durante in training si parte da valori piccoli di $w$ e si va verso valori più grandi.


Le reti feed-forward possono essere utilizzate sia per problemi di classificazione che per problemi di regressione adattando la funzione di attivazione del layer di output. Per affrontare problemi di classificazione multi-classe o multi-regressione, invece, è necessario variare il numero di unità nel layer di output.

![[Pasted image 20250101112825.png]]

Ogni neurone può essere visto come una funzione  $\phi$ della [[Linear Basis Expansion (LBE)|Linear Bases Expantion]]$$\phi_j(\mathbf{x},\mathbf{w})=f_j\left(\sum_iw_{ji}x_i\right)$$ è $\phi$ __Adattiva__ ovvero dipende anche dai parametri e di conseguenza anche dai dati da cui i parametri sono imparati, Mentre del [[Modelli lineari con LMS|modello lineare]] la $\phi$ è __fissa__.   



L'algoritmo di apprendimento [[BackPropagation|backpropagation]] è generalmente legato alle proprietà di __smoothness__ delle funzioni. Ovvero piccole variazioni in input portano a piccole variazioni in output.

Questa assunzione ha senso perché una per funzione obiettivo non continua ad esempio un generatore di numeri casuali non ha senso parlare di generalizzazione.
e questo è il [[Algoritmi di Machine Learning|bias di ricerca]]