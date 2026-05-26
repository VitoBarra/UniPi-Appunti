---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - IIA
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Graph Convolutional Network
---

# Graph Convolutional Network (GCN)
La **Graph Convolutional Network (GCN)** nasce dal tentativo di definire una nozione di convoluzione per grafi analoga a quella usata nelle [[Convolutional Neural Network (CNN)|convolutional neural network]], ma adattata a domini non regolari. Il problema e che un grafo ha una struttura locale, quindi sembra naturale voler concentrare un filtro su un nodo e usare l'informazione dei nodi vicini; tuttavia questa operazione non e banale, perche un grafo non possiede in generale ne una griglia regolare ne un ordinamento canonico del vicinato.

## Due punti di vista
La **Graph Convolutional Network (GCN)** puo essere motivata da due prospettive. La prima e **spaziale**, in cui si cerca di definire la convoluzione direttamente nel dominio dei nodi, facendo giocare ai nodi il ruolo che i pixel hanno nelle immagini. La seconda e **spettrale**, in cui il grafo viene trattato come supporto di un segnale e la convoluzione viene definita nel dominio delle frequenze del grafo. In entrambi i casi l'obiettivo resta lo stesso: costruire un operatore locale che propaghi informazione sul grafo in modo condiviso tra i nodi.

## Formulazione spettrale
La **Graph Convolutional Network (GCN)** trova una prima formulazione pulita nel dominio spettrale. L'idea e che un grafo possa essere studiato dal punto di vista del segnale, non solo dal punto di vista combinatorio: i nodi costituiscono il dominio spaziale del segnale, ma il grafo ammette anche una nozione di frequenza ottenuta dalla decomposizione spettrale di un operatore associato al grafo, tipicamente il Laplaciano.

Se $f$ e il segnale nodale del grafo, $g$ un filtro, $U$ la base ortonormale degli autovettori del Laplaciano e $\lambda$ l'insieme degli autovalori associati, si definisce la convoluzione su grafo come
$$
(f *_G g)=\mathcal{F}^{-1}(\mathcal{F}(f)\mathcal{F}(g))=UW(\lambda)U^T f
$$
dove $\mathcal{F}$ rappresenta la trasformata di Fourier sul grafo, $\mathcal{F}^{-1}$ la trasformata inversa e $W(\lambda)$ il filtro parametrizzato nello spazio delle frequenze. La formula rappresenta il fatto che la convoluzione, difficile da definire direttamente nel dominio spaziale, diventa una moltiplicazione nel dominio spettrale; operativamente, si porta il segnale nel dominio delle frequenze tramite $U^T$, si applica il filtro spettrale $W(\lambda)$ e poi si torna nel dominio dei nodi tramite $U$.

Questa formulazione e teoricamente elegante, perche sfrutta strumenti di analisi spettrale ben definiti e rende la convoluzione una semplice composizione di moltiplicazioni matriciali. Il problema e che il filtro dipende esplicitamente dagli autovalori e dagli autovettori di uno specifico grafo. Se il dataset contiene piu grafi, ogni grafo ha in generale una propria decomposizione spettrale, quindi i parametri appresi su un grafo non si trasferiscono direttamente a un altro. Inoltre la decomposizione agli autovalori di matrici molto grandi rende la formulazione poco scalabile su grafi reali di grandi dimensioni.

## Limiti dell'analogo spaziale diretto
La **Graph Convolutional Network (GCN)** non puo essere ottenuta neppure come semplice trasposizione della convoluzione classica dalle immagini ai grafi. Nelle immagini un filtro $3 \times 3$ funziona perche il vicinato di ogni pixel e ordinato in modo coerente: ha senso parlare di elemento in alto a sinistra, a destra, in basso, e riusare gli stessi pesi spostando il filtro sulla griglia. In un grafo generale questo non vale.

Il vicinato di un nodo non e regolare e, soprattutto, non e ordinabile in modo consistente tra nodi diversi e tra grafi diversi. Se si volesse riusare un filtro come nelle CNN, bisognerebbe sapere quale vicino riceve il peso "in alto a sinistra", quale "in alto a destra" e cosi via; ma questa corrispondenza non esiste in generale. Cicli, assenza di orientamento canonico e mancanza di identita geometriche dei nodi impediscono di trasportare direttamente il bias spaziale classico delle immagini. Operativamente, la convoluzione su grafo richiede quindi un diverso bias induttivo rispetto a quello delle CNN standard.
![[IMG - immagini come grafi.png]]

## Interpretazione operativa
La **Graph Convolutional Network (GCN)** va quindi letta come una specifica famiglia di [[Graph Neural Networks (GNN)]] in cui la propagazione locale e motivata dalla nozione di convoluzione, ma implementata con operatori compatibili con la struttura irregolare del grafo. In questo senso la GCN si colloca nel quadro piu ampio del [[Deep Graph Networks (DGN)#Meccanismo del message passing|Meccanismo del message passing]]: ogni layer costruisce nuovi embedding nodali aggregando informazione dai vicini e ampliando progressivamente il campo recettivo del nodo.

Il significato pratico del modello e che la profondita della rete controlla quanta parte della struttura diventa accessibile alla rappresentazione del nodo. Pochi layer mantengono l'encoding molto locale; piu layer permettono di incorporare struttura piu ampia, ma introducono i limiti tipici della propagazione profonda sui grafi. La GCN e quindi importante non solo come modello specifico, ma come passaggio concettuale che mostra come la convoluzione debba essere reinterpretata quando il dominio non e una griglia ma un grafo.

![[IMG - GCN radius.png]]
![[IMG - GCN Percettiva Radius.png]]

## Proprieta chiave
- la convoluzione su grafo puo essere definita da un punto di vista spaziale o spettrale
- la formulazione spettrale usa la decomposizione del Laplaciano e la Fourier transform sul grafo
- i parametri spettrali dipendono dal grafo specifico e si trasferiscono male tra grafi diversi
- la convoluzione spaziale classica delle CNN non si applica direttamente ai grafi per mancanza di vicinati ordinati
- la GCN va letta come una forma strutturata di propagazione locale nel quadro delle GNN
