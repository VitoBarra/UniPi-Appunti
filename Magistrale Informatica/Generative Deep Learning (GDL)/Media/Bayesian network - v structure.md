---
Course: "[[Generative Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Bayesian network - v structure
---
**Bayesian network - v structure** è una configurazione fondamentale in una [[Bayesian Network]] in cui due variabili $Y_1$ e $Y_2$ convergono su una variabile comune $Y_3$, formando la struttura $$Y_1 \rightarrow Y_3 \leftarrow Y_2$$

Questa struttura è detta collider (o common effect) perché $Y_3$ rappresenta un effetto comune delle due variabili genitrici. Dal punto di vista probabilistico, la distribuzione congiunta fattorizza come $$P(Y_1, Y_2, Y_3) = P(Y_1)P(Y_2)P(Y_3|Y_1,Y_2)$$ sfruttando la decomposizione delle [[Bayesian Network]] :contentReference[oaicite:0]{index=0}

La proprietà distintiva della v-structure riguarda le relazioni di indipendenza. In assenza di osservazioni, le due variabili genitrici risultano marginalmente indipendenti, cioè $$Y_1 \perp Y_2$$ perché non esiste un percorso attivo tra di esse. Tuttavia, questa indipendenza viene meno quando si condiziona sul nodo collider: $$Y_1 \not\!\perp Y_2 \mid Y_3$$

Questo comportamento è controintuitivo e prende il nome di explaining away. L’osservazione di $Y_3$ introduce una dipendenza tra $Y_1$ e $Y_2$ perché entrambe spiegano la stessa evidenza; conoscere una delle due riduce l’incertezza sull’altra.

Nel formalismo della [[d-separation]], il percorso tra $Y_1$ e $Y_2$ attraverso $Y_3$ è:
- bloccato se il collider non è osservato
- attivo se $Y_3$ è osservato oppure se lo è un suo discendente

Formalmente, un path con collider $Y_1 \rightarrow Y_3 \leftarrow Y_2$ è bloccato se $$Y_3 \notin Z$$ e nessun discendente di $Y_3$ appartiene a $Z$, mentre diventa attivo se questa condizione non vale :contentReference[oaicite:1]{index=1}

Questa struttura si distingue nettamente dalle altre configurazioni fondamentali:
- nelle strutture a catena e a fork l’osservazione di un nodo tende a bloccare la dipendenza
- nella v-structure l’osservazione del nodo centrale crea dipendenza

La v-structure è quindi cruciale per determinare le relazioni di indipendenza in una rete e rappresenta l’unico caso in cui la dipendenza emerge solo dopo condizionamento, rendendola centrale nello studio di [[d-separation]] e delle proprietà globali delle [[Bayesian Network]]