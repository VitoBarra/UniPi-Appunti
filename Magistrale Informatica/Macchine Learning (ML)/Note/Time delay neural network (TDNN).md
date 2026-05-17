---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area:
topic:
SubTopic:
---
# Time delay neural network (TDNN)
---
Le __Time delay neural network (TDNN)__ sono un tipo di [[Reti Neurali (NN)|rete neurale]] progettato per dati sequenziali. In senso generale il termine indica reti che usano __ritardi temporali espliciti__; in senso più specifico indica architetture che applicano lo stesso insieme di pesi a finestre temporali locali della sequenza, così da riconoscere lo stesso pattern anche quando compare in posizioni diverse nel tempo.

Se una sequenza è indicata con $x(t)$, una TDNN considera in ogni posizione una finestra locale, ad esempio $$[x(t), x(t-1), \dots, x(t-d)]$$ ma, a differenza di una [[Input delay neural network (IDNN)|IDNN]], non tratta questa finestra semplicemente come un vettore da dare in input a un layer generico. La struttura della rete è invece costruita in modo da far scorrere gli stessi pesi lungo tutta la sequenza.

In questo senso una TDNN può essere interpretata come un antecedente diretto delle __CNN 1D__. Se un filtro temporale ha coefficienti $w_0, w_1, \dots, w_d$, l'uscita in posizione $t$ può essere scritta come:
$$
y(t) = f\left( \sum_{k=0}^{d} w_k x(t-k) + b \right)
$$
Questa forma mette in evidenza due idee fondamentali:
- __località__: ogni output dipende solo da un intorno temporale limitato;
- __condivisione dei pesi__: gli stessi coefficienti vengono riutilizzati in tutte le posizioni della sequenza.

## Differenza rispetto alle IDNN

Le [[Input delay neural network (IDNN)|IDNN]] e le TDNN condividono l'uso di una finestra temporale fissa, ma il rapporto tra i due termini dipende dalla definizione adottata.

In un'accezione ampia, una __IDNN__ può essere considerata una forma semplice di TDNN, perché usa anch'essa ritardi espliciti in ingresso. Nella distinzione più stretta, però, nelle __IDNN__ la finestra di delay viene vista soprattutto come un modo per costruire un vettore di input esteso, che viene poi elaborato da una rete __feed-forward__ standard; nelle __TDNN__, invece, la condivisione dei pesi lungo il tempo è un principio architetturale esplicito, molto più vicino alla logica della convoluzione.

Per questo, quando il termine è usato in senso stretto, le TDNN sono di solito considerate più vicine alle [[Convolutional Neural Network (CNN)|CNN]] rispetto alle IDNN.

## Connessione con le CNN

Una [[Convolutional Neural Network (CNN)|CNN]] applicata a dati monodimensionali, come audio o serie temporali, usa filtri che scorrono lungo un solo asse. Da questo punto di vista, una __CNN 1D__ realizza in forma moderna la stessa idea strutturale delle TDNN.

Nel passaggio alle CNN la stessa logica viene poi estesa in modo naturale:
- si possono usare più filtri in parallelo;
- si possono comporre più layer per estrarre caratteristiche sempre più astratte;
- si possono introdurre __stride__, __padding__ e architetture più profonde.

Da questa linea evolutiva derivano anche le __Temporal Convolutional Networks (TCN)__, che usano convoluzioni 1D, spesso causali e dilatate, per modellare dipendenze temporali su scale più ampie.

