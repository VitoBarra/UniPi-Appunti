---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area:
topic:
SubTopic:
---

#  Struttura di un CSP - Sotto problemi indipendenti
---
nei [[Problemi di soddisfacibilita vincolata (CSP)|CSP]] si può utilizzare la **struttura del problema**, rappresentata attraverso **il grafo dei vincoli**, per risolvere più velocemente il problema della ricerca di un assegnazione. 
Questo si fa tramite decomposizione del problema originale in **sotto problemi indipendenti**

La determinazione dell'indipendenza tra sotto problemi si basa sull'individuazione delle [[Grafi|componenti connesse]] del [[Grafi|grafo]] dei vincoli. Ogni **componente definisce un sotto problema** $CSP_i$ e l'unione delle soluzioni parziali $\bigcup_i S_i$ rappresenta una soluzione complessiva $\bigcup_i CSP_i$. 
Questo approccio consente un'efficienza computazionale significativa: supponendo che ogni sotto problema coinvolga $c$ variabili su un totale $n$, con $c$ costante, il numero di sotto problemi è $n/c$ e la complessità per ciascuno è al massimo $d^c$, con $d$ dimensione del dominio. La complessità totale diventa $O(d^c \cdot n/c)$, dunque lineare rispetto a $n$, contrapposta all'approccio diretto con complessità esponenziale $O(d^n)$. Questa proprietà pero è rara.


