---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
  - Status/AiGenerated
Area: 
topic: 
SubTopic:
---

# Automa a stati finiti
---
L'__automa a stati finiti__ rappresenta un modello matematico astratto, impiegato per descrivere sistemi dinamici caratterizzati da un insieme finito di configurazioni, dette stati, tra cui il sistema può transitare in risposta a determinati stimoli o input. Tale modello si fonda sulla nozione che, in ogni istante, il sistema si trovi in uno e un solo stato, e che l'evoluzione sia determinata da una funzione di transizione. Questa funzione stabilisce, per ogni coppia costituita dallo stato attuale e dall'input ricevuto, quale sarà lo stato successivo.

Formalmente, un automa a stati finiti si definisce come una quintuppla $A = (Q, \Sigma, \delta, q_0, F)$, dove:

- $Q$ è l'insieme finito e non vuoto degli stati;
- $\Sigma$ è l'[[Alfabeto|alfabeto]] finito degli input;
- $\delta : Q \times \Sigma \rightarrow Q$ è la funzione di transizione, che specifica lo stato successivo;
- $q_0 \in Q$ è lo stato iniziale;
- $F \subseteq Q$ è l'insieme degli stati finali o accettanti.

L'alfabeto $\Sigma$ rappresenta l'insieme dei simboli leggibili dal sistema, i quali costituiscono le sequenze o stringhe su cui l'automa opera. Una stringa è definita come una successione finita di simboli appartenenti a $\Sigma$, e l'automa elabora tali stringhe attraverso transizioni di stato determinate dalla funzione $\delta$.

Si distingue tra automi deterministici e non deterministici. Negli automi deterministici (DFA), per ogni stato $q \in Q$ e per ogni simbolo $a \in \Sigma$, la funzione $\delta(q, a)$ restituisce un unico stato successivo. Al contrario, negli automi non deterministici (NFA), la funzione $\delta$ può associare a ogni coppia $(q, a)$ un insieme di stati, consentendo molteplici percorsi computazionali simultanei.

Il concetto di accettazione di una stringa è centrale nel comportamento di un automa. Data una stringa $w = a_1 a_2 \ldots a_n$ con $a_i \in \Sigma$, l'automa parte dallo stato iniziale $q_0$ e applica iterativamente la funzione $\delta$, seguendo la sequenza di simboli di $w$. Se, al termine dell'elaborazione, l'automa si trova in uno stato appartenente all'insieme $F$, la stringa è accettata; in caso contrario, è rifiutata.

L'insieme delle stringhe accettate da un automa a stati finiti costituisce il linguaggio riconosciuto dall'automa, denotato come $L(A)$. Si osserva che i linguaggi riconoscibili da automi a stati finiti coincidono esattamente con i linguaggi regolari, ovvero quelli che possono essere descritti mediante espressioni regolari o grammatiche regolari, come stabilito dai teoremi di equivalenza tra tali modelli formali.

Attraverso la rappresentazione grafica, l'automa si visualizza come un grafo orientato, in cui i nodi rappresentano gli stati e gli archi, etichettati con simboli di $\Sigma$, indicano le transizioni. Lo stato iniziale è generalmente evidenziato da un'entrata senza provenienza, mentre gli stati finali sono contrassegnati graficamente da un doppio cerchio.

Gli automi a stati finiti rivestono un ruolo fondamentale nell'ambito dell'informatica teorica, in particolare nella progettazione di compilatori, nei sistemi di controllo e nell'analisi dei linguaggi formali, costituendo uno strumento essenziale per la modellazione di comportamenti discreti e sequenziali.
