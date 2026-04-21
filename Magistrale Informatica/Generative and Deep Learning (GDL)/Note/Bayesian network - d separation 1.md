---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Bayesian network - d separation
---
Bayesian network - d separation è un criterio grafico che permette di determinare le relazioni di indipendenza condizionata tra variabili in una [[Bayesian Network]] analizzando la struttura del grafo.

Dato un DAG $\mathcal{G}$ e tre insiemi di nodi $X, Y, Z$, la d-separation stabilisce se vale l’indipendenza $$X \perp Y \mid Z$$ sulla base dei percorsi nel grafo, senza calcolare esplicitamente le distribuzioni.

Definizione:
- un percorso non orientato $r$ tra due nodi è detto bloccato da $Z$ se esiste un nodo $Y_c$ nel percorso tale che:
  - caso chain: $$Y_i \rightarrow Y_c \rightarrow Y_j$$ oppure $$Y_i \leftarrow Y_c \leftarrow Y_j$$ con $Y_c \in Z$
  - caso fork: $$Y_i \leftarrow Y_c \rightarrow Y_j$$ con $Y_c \in Z$
  - caso collider: $$Y_i \rightarrow Y_c \leftarrow Y_j$$ con $Y_c \notin Z$ e nessun suo discendente in $Z$ :contentReference[oaicite:0]{index=0}

Un percorso è attivo (non bloccato) se nessuna delle condizioni precedenti si verifica.

Due nodi $X$ e $Y$ sono d-separati da $Z$ se tutti i percorsi tra $X$ e $Y$ sono bloccati da $Z$, cioè $$\text{Dsep}_{\mathcal{G}}(X,Y|Z)$$ implica indipendenza condizionata :contentReference[oaicite:1]{index=1}

Interpretazione:
- la d-separation traduce la struttura del grafo in vincoli probabilistici
- consente di leggere direttamente indipendenze dal grafo
- evita il calcolo esplicito della distribuzione congiunta

Ruolo delle tre strutture fondamentali:
- chain $X \rightarrow Z \rightarrow Y$: il nodo intermedio blocca il flusso se osservato $$X \perp Y \mid Z$$
- fork $X \leftarrow Z \rightarrow Y$: il nodo comune blocca la dipendenza se osservato $$X \perp Y \mid Z$$
- collider $X \rightarrow Z \leftarrow Y$: il nodo centrale attiva il percorso solo se osservato $$X \not\!\perp Y \mid Z$$

Proprietà:
- base della [[Global Markov Property]]
- equivalente alla proprietà locale nelle [[Bayesian Network]]
- permette inferenza strutturale sulle dipendenze

Formalmente, la d-separation definisce quando la struttura del grafo implica indipendenze del tipo $$P(X,Y|Z) = P(X|Z)P(Y|Z)$$, collegando direttamente grafi e distribuzioni probabilistiche