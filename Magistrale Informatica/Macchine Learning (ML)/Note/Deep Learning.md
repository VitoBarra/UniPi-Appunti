---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: "[[Reti Neurali (NN)]]"
topic: 
SubTopic:
---
# Deep Learning
---
Il **Deep Learning** è una sotto-disciplina del [[Machine Learning (ML)|Machine Learning]] che si concentra sull'uso di __Deep Neural Networks__ (DNN). Queste reti si distinguono per la presenza di numerosi __hidden layer__, che consentono di apprendere rappresentazioni gerarchiche dei dati.
Un esempio classico di rete deep è il [[Reti neurali Feed-Forward (FF)|Multi-Layer Perceptron]] (MLP) con più __hidden layer__. 
![[Pasted image 20250205223357.png]]

Il __Deep learning__ ha un __bias induttivo__ dove assume che le funzioni che  [[Funzioni|funzione]] rappresenta siano per natura composizionale, ovvero sono della forma $$f(g(x))$$Questo avviene siccome ogni layer intermedio trasforma l'input in una rappresentazione a più alto livello ($g(x)$) che può essere usato dal successivo __come primitiva__ per costruirne una nuova ancora a più alto livello ($f(g(x))$) e cosi via fino al Output.  
questo processo è anche detto __feature learning__ ed ad ogni layer la feature imparata e in una [[Rappresentazione simbolica e distribuita dei concetti|rappresentazione distribuita]]
Questo processo aiuta la capacita di generalizzazione di una rete neurale siccome gli evita il dover imparare direttamente da tutte le [[Combinatoria|combinazioni]] degli input. 
![[Pasted image 20250205225036.png]]


Il __deep learning__ a differenza di altri modelli come il [[K-Nearest Neighbor (K-NN)|k-nn]] e gli [[alberi di decisione|alberi di decisione]]  __NON__ assumono una __similarità locale__ (__local smoothnes prior__) e infatti può generalizzare anche __NON localmente__ e questo gli permette  di mitigare la __curse of dimesionality__. 


#### Espressivita
le [[Reti Neurali (NN)|reti neurali]] del __deep learning__ *__NON__* sono più espressive rispetto alla sua controparte shallow questo grazie al [[Teorema di approssimazione universale|Teorema di approssimazione universale]] che ci dice che ogni rete con almeno un hidden layer può approssimare arbitrariamente bene qualsiasi funzione, ma non specifica nessun bound sul numero di unita necessarie per l approssimare. 
Per alcune famiglie di funzioni è possibile calcolare questo bound. 

Tuttavia, un __modello deep__ può essere __più efficiente__ in termini di numero di parametri e unita nascoste rispetto ad un modello shallow. Infatti, esistono famiglie di funzioni per cui un modello con almeno $d$ layer può approssimarle in modo compatto nel caso si avesse meno di $d$ layer è richiesto un numero di neuroni esponenziale rispetto al numero di input.

Il **No-Flattening Theorem** afferma le funzioni di natura composizione possono essere rappresentate in modo __efficiente__ da una __rete deep__, ma non possono essere rappresentate con la stessa efficienza se la rete viene appiattita a un solo hidden layer. 




#### Utilizzo delle rappresentazione intermedie
Nel __deep learning__ funziona per via della sua capacita di sfruttare le rappresentazioni intermedie costruite dagli hidden layer.
Per sfruttare al meglio questa proprietà sono state sviluppate alcune tecniche come il 
- __Layer-wise pre-training__:  strategie di training [[Algoritmi di Apprendimento semi-supervisionato|semi-supervisionato]] che sfrutta il **pratraining** su dati unlabled per creare le rappresentazioni interne prima di iniziare l effettivo training su dati con label
- __Transfer learning__: utilizzare rappresentazioni imparate in altri contesti per risolvere problemi diversi dal originale.

##### Pre-Training
un esempio di __pretraining layer-wise__ è il seguente algoritmo:
1. Allena il primo strato per essere un [[NN - Autoassociatore|autoassociatore]] e quindi per minimizzare l'errore di ricostruzione dell'input, questo si fa in modo [[Algoritmi di learning NON supervisionato|non supervisionato]] 
2. Gli output delle unità nascoste dell'autoassociatore vengono ora utilizzati come input per un altro strato, anch'esso addestrato come autoassociatore.  
3. Ripeti il processo descritto nel punto (2) fino a raggiungere il numero desiderato di strati. 
4. Usa l'output dell'ultimo strato nascosto come input per uno strato [[Algoritmi di learning supervisionato|supervisionato]] e inizializza i suoi parametri mantenendo il resto della rete fissa
5. Affina tutti i parametri di questa architettura profonda rispetto al criterio supervisionato.  
![[Pasted image 20250206182240.png]]

il  __pre-training__ può portare miglioramenti in alcuni compiti (soprattutto in [[Neural Lenguage Poricessing (NLP)|Neural Lenguage Processing ]]) ma non in altri. in più è difficile da gestire, ad esempio, gli effetti degli iperparametri divisi in due fasi: __pre-training__ e __training__.  

**"Oggi il pre-training non supervisionato è in gran parte abbandonato"** siccome le moderne tecniche di deep learning sono spesso sufficienti per un buon training da zero, ovvero tramite **end-to-end backpropagation** su tutta la rete deep.  

##### Transfer learning
per fare __Transfer Learning__ utilizziamo un altro modello gia allenato assumendo che esistano __feature imparate__ utili in diversi contesti.

alcuni modi di farlo sono i seguenti
- __Multi-task Learning__: si utilizza un modello già addestrato per un compito diverso mantenendo gli stessi input ma cambiando il target. fornisce una sorta di regolarizzazione implicita. 
- __Adattamento di dominio__:  in cui si cambia il dominio di input in un altro che ha __feature__ in comune con quello del dominio originario.
- __Trasferimento di feature__: si semplicemente parte da un modello allenato su un dataset molto grande e si riallena solo una piccola parte del modello in modo da adattarlo al task specifico (si fa spesso partendo da AlexNet) ![[Pasted image 20250206225714.png]]




### Training di una Rete Neurale deep
Una rete **neurale deep** può essere allenata tramite l'algoritmo di [[backpropagation|backpropagation]]. Tuttavia, durante l'addestramento, il valore del gradiente può subire due problematiche:
- **Vanishing Gradient**: Se il gradiente diventa troppo piccolo, gli aggiornamenti dei pesi nelle prime layer della rete diventano insignificanti, impedendo alla rete di apprendere.
- **Exploding Gradient**: Se il gradiente diventa troppo grande, gli aggiornamenti dei pesi diventano instabili, causando divergenza nel processo di training.
Per mitigare questo problema, sono state sviluppate diverse tecniche, tra cui **gradient clipping** e l'uso di funzioni di attivazione con derivata costante..

##### Gradient clipping
Uno dei metodi più comuni per affrontare il problema dell' __exploding gradient__ è il __gradient clipping__. Questo metodo previene aggiornamenti estremi limitando la norma del gradiente: $$g' = \nu \frac{g}{||g||} \quad \text{se } ||g|| > \nu$$Dove:
- $g$ è il gradiente originale
- $\nu$ è una soglia predefinita (hyperparameter) In questo modo, il gradiente mantiene la sua direzione originale, ma con una grandezza controllata.

La ripetizione di moltiplicazioni attraverso molti strati può introdurre discontinuità nella funzione di costo.   
![[Pasted image 20250208212930.png]]


##### Funzioni di attivazione
Le funzioni di attivazione __[[Funzione di attivazione - Sigmoidale|sigmoide]]__ e __[[Funzione di attivazione - TanH|tanh]]__ soffrono di saturazione: i loro valori tendono a essere molto vicini a $0$ o $1$, facendo sì che il gradiente diventi molto piccolo e rallenti l'apprendimento (__vanishing gradient__).
per migliorare questo aspetto si fa uso di __[[Funzione di attivazione - ReLu|ReLU]]__ ha notevolmente migliorato il training dei modelli profondi, in quanto: Propaga gradienti significativi attraverso la rete la [[Derivate|derivata]] è o $0$ o $1$ e non soffre di saturazione per valori positivi.

Tuttavia, la funzione __ReLU__ può avere problemi con i **neuroni morenti** (Dead Neurons), ovvero quando i valori negativi producono gradienti nulli. Varianti come __[[Funzione di attivazione - LeakyReLu|Leaky ReLU]]__ e __[[Funzione di attivazione - ELU|ELU]]__ sono state sviluppate per mitigare questo problema.


## Altre Tecniche per Stabilizzare l'Allenamento

altre tecniche che aiutano sono
- **Weight Initialization**: Tecniche come **Xavier (Glorot) Initialization** e **He Initialization** aiutano a mantenere valori iniziali dei pesi che prevengono gradienti troppo piccoli o troppo grandi.
- **Batch Normalization**: Normalizza gli input di ciascuno strato durante il training, riducendo la covariate shift e migliorando la propagazione del gradiente.
- **Optimizer Avanzati**: Algoritmi come **Adam**, **RMSprop** e **Momentum-based SGD** aiutano a stabilizzare l’aggiornamento dei pesi.
