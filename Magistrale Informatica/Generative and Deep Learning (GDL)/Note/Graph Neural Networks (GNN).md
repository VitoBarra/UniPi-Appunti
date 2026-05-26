---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Deep Learning for Graph
topic: Graph Neural Networks
SubTopic:
---

# Graph Neural Networks (GNN)
Le **Graph Neural Networks (GNN)** sono modelli neurali progettati per [[Structural Domain Learning (SDL)|dati strutturati]] come [[Strutture Dati - Grafi|grafi]], in cui l'informazione non e contenuta solo nelle feature dei singoli nodi ma anche nella struttura delle relazioni. L'obiettivo e apprendere rappresentazioni di nodi, archi o grafi interi che integrino contenuto locale e contesto topologico.

Le **Graph Neural Networks (GNN)** costruiscono **embedding** contestuali propagando informazione lungo gli archi del grafo. Un nodo non viene quindi rappresentato isolatamente, ma come funzione delle proprie **feature**, del **proprio vicinato** e delle trasformazioni applicate ai **messaggi ricevuti**. Questo principio compare oggi soprattutto nella forma del [[z]] 

Le **Graph Neural Networks (GNN)** è un estensione delle [[Recurrent Neural Network (RNN)|reti neurali ricorrenti]] a domini strutturati con cicli. Nelle sequenze una RNN aggiorna lo stato corrente usando l'input corrente e uno stato precedente ben definito; in un grafo questa ipotesi non vale, perche un nodo puo dipendere da un vicino che dipende a sua volta dal nodo stesso. La presenza di cicli impedisce quindi un unfolding lineare del calcolo e obbliga a trattare l'encoding come una dinamica iterativa.
Le **Graph Neural Networks (GNN)** risolvono questo problema imponendo che la dinamica degli stati nodali converga a un **punto fisso**. L'idea e definire per ogni nodo uno stato latente che dipende sia dall'informazione locale sia dagli stati dei vicini, ma in modo tale che l'aggiornamento complessivo resti stabile anche in presenza di dipendenze reciproche.

Si introduce uno stato nodale $h(v)$, dove $v$ e il nodo considerato. Se $x(v)$ indica la feature del nodo, $N(v)$ il suo vicinato, $V$ la trasformazione applicata all'input locale e $W$ quella applicata agli stati dei vicini, formalmente si scrive$$h(v)=\tanh\left(Vx(v)+\sum_{v' \in N(v)}Wh(v')\right)$$
La formula rappresenta una mappa ricorrente su grafo: $Vx(v)$ codifica il contributo del nodo, mentre $\sum_{v' \in N(v)}Wh(v')$ aggrega l'effetto degli stati dei vicini. Operativamente, gli embedding nodali non si ottengono in un singolo forward pass, ma per iterazioni successive fino al raggiungimento di una configurazione stabile.

La proprieta decisiva e la **contrattivita**. Si richiede che la mappa di aggiornamento riduca progressivamente la distanza tra stati successivi, cosi da garantire convergenza della dinamica. Per definizione, se l'operatore e contrattivo, esiste un punto fisso stabile verso cui l'iterazione converge; questo inserisce il modello nel quadro dei [[Sistemi dinamici|sistemi dinamici]], dove diventano centrali nozioni come stabilita, convergenza e attrattori. Operativamente, il "ping-pong" tra nodi in dipendenza reciproca termina e l'inferenza diventa ben definita anche su grafi ciclici.

Il vantaggio del modello e l'aderenza naturale alla struttura ricorrente del grafo. Il limite e che durante l'addestramento i parametri devono restare in una regione che preservi la contrattivita, quindi dopo ogni aggiornamento dei pesi puo essere necessario riscalarli o correggerli. Inoltre anche in fase di inferenza la rete deve essere eseguita fino a convergenza. Il costo computazionale e quindi elevato, ma il modello conserva un bias ricorrente che puo generalizzare naturalmente da grafi piu piccoli a grafi piu grandi, analogamente a quanto accade con le RNN quando si passa a sequenze piu lunghe.

Questo permette alla rate di funzionare **indipendentemente** dalla dimensione del grafo esattamente come le RNN possono funzionare con sequenze di lunghezza arbitraria
![[IMG - approccio contrattivo - Graph Neural Networks (GNN).png]]
![[IMG - graph Dynamical System.png]]
