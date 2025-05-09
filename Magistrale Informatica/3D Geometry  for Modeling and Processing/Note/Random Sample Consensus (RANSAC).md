---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Random Sample Consensus (RANSAC)
---
Il **Random Sample Consensus (RANSAC)** è un metodo statistico robusto, concepito per stimare i parametri di un modello matematico a partire da un insieme di dati osservati che possono contenere un'alta percentuale di **outlier**. 

L'approccio di **RANSAC** si basa su un paradigma iterativo di tipo ***hypothesize-and-test***: si ipotizza un modello e lo si verifica rispetto ai dati. 

 si seleziona in modo casuale un sottoinsieme minimo di punti dal dataset originario, chiamato *ipotesi di inlier*, e si stima un modello utilizzando solo questi punti. Il modello così ottenuto viene poi testato contro tutti gli altri dati: ogni punto viene classificato come ***inlier*** o ***outlier*** a seconda che rispetti o meno una soglia di tolleranza rispetto al modello.

Un modello è considerato valido se riesce a spiegare un numero sufficiente di punti, cioè se il numero di inlier supera una certa soglia. In tal caso, il modello può essere ulteriormente raffinato stimando nuovamente i parametri, questa volta utilizzando l'intero insieme di inlier.

Questo approccio risulta efficace, ad esempio, nel caso di *line fitting* robusto. Se si tenta di adattare una retta a un dataset contenente molti outlier utilizzando metodi classici, come la minimizzazione dei minimi quadrati, gli outlier influenzano pesantemente la stima del modello, generando risultati poco rappresentativi dei dati effettivi. 
Invece, RANSAC riesce a individuare una retta che approssima correttamente la maggior parte dei punti buoni, ignorando gli **outlier** ![[IMG - RANSAC su linee.png]]
Dal punto di vista [[Definizione di Probabilita|probabilistico]], la forza di RANSAC risiede nella sua capacità di garantire, con alta probabilità, l'identificazione di un modello corretto in un numero limitato di iterazioni. Supponendo che $P$ sia la probabilità che un singolo punto sia un inlier, e che siano necessari $s$ punti per definire un'ipotesi di modello (ad esempio $s = 2$ per una retta), la probabilità che una singola iterazione scelga solo inlier è $P^s$. Di conseguenza, la probabilità che nessuna delle $N$ iterazioni scelga tutti inlier è:$$
(1 - P^s)^N
$$Pertanto, la probabilità che almeno una iterazione selezioni solo inlier (cioè che trovi un modello corretto) è:$$
1 - (1 - P^s)^N
$$Questa relazione consente di stimare il numero necessario di iterazioni $N$ per ottenere, con alta probabilità, un modello valido.


