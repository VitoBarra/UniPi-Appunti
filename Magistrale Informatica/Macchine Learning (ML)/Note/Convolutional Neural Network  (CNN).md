---
Course: "[[Machine Learning (ML)]]"
Course 2: "[[Generative and Deep Learning (GDL)]]"
tags:
  - IIA
  - ML
  - GDL
Area:
topic:
SubTopic:
---
# Convolutional Neural Network (CNN)
---
Le **reti neurali convoluzionali (CNN)** sono un [[Modelli Parametrici|modello parametrico]] del paradigma delle [[Reti Neurali (NN)|reti neurali]], allenate con [[Algoritmi di learning supervisionato|algoritmi di apprendimento supervisionato]]. Sono particolarmente adatte a dati con struttura spaziale, soprattutto immagini, e dal punto di vista strutturale possono essere viste come l'estensione bidimensionale delle [[Time delay neural network (TDNN)|TDNN]], cioè delle cosiddette **CNN 1D**.

I dati naturali per questa rete sono quindi le sequenze 2D, cioè le immagini. In un'immagine i pixel vicini sono spesso correlati e, considerati insieme, formano bordi, texture e strutture locali che hanno significato solo quando vengono lette nel loro contesto.
![[IMG - correlazione locale tra pixel.png]]
Un'altra proprietà importante delle immagini è che un oggetto rimane lo stesso anche se cambia posizione. Questa è detta **invarianza traslazionale**: se un pattern si sposta nell'immagine, il suo significato non cambia.
![[IMG - invarianza traslazionale.png]]

Una [[Reti neurali Feed-Forward (FF)|rete completamente connessa]] tratta invece l'immagine come un vettore piatto. In questo modo perde l'organizzazione spaziale dei pixel e non sfrutta direttamente il fatto che lo stesso pattern possa comparire in posizioni diverse. Di conseguenza, la rete è costretta a imparare pesi diversi per riconoscere configurazioni simili in punti diversi dell'immagine, con un costo molto elevato in termini di parametri.

Le **CNN** costruiscono il proprio **[[Algoritmi di Machine Learning|inductive bias]]** attorno a queste proprietà dei dati e sono generalmente composte da:
- **convolutional layer**: applicano piccoli filtri locali all'immagine, così da sfruttare la correlazione spaziale tra pixel vicini. Gli stessi pesi del filtro vengono riutilizzati in tutte le posizioni (**weight sharing**), riducendo il numero di parametri e permettendo di rilevare lo stesso pattern in punti diversi dell'input.
- **pooling layer**: riducono la dimensionalità delle feature map e rendono la rappresentazione meno sensibile a piccole traslazioni.
La struttura dei **convolutional layer** sfrutta quindi la località dell'informazione, mentre il **weight sharing** permette di riconoscere lo stesso pattern anche quando compare in posizioni diverse. Per questo la convoluzione produce una rappresentazione **equivariante alla traslazione**: se il pattern si sposta, anche la risposta del filtro si sposta in modo coerente. Una maggiore **invarianza** alla posizione emerge invece dopo operazioni di aggregazione come il **pooling**.

In fondo alla rete sono spesso presenti layer [[Reti neurali Feed-Forward (FF)|feed-forward densi]], che usano le feature estratte dagli altri layer per costruire un output adatto al task.

La struttura finale risulta come
![[IMG - Struttura CNN.png]]

## Convolutional layer
I **convolutional layer** in una **CNN** eseguono l'[[Operazione di convoluzione|operazione di convoluzione 2D]]: un piccolo __filtro__ o __kernel__ scorre localmente sull'immagine e produce una nuova matrice detta __feature map__. Ogni valore della feature map misura quanto il pattern descritto dai pesi del filtro è presente in una certa regione dell'input. Fissati i pesi del kernel, la convoluzione è quindi un **operatore lineare**: ogni valore in output è ottenuto come combinazione lineare dei valori dell'input nella finestra osservata.

Nelle librerie di **deep learning** l'operazione implementata è in genere:
$$
S(i,j) = \sum_m \sum_n I(i + m, j + n) K(m,n)
$$
Formalmente questa scrittura è una **cross-correlazione**, perché il kernel non viene ribaltato. Nel linguaggio delle CNN, però, si parla comunque di convoluzione, perché il ruolo del layer resta lo stesso: estrarre caratteristiche locali tramite filtri appresi durante il training.

Se l'immagine è in scala di grigi, il filtro è bidimensionale. In questo caso l'input ha un solo canale e ogni valore dell'output si ottiene combinando localmente i pixel contenuti nella finestra coperta dal filtro.
![[IMG - Convuluzione immagine gray scale.png]]

Se invece l'input è a colori, l'immagine ha più canali, ad esempio __RGB__. Il filtro deve quindi avere una profondità compatibile con l'input: per esempio, un kernel $5 \times 5$ applicato a un'immagine RGB ha dimensione $5 \times 5 \times 3$. Il filtro osserva simultaneamente tutti i canali e produce comunque __un solo valore per posizione__, ottenuto sommando i contributi delle diverse slice del kernel.
![[IMG - convoluzione si immaigne a colori con 3 canali.png]]

Nel caso generale si parla quindi di __convoluzione multi-canale__: ogni filtro ha una profondità pari al numero di canali in ingresso e produce una singola feature map, mentre più filtri in parallelo producono i diversi canali del layer successivo. Per la definizione matematica generale della convoluzione e per il ruolo di __padding__ e __stride__ si veda [[Operazione di convoluzione]].
![[IMG - convoluzione multi canale.png]]

Se in uno strato convoluzionale si usano più filtri diversi, per esempio $D_K$ filtri, l'output non è una sola immagine ma un blocco di __$D_K$ feature map__, una per filtro. L'uscita di uno strato convoluzionale è quindi un tensore con due dimensioni spaziali e una dimensione di canale.

Dopo la convoluzione si applica in genere una funzione di attivazione elemento per elemento, ottenendo una __transformed feature map__. In questo modo la rete non si limita a una trasformazione lineare dell'input, ma introduce la non linearità necessaria per costruire rappresentazioni via via più espressive nei layer successivi.

![[IMG - trasformazione feature map.png]]

Comunemente, per motivi di stabilità del learning, la [[Funzioni di attivazione|funzione di attivazione]] usata è la [[Funzione di attivazione - ReLu|ReLU]].

## Pooling layer
Dopo la convoluzione e la [[Funzioni di attivazione|funzione di attivazione]], spesso si introduce un'operazione di __pooling__. Il pooling riduce la __dimensionalità__ delle __feature map__ applicando una funzione fissa su piccole finestre locali, quindi non usa pesi appresi come la convoluzione.

Anche nel pooling compare il concetto di __stride__, che controlla di quanto la finestra viene spostata a ogni passo. Riducendo la risoluzione spaziale delle feature map, il pooling abbassa il costo computazionale dei layer successivi e rende la rappresentazione meno sensibile a piccole traslazioni dell'input.

Le forme più comuni sono:
- __Max pooling__: seleziona il valore massimo nella finestra, conservando la risposta più intensa.
![[IMG - Max pooling.png]]
- __Average pooling__: calcola la media dei valori nella finestra, producendo una rappresentazione più smussata.
- __L2-norm pooling__: aggrega i valori della finestra tramite la loro [[Norme Matriciali e Norme Vettoriali|norma euclidea]], dando più peso alle attivazioni grandi ma tenendo conto anche delle altre.
- __Random pooling__: seleziona casualmente un valore nella finestra secondo una distribuzione che favorisce le attivazioni più alte, introducendo una componente stocastica.

L'idea centrale è che si perde dettaglio fine, ma si conserva l'informazione più utile per i layer successivi. In particolare, il pooling spaziale introduce una certa __invarianza locale alla traslazione__: se una feature si sposta leggermente all'interno della finestra, l'output può rimanere simile, soprattutto nel caso del max pooling.

Il pooling può essere applicato non solo nello spazio ma anche __tra canali__. Questo è il caso del __cross-channel pooling__, in cui si aggregano, nella stessa posizione spaziale, le attivazioni provenienti da canali diversi. È utile quando filtri distinti riconoscono varianti dello stesso pattern, per esempio la stessa cifra con orientazioni diverse: invece di mantenere separatamente le diverse feature map, si può combinare la loro risposta in un'unica mappa che segnala la presenza del pattern indipendentemente dalla variante che lo ha attivato.
![[IMG - Cross channel pooling.png]]
In questo senso, mentre il pooling spaziale favorisce soprattutto l'invarianza alla traslazione, il cross-channel pooling può favorire anche invarianza rispetto ad altre trasformazioni, come orientazione, scala o colore, a seconda di come sono organizzati i filtri. In generale, il tipo di pooling scelto determina rispetto a quali variazioni la rappresentazione diventa più stabile.


Una regola generale è che la dimensione delle featuremap a cui si applica uno pooling è $$W' =  \cfrac{W -K}{S} + 1$$

#### CNN viste come feed-forward
Una **CNN** può essere vista come una [[Reti neurali Feed-Forward (FF)|rete feed-forward]] con **connettività sparsa** e **pesi condivisi**. Per visualizzare meglio questa struttura, è utile considerare prima il caso 1D: un neurone convoluzionale con kernel di ampiezza 3 non è connesso a tutto l'input, ma solo a tre elementi adiacenti. La convoluzione può quindi essere letta come un layer sparso, in cui ogni neurone riceve input solo da una piccola finestra locale.
![[IMG - CNN come FF.png]]

La seconda proprietà chiave è il **weight sharing**. Se il kernel ha tre pesi, gli stessi tre pesi vengono riutilizzati in tutte le posizioni della sequenza o dell'immagine. In questo senso, la convoluzione equivale alla replica dello stesso piccolo insieme di parametri su un pattern di connessioni sparse, invece che all'uso di pesi distinti per ogni neurone del layer.

Lo **stride** rende questa struttura ancora più sparsa: invece di calcolare un output in ogni posizione, il filtro viene applicato saltando alcune posizioni. Di conseguenza si ottengono meno neuroni in uscita e una rappresentazione più compatta.
![[IMG - CNN as FF stride.png]]

Quando si impilano più layer convoluzionali, ogni neurone dei layer profondi dipende indirettamente da una porzione sempre più ampia dell'input originale. In altre parole, aumenta il **campo recettivo** (*receptive field*): i primi layer catturano pattern locali semplici, mentre quelli successivi combinano queste informazioni in strutture via via più complesse.
![[IMG - receptive fiedl CNN 1D.png]]

Il **padding** modifica il modo in cui questo campo recettivo si distribuisce lungo i bordi dell'input e permette di controllare meglio la dimensione delle feature map nei vari layer.
![[IMG - CNN receptive field con padding.png]]

## Backpropagation e transpose convolution
Una convoluzione discreta può essere vista come un'operazione lineare e quindi come una moltiplicazione matrice-vettore. Se si vettorizza l'input $x$, l'uscita di uno strato convoluzionale può essere scritta come:
$$
y = Wx
$$
dove $W$ è una matrice molto sparsa, costruita replicando gli stessi pesi del kernel nelle posizioni compatibili con la connettività locale e con lo stride.

In questa forma, la [[Back Propagation|backpropagation]] non cambia concettualmente rispetto a un layer denso: il gradiente rispetto all'input si ottiene applicando la matrice trasposta,
$$
\frac{\partial L}{\partial x} = W^T \frac{\partial L}{\partial y}
$$
mentre il gradiente rispetto ai pesi condivisi si ottiene sommando i contributi provenienti da tutte le posizioni in cui il kernel è stato riutilizzato.

ad esempio la convoluzione
![[IMG - convoluzione esempio.png]]
puo essere rappresentata dalla matrice $$
W =
\begin{pmatrix}
w_{0,0} & w_{0,1} & w_{0,2} & 0 & w_{1,0} & w_{1,1} & w_{1,2} & 0 & w_{2,0} & w_{2,1} & w_{2,2} & 0 & 0 & 0 & 0 & 0 \\
0 & w_{0,0} & w_{0,1} & w_{0,2} & 0 & w_{1,0} & w_{1,1} & w_{1,2} & 0 & w_{2,0} & w_{2,1} & w_{2,2} & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & w_{0,0} & w_{0,1} & w_{0,2} & 0 & w_{1,0} & w_{1,1} & w_{1,2} & 0 & w_{2,0} & w_{2,1} & w_{2,2} & 0 \\
0 & 0 & 0 & 0 & 0 & w_{0,0} & w_{0,1} & w_{0,2} & 0 & w_{1,0} & w_{1,1} & w_{1,2} & 0 & w_{2,0} & w_{2,1} & w_{2,2}
\end{pmatrix}
$$

La **transpose convolution** nasce proprio da questa osservazione: non è la vera inversa della convoluzione, ma l'operazione associata alla matrice trasposta $W^T$. Per questo viene usata per riportare un gradiente o una rappresentazione da uno spazio più piccolo a uno più grande, mantenendo la stessa struttura locale dell'operatore convoluzionale.

Se la convoluzione forward usa **stride maggiore di 1**, la matrice $W$ salta alcune posizioni dell'input. Di conseguenza, l'operatore trasposto corrispondente non può limitarsi ad applicare di nuovo il filtro: deve prima riespandere la rappresentazione intermedia. Operativamente questo si può vedere come un inserimento di zeri tra i campioni adiacenti e una successiva convoluzione con un padding coerente. In generale, con stride $s$, si inseriscono **$s-1$ zeri** tra due elementi consecutivi lungo ciascuna dimensione spaziale.

La transpose convolution viene quindi usata in due sensi strettamente collegati:
- durante la backpropagation di una convoluzione stridata, perché implementa in modo efficiente l'azione di $W^T$ senza materializzare esplicitamente la grande matrice sparsa;
- come layer di upsampling appreso, quando si vuole produrre un'uscita spazialmente più grande a partire da una feature map più piccola.

Nel secondo caso non si sta ricostruendo esattamente l'informazione persa dalla convoluzione precedente: l'operatore trasposto non annulla la convoluzione, ma distribuisce nello spazio l'informazione disponibile secondo pesi appresi.
