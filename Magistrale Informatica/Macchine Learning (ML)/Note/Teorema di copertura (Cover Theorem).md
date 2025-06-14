---
Course: "[[Machine Learning (ML)]]"
tags:
  - IIA
  - ML
Area: 
topic: 
SubTopic:
---
# Teorema di copertura (Cover Theorem)
---
Il **Cover's Theorem**, formulato da Thomas Cover, afferma che se si proietta un insieme di dati in uno spazio di dimensione più alta con una trasformazione non lineare, allora è più probabile che i dati diventino linearmente separabili. Questo concetto è alla base del funzionamento dei **kernel methods**, come il **Support Vector Machine (SVM) con kernel**.

Formalmente, supponiamo di avere un dataset $\mathcal{D} = \{ (\mathbf{x}_i, y_i) \}_{i=1}^{N}$ con $\mathbf{x}_i \in \mathbb{R}^d$ e $y_i \in \{-1, 1\}$. Se i punti non sono linearmente separabili nello spazio originale $\mathbb{R}^d$, possiamo mapparli in uno spazio di dimensione superiore $\mathbb{R}^D$ con una funzione non lineare $\phi: \mathbb{R}^d \to \mathbb{R}^D$, tale che la separabilità lineare sia più probabile:

$$
\mathbf{x} \mapsto \phi(\mathbf{x})
$$

L'idea chiave è che l'aumento della dimensionalità permette di trovare iperpiani di separazione con maggiore probabilità. In particolare, Cover mostrò che se lo spazio proiettato ha una **sufficientemente alta dimensionalità** e la trasformazione è abbastanza **complessa e non lineare**, allora i dati diventeranno linearmente separabili con probabilità elevata.

### Dimostrazione Intuitiva

Supponiamo che in $\mathbb{R}^d$ i dati siano distribuiti in modo che non possano essere separati da un iperpiano. Se applichiamo una trasformazione $\phi(\mathbf{x})$ che li mappa in $\mathbb{R}^D$ con $D \gg d$, esistono più gradi di libertà per separare i dati. La separabilità dipende dal numero di possibili iperpiani che possono essere costruiti nello spazio trasformato. Secondo la **teoria della capacità di separazione**, il numero di modi in cui un insieme di punti può essere separato da un iperpiano cresce con la dimensionalità dello spazio.

Un'analogia visiva è quella di un toro e un nodo: in $\mathbb{R}^2$ un nodo intrecciato non può essere sciolto senza spezzarlo, mentre in $\mathbb{R}^3$ può essere sciolto spostandolo lungo la dimensione aggiuntiva.

Matematicamente, se il numero di punti nel dataset è $N$ e lo spazio trasformato ha dimensione $D$, la probabilità di separabilità aumenta se $D$ è sufficientemente grande rispetto a $N$. Una condizione euristica è:

$$
D \gg \log N
$$

che suggerisce che anche una modesta crescita della dimensione dello spazio trasformato può aumentare significativamente la separabilità.


### Limiti del Teorema

Sebbene l'aumento della dimensionalità favorisca la separabilità, introduce anche problemi pratici:

1. **Overfitting**: In uno spazio di dimensione molto alta, un modello può diventare troppo complesso e adattarsi eccessivamente ai dati di training.
2. **Costo computazionale**: Lavorare con spazi ad alta dimensione è costoso in termini di memoria e tempo di calcolo, sebbene i kernel methods aiutino a mitigare questo problema.
3. **Curse of Dimensionality**: Un’eccessiva crescita della dimensione può portare a problemi come la dispersione dei punti e la scarsa generalizzazione.

In conclusione, il **Cover's Theorem** giustifica l'uso della proiezione non lineare per migliorare la separabilità dei dati, fornendo le basi teoriche per i metodi a kernel. Tuttavia, l’aumento della dimensionalità deve essere gestito con attenzione per evitare problemi pratici.
