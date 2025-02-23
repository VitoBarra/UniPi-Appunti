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
Le **reti neurali convoluzionali (CNN)** sono un [[Modelli di machine learning parametrici|modello parametrico]] dell paradigma delle [[Reti Neurali (NN)|reti neurali]] allenate con [[Algoritmi di apprendimento supervisionato|algoritmi di apprendimento supervisionato]] particolarmente efficace per il riconoscimento di immagini e pattern, sono considerate come una generalizazione delle [[Input delay neural network (IDNN)|IDNN]] in 2D.

Si basano su tre principi chiave:
1. **Connessioni locali**: ogni neurone è connesso solo a una regione ristretta dell'input, riducendo la complessità computazionale.
2. **Pesi condivisi**: lo stesso filtro viene applicato a diverse parti dell'immagine, permettendo la rilevazione degli stessi pattern ovunque nel immagine dando l __invarianza per traslazione__.
3. **Pooling**: riduce la dimensionalità mantenendo le caratteristiche più significative, rendendo il modello più robusto a traslazioni.
	

## Convoluzione 2D
l operazione di [[Operazione di convoluzione|convoluzione]] è un'operazione fondamentale in una __CNN__. Il processo di convoluzione tra un'immagine $I$ e un filtro $K$ è definito come $$
S(i,j) = (I * K)(i,j) = \sum_m \sum_n I(m,n) K(i - m, j - n).
$$Questa forma è utilizzata in molte librerie di reti neurali (NN) per le CNN:$$
S(i,j) = (I * K)(i,j) = \sum_m \sum_n I(i + m, j + n) K(m, n).
$$Scritta nella forma di **cross-correlazione**.
Dove:
- $S(i,j)$ è l'output della convoluzione,
- $I(i-m, j-n)$ è il valore del pixel,
- $K(m,n)$ è il kernel (filtro) della convoluzione.
![[Pasted image 20250222232503.png]]
 Ovvero si fa L'uso di __[[filtering|filtri]]__. La dimensione della **feature map** dipende dall'applicazione dei filtri. In particolare, modificando lo **stride**, ovvero il passo con cui il filtro si sposta sull'immagine, è possibile controllare le dimensioni della **feature map** risultante. Con __stride__ $1$ e aggiungendo __padding__ sul bordo si ottiene una feature map della stessa dimensione del immagine originale   ![[Pasted image 20250222220623.png]]  mentre  un stride maggiore di $1$ riduce la dimensione dell'output, ad esempio con stride $2$ ![[Pasted image 20250222233822.png]]

## Pooling
il __Pooling__ è un operazione che riduce la __dimensionalità__ delle __feature map__ le caratteristiche più significative.

Quest operazione può essere considerato come un filtro ma invece di usare dei pesi fa un operazione specifica, si applica quindi il concetto di __stride__.

due tipi  comuni di pooling sono:
- __Max pooling__: seleziona il valore massimo in una finestra, mantenendo le caratteristiche più prominenti.
- __Average pooling__: calcola la media dei valori in una finestra, utile per ridurre il rumore.

![[Pasted image 20250222220840.png]]

Il __pooling__ aiuta a ridurre la dimensionalità dei dati da gestire e rendere il modello più robusto a piccole traslazioni.

## Architettura di una CNN
Una __CNN tipica__ è composta da:
1. __layer convoluzionali__ estraggono caratteristiche locali tramite filtri.
2. __layer pooling__: riducono la dimensionalità, migliorando l'efficienza computazionale.
3. __layer [[Reti neurali Feed-Forward (FF)|feed-forward]]__: elaborano le _feature map_ per produrre la classificazione.
![[Pasted image 20250222220903.png]]![[Pasted image 20250223010115.png]]
    
## GPU e Tensor Notation
Le operazioni di convoluzione e moltiplicazione di matrici sono computazionalmente costose, ma possono essere accelerate tramite **GPU** e l [[Inner Product|operazioni tra tensore]]

L'uso della notazione tensoriale permette di parallelizzare molte operazioni lineari, migliorando l'efficienza del training su dataset di grandi dimensioni.
![[Pasted image 20250222220955.png]]















