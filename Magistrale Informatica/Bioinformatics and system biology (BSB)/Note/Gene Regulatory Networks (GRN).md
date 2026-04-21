---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Gene Regulatory Networks (GRN)
---
Una **Gene Regulatory Network (GRN)** è un [[Biological networks|biological network]] che rappresenta il **sistema di regolazione dell’espressione** [[DNA|genica]] in cui i **geni influenzano l’attivazione** o **l’inibizione** di altri **geni**. In questo contesto i nodi rappresentano geni e gli archi rappresentano influenze regolatorie tra geni.

Una [[Gene Regulatory Networks (GRN)|GRN]] modella come lo stato di attivazione di un gene dipenda da **altri geni** o da **stimoli esterni**. Formalmente può essere rappresentata come un grafo orientato in cui ogni gene $g_i$ è associato ad una variabile di stato $x_i$ che rappresenta il livello di attività del gene.

Nel caso più semplice si utilizzano stati discreti binari $x_i \in \{0,1\}$ dove $0$ rappresenta gene inattivo e $1$ gene attivo.

In generale lo stato del gene $i$ al tempo successivo dipende da una funzione dei geni regolatori e degli eventuali **input esterni**:
$$
x_i(t+1)=f_i(x_1(t),x_2(t),...,x_n(t),u_1(t),...,u_m(t))
$$
dove $u_k$ rappresentano **stimoli esterni o condizioni ambientali** che possono influenzare l’attività genica, come segnali cellulari, nutrienti o condizioni fisiologiche.

L’obiettivo di questo modello è descrivere come l’interazione tra geni e fattori esterni determini la **configurazione funzionale della cellula**, cioè quali geni risultano espressi in risposta a specifiche condizioni ambientali o segnali cellulari.

L’interazione tra geni può essere interpretata come un’influenza regolatoria: un gene può **attivare** o **inibire** l’espressione di un altro gene. Tuttavia queste relazioni non descrivono direttamente il dettaglio biochimico delle reazioni molecolari ma rappresentano un livello di astrazione più alto chiamato **gene-to-gene influence** o **factor-to-gene influence**

![[IMG - Gene Regulatory Networks (GRN) influense.png]]


Un esempio di [[Gene Regulatory Networks (GRN)|GRN]] è la **differenziazione delle cellule T CD4+**, in cui diversi fattori di trascrizione e segnali esterni determinano il tipo di cellula T che verrà prodotto.
![[IMG - GRN -  CD4+ T cell differentiation.png]]
In questo network:
- i **nodi gialli** rappresentano **stimoli esterni** (ad esempio citochine o segnali ambientali)
- i **nodi interni** rappresentano **geni o fattori di trascrizione**
- gli **archi positivi** indicano influenze di **attivazione**
- le interazioni possono essere **combinate**, cioè l’attivazione di un gene può richiedere la presenza simultanea di più regolatori
La rete descrive quindi come segnali ambientali e regolazioni geniche cooperino per guidare la cellula verso diversi **stati funzionali**, corrispondenti a differenti programmi di espressione genica.
