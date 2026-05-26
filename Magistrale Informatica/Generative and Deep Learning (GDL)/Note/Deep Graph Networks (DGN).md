---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Deep Graph Networks
---

# Deep Graph Networks (DGN)
Le **Deep Graph Networks (DGN)** sono il quadro generale in cui si collocano molte architetture neurali per grafi. L'idea di base e che ogni nodo mantenga uno stato latente che viene aggiornato layer dopo layer usando il proprio contenuto, la struttura del grafo e le rappresentazioni dei nodi vicini. In questo senso le DGN costituiscono una formalizzazione del caso dei [[Graph Theory|grafi]] nello [[Structural Domain Learning (SDL)|structural domain learning]] e una forma specifica di [[Rappresentazione simbolica e distribuita dei concetti|representation learning]] su domini relazionali.

![[IMG - Deep Graph Networks.png]]

Le **Deep Graph Networks (DGN)** sono inoltre strettamente legate alle [[Convolutional Neural Network (CNN)|CNN]], non nel senso che una famiglia sia una sottoclasse dell'altra, ma nel senso che riusano le stesse idee strutturali in un dominio diverso. Le CNN lavorano su griglie regolari e sfruttano localita, weight sharing, crescita gerarchica del campo recettivo e, spesso, pooling; le DGN trasferiscono queste idee ai grafi, dove pero il vicinato non e regolare e la nozione di convoluzione non puo essere implementata come semplice scorrimento di un filtro su una griglia.

In questa lettura una DGN puo essere vista come un'architettura composta da blocchi locali di propagazione, eventuali meccanismi di contrazione o pooling e un readout finale, in stretta analogia con la struttura generale delle CNN ma con operatori adattati ai grafi. L'immagine seguente rende visibile proprio questa parentela architetturale: una sequenza di blocchi locali costruisce rappresentazioni nodali sempre piu contestuali, eventuali operazioni di pooling modificano la scala della struttura e il readout finale produce l'output desiderato. ![[IMG - Deep GraphNetworks architettura completa.png]]

Da questo quadro generale discendono poi i meccanismi specifici. Il [[Meccanismo del message passing]] implementa la forma grafica di una "convoluzione" locale, perche aggiorna ogni nodo usando il proprio intorno; il pooling realizza invece il passaggio a rappresentazioni piu compatte e gerarchiche, analogamente a quanto avviene nelle CNN, ma senza poter contare su una geometria regolare.

## Problema strutturale
Le **Deep Graph Networks (DGN)** nascono da un vincolo molto semplice ma decisivo: in un grafo non posso in generale identificare o ordinare i vicini di un nodo in modo consistente. Se non posso ordinare il vicinato, non posso neppure decidere di assegnare a un vicino il "primo peso", a un altro il "secondo peso" e cosi via, come accade in una griglia regolare. La soluzione e quindi forzare una forma di **democrazia parametrica**: i vicini vengono trattati con pesi condivisi, e la differenza non e data dalla posizione nel vicinato ma dal contenuto dei messaggi che portano.

Questo e il motivo per cui nelle DGN compare naturalmente il **weight sharing** tra nodi e tra vicinati. L'operatore locale non puo dipendere dall'ordine con cui i messaggi arrivano dal **[[MultiInsieme|multinsieme]]** dei messaggi ricevuti. Il layer neurale deve quindi essere in grado di elaborare input a cardinalita variabile e non ordinati.




## Meccanismo del message passing
Le **Deep Graph Networks (DGN)** implementano questo vincolo tramite il **Meccanismo del message passing**. Ogni layer e un round locale di comunicazione: il nodo $v$ riceve messaggi dai nodi del proprio vicinato $\mathcal{N}_v$, li aggrega con una funzione invariante alla permutazione e usa il risultato per aggiornare il proprio stato.

Se $h_v^{(\ell)}$ indica lo stato del nodo $v$ al layer $\ell$, una formulazione astratta molto generale si scrive$$
h_v^{(\ell+1)}=\phi^{\ell+1}\left(h_v^\ell,\Psi\left(\left\{\psi^{\ell+1}(h_u^\ell)\mid u \in \mathcal{N}_v\right\}\right)\right)
$$dove $\psi^{\ell+1}$ trasforma i messaggi dei vicini, $\Psi$ li aggrega con un operatore permutation invariant e $\phi^{\ell+1}$ combina il risultato con lo stato corrente del nodo. La formula rappresenta uno schema generale: prima si trasformano i messaggi, poi si aggregano in modo compatibile con il vicinato non ordinato, infine si aggiorna lo stato del nodo. Operativamente, moltissimi modelli della letteratura possono essere letti come istanziazioni diverse di questa struttura, cambiando la forma di $\psi$, di $\Psi$ e di $\phi$.

Una formulazione equivalente, piu sintetica, esplicita prima il messaggio aggregato$$
m_v^{(k)}=\mathrm{AGG}\left(\{h_u^{(k)}:u \in \mathcal{N}(v)\}\right)
$$e poi l'aggiornamento$$
h_v^{(k+1)}=\mathrm{UPDATE}\left(h_v^{(k)},m_v^{(k)}\right).
$$Qui `AGG` e `UPDATE` sono i blocchi fondamentali del modello: la prima formula sintetizza il vicinato, la seconda costruisce il nuovo embedding del nodo.
![[IMG - Graph message passing.png]]
Le **Deep Graph Networks (DGN)** scambiano messaggi solo localmente, ma ottengono un effetto globale. Al primo layer un nodo usa informazione dei vicini diretti; al secondo layer usa stati che contengono gia informazione proveniente dai vicini dei vicini; continuando, il suo **receptive field** cresce con la profondita. In termini di comunicazione, ogni layer e un round locale, ma piu round permettono la diffusione dell'informazione su regioni sempre piu ampie del grafo; e proprio per questo una computazione puramente locale puo produrre una rappresentazione che riflette proprieta globali del grafo.
```pseudo
	\begin{algorithm}
	\caption{Simple message-passing neural network}
	\begin{algorithmic}
	\STATE \textbf{Input:} grafo non orientato $G=(V,E)$
	\STATE \textbf{Input:} embedding nodali iniziali $\{h_n^{(0)}=x_n\}$
	\STATE \textbf{Input:} funzione $\mathrm{Aggregate}(\cdot)$
	\STATE \textbf{Input:} funzione $\mathrm{Update}(\cdot)$
	\STATE \textbf{Output:} embedding nodali finali $\{h_n^{(L)}\}$
	\FOR{$\ell=0,\dots,L-1$}
		\STATE $z_n^{(\ell)} \leftarrow \mathrm{Aggregate}\left(\{h_m^{(\ell)}: m \in \mathcal{N}(n)\}\right)$
		\STATE $h_n^{(\ell+1)} \leftarrow \mathrm{Update}\left(h_n^{(\ell)},z_n^{(\ell)}\right)$
	\ENDFOR
	\STATE \textbf{return} $\{h_n^{(L)}\}$
	\end{algorithmic}
	\end{algorithm}
```
Lo stesso meccanismo puo quindi essere letto in forma algoritmica: ogni iterazione del ciclo sui layer e un round di comunicazione in cui prima si sintetizza il contesto locale del nodo e poi si aggiorna il suo embedding usando insieme stato corrente e vicinato aggregato.

Le **Deep Graph Networks (DGN)** richiedono inoltre che l'aggregatore lavori su [[MultiInsieme|multinsiemi]] di cardinalita variabile. Se un nodo ha uno, tre o venti vicini, il layer deve comunque produrre un output della stessa dimensione. Per questo si usano operatori come somma, media o massimo. Questi operatori non sono equivalenti dal punto di vista espressivo: la somma preserva la molteplicita delle occorrenze, mentre media e massimo possono collassare multinsiemi distinti nello stesso output. Operativamente, la scelta di `AGG` determina quanta struttura locale il modello riesce a distinguere.
![[IMG - message passing congregatore a dimensoine variabile.png]]
Il **Meccanismo del message passing** puo essere reso piu flessibile introducendo un peso specifico per ciascun messaggio ricevuto. Se $\alpha_{vj}$ misura quanto il nodo $v$ deve attendere al vicino $j$, una forma tipica dell'aggregazione diventa$$
h_v^{(l)}=\sum_{j \in N(v)} \alpha_{vj}W h_j^{(l-1)}.
$$Qui $W$ trasforma il messaggio del vicino e $\alpha_{vj}$ ne controlla la rilevanza; operativamente, l'aggregatore non tratta piu tutti i vicini nello stesso modo, ma costruisce una sintesi pesata del vicinato. In questa lettura l'attenzione non sostituisce il message passing: ne costituisce una specifica istanziazione in cui `AGG` diventa adattiva e dipendente dal contenuto dei messaggi. Le versioni multi-head ripetono questa operazione in piu sottospazi e permettono pesature differenti sullo stesso intorno, in analogia con il [[Meccanismo Self-Attention|meccanismo di self-attention]]. Questa famiglia e trattata piu direttamente in [[Graph Attention Network]]. ![[IMG - graph self-attension.png]]

La differenza emerge chiaramente quando il task richiede di **contare** configurazioni locali. Con `max` si seleziona solo il vicino dominante e si perde informazione sulla numerosita; con `mean` l'informazione viene normalizzata rispetto al numero di vicini, quindi non e piu possibile distinguere multisets che hanno la stessa media ma cardinalita diversa; con `sum`, invece, le occorrenze si accumulano e il modello puo rappresentare differenze strutturali che dipendono proprio dal numero di vicini o di pattern locali presenti. In domini come la chimica questa distinzione e cruciale, perche strutture locali diverse possono corrispondere a proprieta funzionali diverse.

Questo e il punto messo in evidenza dalla **Graph Isomorphism Network**, spesso riassunta con l'idea che "sum is better". Il risultato collega l'espressivita delle GNN al test di isomorfismo di **Weisfeiler-Lehman**: la scelta della funzione di aggregazione influenza direttamente quali strutture il modello riesce a separare. Una formulazione tipica del layer e$$
h_v^{(k)}=\mathrm{MLP}^{(k)}\left((1+\epsilon^{(k)})\cdot h_v^{(k-1)}+\sum_{u \in \mathcal{N}(v)} h_u^{(k-1)}\right)
$$
dove $h_v^{(k)}$ e lo stato del nodo $v$ al layer $k$, $\epsilon^{(k)}$ regola il peso del contributo auto-riferito e l'`MLP` realizza la trasformazione non lineare finale. Per un embedding di grafo si usa poi un readout sui nodi a tutti i layer, formalmente$$
h_G=\mathrm{CONCAT}\left(\mathrm{READOUT}\left(\{h_v^{(k)} \mid v \in G\}\right)\mid k=0,\dots,K\right).
$$Il significato operativo e che il modello somma i messaggi del vicinato invece di mediare o selezionare, massimizzando la capacita di distinguere strutture compatibile con il limite del test di Weisfeiler-Lehman di primo ordine.

Le **Deep Graph Networks (DGN)** possono emettere un output per ciascun nodo oppure un output per l'intero grafo. Nel primo caso si usa direttamente lo stato finale $h_v^{(L)}$ del nodo; nel secondo si applica una funzione di aggregazione globale sulle rappresentazioni nodali, cioe un readout di livello grafo. La stessa dinamica locale puo quindi supportare task diversi cambiando il livello su cui si applica la predizione.

![[IMG - message passing su grafi di diverso tipi.png]]


## Pooling
Le **Deep Graph Networks (DGN)** possono incorporare anche operazioni di **pooling**, in stretta analogia con le [[Convolutional Neural Network (CNN)|CNN]], ma adattate alla struttura di un grafo. L'idea e ridurre progressivamente la dimensione della rappresentazione costruendo una versione piu compatta del grafo, in cui nodi o gruppi di nodi vengano contratti in super-nodi. Operativamente, il pooling introduce un livello di astrazione piu alto e accorcia le distanze effettive tra regioni del grafo, cosi che il [[Meccanismo del message passing]] possa diffondere informazione su porzioni piu ampie della struttura con meno layer.

In termini strutturali, il pooling sui grafi e un problema di **coarsening**: si vuole costruire un grafo piu piccolo che preservi, almeno in parte, proprieta rilevanti del grafo originale. Una possibilita e identificare comunità o cluster di nodi e sostituirli con un super-nodo; in questo caso il problema centrale diventa stabilire quale nozione di comunità sia significativa per il task. Esistono approcci di tipo grafoteorico che forniscono anche garanzie sul mantenimento di proprieta come distanze, componenti connesse o altre caratteristiche globali della struttura.

Una seconda famiglia di approcci prova a rendere il pooling **differenziabile**, cioe a parametrizzare l'assegnazione dei nodi a gruppi e addestrarla con il resto della rete. Qui pero emerge un punto delicato: la riduzione discreta da $N$ nodi a un numero piu piccolo di super-nodi non e, in senso stretto, un'operazione differenziabile. Per questo molti metodi non realizzano una vera contrazione combinatoria del grafo, ma una proiezione continua che simula il pooling preservando la possibilita di propagare gradienti. Operativamente, questi metodi mantengono il vantaggio rappresentazionale dell'aggregazione gerarchica, ma non sempre portano un vero guadagno computazionale.

Una terza famiglia lavora invece sulle **graph signatures**, cioe costruisce matrici o rappresentazioni compatte degli stati nodali e ne estrae una struttura ridotta tramite fattorizzazioni o proiezioni a rango basso. Anche qui il senso del pooling non e solo ridurre dimensione, ma cambiare scala alla rappresentazione in modo che il grafo diventi piu gestibile dal punto di vista del routing dell'informazione.

Il pooling ha quindi una doppia funzione: da un lato aumenta l'astrazione, dall'altro puo accelerare la convergenza della diffusione informativa nel grafo. Il suo uso, tuttavia, non e universale: nei task strettamente nodali va introdotto con cautela, perche contrarre nodi significa anche modificare direttamente gli oggetti su cui si vuole predire.

![[IMG - pooling layer in DGN.png]]


# Training
come si traina dipende da che tipo di task si sta cercando di risolvere 
![[IMG - DGN training.png]]

## Ruolo come framework generale
Le **Deep Graph Networks (DGN)** non identificano un singolo modello, ma una famiglia di architetture. 
- [[Graph Neural Networks (GNN)]]
    - [[Graph Echo State Network]] 
        - [[Deep Reservoirs for Graphs]]
- [[Graph Convolutional Network (GCN)]]
- [[Contextual Neural Networks for Graphs (NN4G)]]
 possono essere letti come scelte diverse di messaggio, aggregazione, aggiornamento o raggio di comunicazione dentro questo schema generale.

## Proprieta chiave
- il vicinato non ordinabile impone weight sharing e aggregazione permutation invariant
- il message passing e il meccanismo centrale che traduce struttura in computazione neurale
- molti modelli diversi si ottengono come istanziazioni della stessa formula generale
- comunicazione locale iterata produce diffusione globale dell'informazione
- il livello di readout determina se l'output e nodale o globale
