---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Recurrent graph models
---

# Contractive Graph Neural Networks
Le **Contractive Graph Neural Networks** sono tra le prime formulazioni neurali per grafi con cicli. L'idea e definire per ogni nodo uno stato latente che dipende sia dall'informazione locale sia dagli stati dei vicini, ma in modo tale che la dinamica complessiva resti convergente anche in presenza di dipendenze reciproche.

Si introduce uno stato nodale $h(v)$, dove $v$ e il nodo considerato. Se $x(v)$ indica la feature del nodo, $N(v)$ il suo vicinato, $V$ la trasformazione applicata all'input locale e $W$ quella applicata agli stati dei vicini, si scrive
$$
h(v)=\tanh\left(Vx(v)+\sum_{v' \in N(v)}Wh(v')\right).
$$
La formula rappresenta una mappa ricorrente su grafo: il nodo combina il proprio contenuto con gli stati del vicinato; operativamente, gli embedding nodali non si ottengono in un singolo forward pass, ma per iterazioni successive fino al raggiungimento di un punto fisso.

La proprieta decisiva e la **contrattivita**. Si richiede che la mappa di aggiornamento riduca progressivamente la distanza tra stati successivi, cosi da garantire convergenza della dinamica. Per definizione, se l'operatore e contrattivo, esiste un punto fisso stabile verso cui l'iterazione converge; operativamente, questo rende ben definita l'inferenza anche su grafi ciclici.

Il vantaggio del modello e l'aderenza naturale alla struttura ricorrente del grafo. Il limite e che durante l'addestramento i parametri devono restare in una regione che preservi la contrattivita, e questo rende l'ottimizzazione costosa e poco flessibile rispetto alle architetture feed-forward moderne.

Proprieta chiave:
- definiscono una dinamica ricorrente di punto fisso su grafi
- gestiscono naturalmente cicli e dipendenze reciproche
- richiedono contrattivita per garantire convergenza
- il vincolo di stabilita rende il training piu oneroso
