---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Reti Neurali Convoluzionali (CNN)
---
Le **reti neurali convoluzionali (CNN)** sono un'architettura avanzata di reti neurali, particolarmente efficace per il riconoscimento di immagini e pattern. Si basano su tre principi chiave:

1. **Connessioni locali**: ogni neurone è connesso solo a una regione ristretta dell'input, riducendo la complessità computazionale.
2. **Pesi condivisi**: lo stesso filtro viene applicato a diverse parti dell'immagine, permettendo la rilevazione degli stessi pattern ovunque.
3. **Pooling**: riduce la dimensionalità mantenendo le caratteristiche più significative, rendendo il modello più robusto a traslazioni.

## Convoluzione

La convoluzione è un'operazione fondamentale in una CNN. Il processo di convoluzione tra un'immagine $I$ e un filtro $K$ si scrive come:

S(i,j)=∑m∑nI(i−m,j−n)K(m,n)S(i,j) = \sum_m \sum_n I(i-m, j-n) K(m,n)

Dove:

- $S(i,j)$ è l'output della convoluzione,
- $I(i-m, j-n)$ è il valore del pixel,
- $K(m,n)$ è il kernel (filtro) della convoluzione.

L'uso di filtri multipli consente di estrarre differenti caratteristiche dell'immagine, come bordi, texture e forme.

## Stride e Padding

- **Stride**: definisce il passo con cui il filtro si sposta sull'immagine. Un stride maggiore di 1 riduce la dimensione dell'output.
- **Padding**: aggiunta di pixel di bordo per mantenere le dimensioni dell'immagine dopo la convoluzione. Il **zero-padding** è comunemente utilizzato per evitare la perdita di informazioni ai bordi.

## Pooling

Operazione che riduce la dimensionalità della rappresentazione mantenendo le caratteristiche più significative. Tipi comuni:

- **Max pooling**: seleziona il valore massimo in una finestra, mantenendo le caratteristiche più prominenti.
- **Average pooling**: calcola la media dei valori in una finestra, utile per ridurre il rumore.

Il pooling aiuta a rendere il modello più robusto a traslazioni, riducendo la sensibilità a piccoli cambiamenti di posizione nelle immagini.

## Architettura di una CNN

Una CNN tipica è composta da:

1. **Strati convoluzionali**: estraggono caratteristiche locali tramite filtri.
    
2. **Strati di pooling**: riducono la dimensionalità, migliorando l'efficienza computazionale.
    
3. **Strati completamente connessi (FC)**: elaborano le feature map per produrre la classificazione.
    
4. **Funzione di attivazione**: ReLU (Rectified Linear Unit) è comunemente utilizzata per introdurre non-linearità:
    
    f(x)=max⁡(0,x)f(x) = \max(0, x)
    
    Questo aiuta a prevenire il problema della scomparsa del gradiente.
    

## LeNet e AlexNet

- **LeNet**: prima CNN sviluppata da LeCun per il riconoscimento di caratteri scritti a mano (MNIST). Composta da strati convoluzionali seguiti da livelli di pooling e uno strato FC finale.
- **AlexNet**: ha vinto la competizione ImageNet nel 2012, utilizzando più strati convoluzionali, dropout per prevenire overfitting e ReLU per velocizzare l'addestramento.

## Allenamento di una CNN

Il training di una CNN utilizza la **discesa del gradiente** con backpropagation. La funzione di costo comunemente utilizzata per la classificazione è l'entropia incrociata:

L=−∑iyilog⁡(y^i)L = -\sum_i y_i \log(\hat{y}_i)

Dove:

- $y_i$ è la classe vera,
- $\hat{y}_i$ è la probabilità predetta.

L'ottimizzazione avviene tramite algoritmi come Adam o SGD (Stochastic Gradient Descent), che aggiornano i pesi in base all'errore calcolato.

## GPU e Tensor Notation

Le operazioni di convoluzione e moltiplicazione di matrici sono computazionalmente costose, ma possono essere accelerate tramite **GPU**. I framework come TensorFlow utilizzano **tensordot** per ottimizzare le operazioni tra tensori.

L'uso della notazione tensoriale permette di parallelizzare molte operazioni lineari, migliorando l'efficienza del training su dataset di grandi dimensioni.

## Conclusione

Le CNN sono oggi alla base di molte applicazioni avanzate di visione artificiale e deep learning. L'evoluzione delle architetture ha portato a modelli più avanzati come **ResNet, VGG e Capsule Networks**. Grazie alle CNN, i sistemi di intelligenza artificiale possono riconoscere oggetti, volti e testi con elevata accuratezza.