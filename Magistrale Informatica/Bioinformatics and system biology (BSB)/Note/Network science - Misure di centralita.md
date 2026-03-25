---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# network science - misure di centralita
---
Le **misure di centralità** sono concetti della [[Network Science|network science]] usati per quantificare l'importanza topologica dei nodi all'interno di una rete. L'idea generale è che un nodo possa essere rilevante per ragioni diverse: perché ha molte connessioni, perché è vicino a molti altri nodi, perché collega [[Network Science - Community o moduli|moduli]] distinti oppure perché è connesso a nodi già molto influenti.

## Degree centrality
La **degree centrality** misura il numero di connessioni dirette di un nodo:
$$C_D(v)=k_v$$
In una rete non orientata coincide con il grado del nodo, mentre nelle reti orientate si può distinguere tra **in-degree** e **out-degree**.

È una misura locale e semplice da interpretare:
- identifica nodi altamente interattivi;
- evidenzia possibili **hub**;
- non descrive però il ruolo del nodo nella struttura globale della rete.

Un nodo può infatti avere molte connessioni ma trovarsi in una regione periferica del network, senza avere un ruolo centrale nella comunicazione tra moduli.

## Closeness centrality
La **closeness centrality** misura quanto rapidamente un nodo può raggiungere tutti gli altri nodi della rete:
$$C_C(v)=\frac{N-1}{\sum_u d(v,u)}$$
dove $d(v,u)$ è la distanza minima tra i nodi.

Un nodo con alta closeness:
- si trova mediamente vicino agli altri nodi;
- può diffondere rapidamente informazione o segnali;
- tende a occupare una posizione favorevole rispetto alla struttura complessiva della rete.

Questa misura è particolarmente utile quando interessa la velocità di accesso o di trasmissione, ma è sensibile alla presenza di componenti sconnesse o di regioni scarsamente collegate.

## Betweenness centrality
La **betweenness centrality** misura quanto frequentemente un nodo compare nei cammini minimi tra coppie di altri nodi:
$$C_B(v)=\sum_{s\neq v\neq t}\frac{\sigma_{st}(v)}{\sigma_{st}}$$
dove:
- $\sigma_{st}$ è il numero di cammini minimi tra $s$ e $t$;
- $\sigma_{st}(v)$ è il numero di tali cammini che passano per $v$.

Questa misura individua nodi che fungono da **ponti topologici** tra regioni differenti della rete. Un nodo può avere grado modesto ma betweenness elevata se collega moduli funzionali distinti.

In ambito biologico questi nodi sono spesso interpretati come:
- **bottleneck**;
- mediatori della comunicazione tra processi diversi;
- elementi critici la cui rimozione può frammentare la rete o alterare il flusso di informazione.

## Eigenvector centrality
L'**eigenvector centrality** assegna importanza ai nodi connessi ad altri nodi importanti. Se $x_i$ è l'importanza del nodo $i$, vale:
$$Ax=\lambda x$$
dove $A$ è la matrice di adiacenza e $x$ l'autovettore principale.

L'idea è che non tutte le connessioni abbiano lo stesso valore: essere collegati a nodi molto centrali pesa di più che essere collegati a nodi marginali. Questa misura è quindi più globale della degree centrality e cattura l'influenza topologica indiretta.

Una variante nota è il **PageRank**, interpretabile come un **random walk con restart**, che introduce un fattore di teletrasporto per rendere la misura più robusta.

## Interpretazione biologica
Nelle reti biologiche, centralità diverse mettono in evidenza ruoli diversi:
- alta **degree centrality**: possibili hub molecolari;
- alta **betweenness centrality**: nodi ponte tra moduli;
- alta **closeness centrality**: nodi ben posizionati per raggiungere rapidamente il resto della rete;
- alta **eigenvector centrality**: nodi inseriti in regioni globalmente influenti.

Per questo motivo l'interpretazione biologica non dovrebbe mai basarsi su una sola misura isolata. In pratica si confrontano più centralità e si integrano con il contesto sperimentale, la qualità del network e il significato biologico delle interazioni.
