---
Course: "[[Machine Learning (ML)]]"
tags:
  - IA
  - ML
Area: 
topic: 
SubTopic:
---
# Learning in Domini strutturati (SDL)
---
## Perché i dati strutturati e le reti?

I dati reali spesso non sono semplici vettori ma strutture complesse con relazioni intrinseche. I grafi sono una rappresentazione naturale per molteplici domini, tra cui:
- **Visione artificiale**: reti per la comprensione delle scene
- **Trasporti**: modelli predittivi del traffico
- **Social network**: modellazione delle interazioni tra utenti
- **Chimica**: rappresentazione di molecole per il drug design
- **Biologia**: reti proteiche e analisi del cervello
- **Linguistica**: parsing e knowledge graphs
Questi dati possono essere modellati con **reti neurali profonde (DGN - Deep Graph Networks)**, che generalizzano i modelli classici di deep learning ai grafi.

## Origini delle reti neurali per dati strutturati

L'uso di reti neurali per dati strutturati ha una forte impronta italiana, con ricerche dagli anni ‘90 sui seguenti approcci:
- **Reti neurali ricorsive** (1997-2000) per dati ad albero
- **Self-Organizing Maps per strutture** (2003-2005)
- **Tree Echo State Networks e Deep Reservoir Computing** (2010-2018)
- **Graph Neural Networks (GNN) e Graph Echo State Networks (GraphESN)** (2005-2010)
L’evoluzione delle reti neurali sui grafi ha portato alla nascita dei **Deep Graph Networks (DGN)**, che si sono diffusi globalmente a partire dal 2015.

## Rappresentazione dei grafi e apprendimento strutturato

Un nodo in un grafo è descritto da un vettore di caratteristiche . Gli archi tra i nodi hanno etichette che possono rappresentare distanze, connessioni logiche o altre proprietà.

L’apprendimento strutturato può essere visto come il problema di mappare i dati strutturati in uno spazio continuo: Dove è una funzione che trasforma la struttura in una rappresentazione utilizzabile per regressione o classificazione.

## Il concetto di Message Passing nei DGN

L’idea centrale dei DGN è il **Message Passing**, un processo iterativo che permette ai nodi di aggiornare il proprio stato in base alle informazioni ricevute dai vicini.

### Passaggi fondamentali:

1. Ogni nodo calcola un **messaggio** in base ai propri attributi e a quelli dei vicini
2. I nodi aggregano i messaggi ricevuti con una funzione invariante alla permutazione
3. Il nodo aggiorna il proprio stato combinando i messaggi con pesi liberi

L’iterazione del processo di Message Passing permette di diffondere l’informazione tra tutti i nodi del grafo.

## Problemi nei modelli di apprendimento su grafi

I DGN affrontano sfide significative, tra cui:

- **Over-smoothing**: con l’aumento della profondità, i nodi tendono a diventare indistinguibili
- **Over-squashing**: la capacità di rappresentare informazioni a lungo raggio diminuisce esponenzialmente con la profondità
- **Scalabilità**: addestrare reti profonde su grafi molto grandi è computazionalmente costoso
### Soluzioni proposte:

1. **Graph Echo State Networks (GESN)**: evitano il backpropagation completo e accelerano l’apprendimento
2. **NN4G+**: modelli che costruiscono architetture dinamicamente in modo efficiente
3. **Analisi spettrale**: studi per mantenere alta la variabilità spaziale delle rappresentazioni

## Applicazioni e sviluppi futuri

I DGN trovano applicazioni in molti ambiti, come:
- **Bioinformatica**: predizione di proprietà dinamiche nei percorsi biochimici
- **Chimica computazionale**: generazione di nuove molecole con reti generative
- **Spiegabilità dei modelli**: XAI per interpretare le decisioni delle reti neurali
- **Apprendimento continuo**: estensione delle DGN a contesti di lifelong learning

Le ricerche future mirano a **rendere più efficienti le DGN**, migliorando la loro scalabilità, interpretabilità e applicabilità a contesti dinamici.