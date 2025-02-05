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
Le __Deep Neural Networks__ (DNN) sono una generalizzazione delle [[Reti neurali Feed-Forward (FF)|Multi-Layer Perceptron]] (MLP) con molteplici livelli di rappresentazione. La profondità della rete consente di apprendere rappresentazioni gerarchiche e distribuite dei dati.



grazie al [[Teorema di approssimazione universale|Teorema di approssimazione universale]]  una rete con un solo strato nascosto e teoricamente capace di approssimare qualsiasi funzione continua con una sufficiente quantitadi neuroni. Una rete con un solo strato nascosto è teoricamente capace di approssimare qualsiasi funzione continua con una sufficiente quantità di neuroni.
Tuttavia, un modello più profondo permette una rappresentazione più efficiente rispetto a una rete poco profonda con un numero esponenziale di neuroni.

- **Profondità vs. Efficienza:** Reti profonde richiedono meno unità rispetto a reti poco profonde per lo stesso compito.
- **Bias induttivo:** I modelli profondi sfruttano la struttura gerarchica intrinseca dei dati.
- **Implicazioni:** Le reti profonde sono alla base di avanzamenti in visione artificiale, NLP, e molte altre applicazioni.

##### No flattening results


#### Difficolta in fase di training

Nelle reti profonde, il calcolo del gradiente lungo molti strati porta a problemi:

- **Vanishing Gradient:** Se i gradienti sono piccoli, la retropropagazione si arresta.
- **Exploding Gradient:** Se i gradienti sono grandi, l'aggiornamento dei pesi diventa instabile.

Soluzioni:

- **Uso di ReLU** invece di sigmoide/tanh.
- **Batch Normalization:** Normalizza l'attivazione degli strati intermedi.
- **Weight Initialization:** Tecniche come He o Xavier initialization.
- **Gradient Clipping:** Limita la grandezza dei gradienti.

#### Deep Learning e Rappresentazione Distribuita

Le reti profonde apprendono rappresentazioni distribuite:

- **Feature gerarchiche:** Dai bordi alle forme fino agli oggetti.
- **Word Embeddings:** Relazioni tra parole modellate da operazioni vettoriali: $$Rep(king)−Rep(male)+Rep(female)≈Rep(queen)\text{Rep}(\text{king}) - \text{Rep}(\text{male}) + \text{Rep}(\text{female}) \approx \text{Rep}(\text{queen})$$


#### Pre-training di un modello deep

1. **SGD con Momentum:** $vt=βvt−1+(1−β)∇J(θ)v_t = \beta v_{t-1} + (1 - \beta) \nabla J(\theta)$
2. **Adam Optimizer:** $mt=β1mt−1+(1−β1)gtm_t = \beta_1 m_{t-1} + (1 - \beta_1) g_t vt=β2vt−1+(1−β2)gt2v_t = \beta_2 v_{t-1} + (1 - \beta_2) g_t^2$
3. **Regularizzazione:**
    - Dropout: Disattivazione casuale di neuroni durante l'addestramento.
    - L2 weight decay: Penalizzazione dei pesi elevati.

