---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Problemi di ricerca
---
Formalmente, un **problema di ricerca** può essere definito come una quintupla:
$$
\langle S, A, s_0, G, T \rangle
$$
dove:
- $S$ è l’insieme degli stati possibili, detto **spazio degli stati** (*state space*), ovvero l’insieme di tutte le configurazioni del mondo che l’ambiente può assumere.
- $A$ è l’insieme delle **azioni** disponibili all’agente. Per ogni stato $s \in S$, si definisce una funzione $ACTIONS(s)$ che restituisce l’insieme finito di azioni applicabili in $s$.
- $s_0 \in S$ è lo **stato iniziale** (*initial state*), ovvero la configurazione del mondo da cui parte l’agente.
- $G \subseteq S$ è l’insieme degli **stati obiettivo** (*goal states*), ovvero gli stati considerati soddisfacenti in base a un criterio specificato. L’obiettivo può essere definito in diversi modi: come uno stato singolo, come un insieme finito di stati, oppure come una proprietà che descrive un insieme (anche potenzialmente infinito) di stati. Per gestire questa generalità, si definisce comunemente un predicato $IS\text{-}GOAL(s)$ che verifica se $s$ soddisfa il criterio desiderato.
- $T: S \times A \rightarrow S$ è il **modello di transizione** (*transition model*), ovvero una funzione deterministica che restituisce il nuovo stato risultante dall'applicazione di un’azione $a$ nello stato $s$: formalmente, $T(s, a) = s'$.

A queste componenti si aggiunge una **funzione di costo delle azioni**, detta $c(s, a, s')$ o $ACTION\text{-}COST(s, a, s')$, che assegna un valore numerico al costo di eseguire l’azione $a$ nello stato $s$ e arrivare allo stato $s'$. Questa funzione deve riflettere la metrica di prestazione adottata dall’agente. 

Una **sequenza di azioni** forma un *percorso* (*path*), e una **soluzione** al problema è un percorso che collega lo stato iniziale a uno stato obiettivo. Il **costo totale del percorso** è dato dalla somma dei costi delle singole azioni:
$$
\sum_{i=1}^{n} c(s_{i-1}, a_i, s_i)
$$
dove ogni $s_i = T(s_{i-1}, a_i)$ e $a_i$ è applicabile in $s_{i-1}$. Una **soluzione ottimale** (*optimal solution*) è una soluzione che minimizza il costo totale del percorso tra $s_0$ e uno stato in $G$.

Lo spazio degli stati può essere rappresentato come un **[[UniPi-Appunti/Triennale Informatica/Fondamenti Del Informatica (FDI)/Struttura dati - Grafi|grafo orientato]]** (*graph*), in cui i vertici rappresentano gli stati e gli archi orientati rappresentano le azioni. Ogni azione applicabile in uno stato definisce un arco dal nodo corrispondente a quello del risultato dell’azione. 