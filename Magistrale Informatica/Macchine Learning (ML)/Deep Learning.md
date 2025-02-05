---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Deep Learning
---
il __deep learning__ è la disciplina sotto categoria del [[Machine Learning (ML)|macchine learning]] che studia le __Deep Neural Networks__ (DNN) sono delle [[Reti Neurali (NN)|reti neurli]]  "profonde" ovvero dove i gli hidden layer sono molti.
una caso semplice per costruire una rete che rispetta il deep learning è una [[Reti neurali Feed-Forward (FF)|Multi-Layer Perceptron]] (MLP)  che ha un certo numero di hidden layer. 
![[Pasted image 20250205223357.png]]

Il __Deep learning__ ha un __bias induttivo__ dove assume che le funzioni che  [[Funzioni|funzione]] rappresenta siano per natura composizionali, ovvero sono della forma $$f(g(x))$$Questo avviene siccome ogni layer intermedio trasforma l'input in una rappresentazione a più alto livello ($g(x)$) che può essere usato dal successivo __come primitiva__ per costruirne una nuova ancora a più alto livello ($f(g(x))$) e cosi via fino al Output. 
questo processo è anche detto  __feature extraction__ e aiuta la capacita di generalizzazione di una rete neurale siccome evita alla rete il dover usare direttamente le [[Combinatoria|combinazioni]] degli input che sono per natura molto di piu rispetto alle primitive estratte.

questo __bias induttivo__ permette al __deep learning__ di affrontare il __curse of dimesionality__ infatti mentre altri modelli come il [[K-Nearest Neighbor (K-NN)|k-nn]] e gli [[alberi di decisione|alberi di decisione]] assumono una similarità locale  (local smoothnes prior) qui non c è questa necessita e infatti il __deep learning__ può generalizzazione anche __NON localmente__ 

![[Pasted image 20250205225036.png]]


le [[Reti Neurali (NN)|reti neurali]] del __deep learning__ *__NON__* sono più espressive rispetto alla sua controparte shallow questo grazie al [[Teorema di approssimazione universale|Teorema di approssimazione universale]] che ci dice che ogni rete con almeno un hidden layer può approssimare arbitrariamente bene qualsiasi funzione, ma non specifica nessun bound sul numero di unita necessarie per l approssimare. 
Per alcune famiglie di funzioni è possibile calcolare questo bound. 

Tuttavia, un __modello deep__ può essere __più efficiente__ in termini di numero di parametri e unita nascoste rispetto ad un modello shallow. Infatti, esistono famiglie di funzioni per cui un modello con almeno $d$ layer può approssimarle in modo compatto, mentre modelli con meno di $d$ layer richiedono un numero  di neuroni rispetto esponenziale al numero di input.

Il **No-Flattening Theorem** afferma le funzioni di natura composizionale possono essere rappresentate in modo __efficiente__ da una __rete deep__, ma non possono essere rappresentate con la stessa efficienza se la rete viene appiattita a un solo hidden layer. 






#### Difficoltà in fase di training

Nelle reti profonde, il calcolo del gradiente lungo molti strati porta a problemi:

- **Vanishing Gradient:** Se i gradienti sono piccoli, la retropropagazione si arresta.
- **Exploding Gradient:** Se i gradienti sono grandi, l'aggiornamento dei pesi diventa instabile.

Soluzioni:

- **Uso di ReLU** invece di sigmoide/tanh.
- **Batch Normalization:** Normalizza l'attivazione degli strati intermedi.
- **Weight Initialization:** Tecniche come He o Xavier initialization.
- **Gradient Clipping:** Limita la grandezza dei gradienti.


