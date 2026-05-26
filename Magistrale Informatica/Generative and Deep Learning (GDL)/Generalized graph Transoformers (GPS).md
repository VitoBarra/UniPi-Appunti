---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area: Deep Learning for Graph
topic: Models
SubTopic: Hybrid graph models
---

# Generalized graph Transoformers (GPS)
I **Generalized graph Transoformers (GPS)** sono modelli ibridi per grafi che combinano una componente locale di [[Deep Graph Networks (DGN)#Meccanismo del message passing|message passing]] con una componente globale di [[Graph Transformer]]. L'idea nasce dal compromesso tra due esigenze opposte: da un lato preservare il bias strutturale del grafo, dall'altro diffondere rapidamente informazione anche tra nodi molto lontani.

## Idea del modello
Il **GPS** affianca due rami calcolati in parallelo. Il primo e un graph transformer, che realizza diffusione globale dell'informazione facendo parlare ogni nodo con tutti gli altri. Il secondo e una rete di message passing locale, che aggiorna i nodi usando il vicinato strutturale e quindi resta fortemente sensibile agli archi del grafo. I due risultati vengono poi fusi in un'unica rappresentazione.

Operativamente, il ramo transformer migliora l'accesso a dipendenze a lungo raggio, ma da solo ha un bias strutturale debole; il ramo locale non garantisce una diffusione globale rapida, ma preserva la geometria relazionale del grafo. Il senso del modello ibrido e quindi unire diffusione globale e sensibilita strutturale in una singola architettura.

![[IMG - ML su grafi GPD.png]]

## Perche servono modelli ibridi
I **Generalized graph Transoformers (GPS)** nascono dal fatto che le architetture puramente locali e quelle puramente globali hanno limiti complementari. Le DGN basate su message passing implementano bene la struttura, ma possono faticare a trasferire informazione su grandi distanze con pochi layer. I graph transformer eliminano questo problema, ma rischiano di trattare il grafo come una semplice collezione di token, perdendo proprio il vantaggio della struttura relazionale.

Il modello ibrido recupera allora "quella parte dell'effetto del message passing" che il transformer puro tende a buttare via: il ramo locale continua a leggere il grafo attraverso gli archi, mentre il ramo globale consente una comunicazione rapida tra nodi arbitrariamente distanti.

## Schema architetturale
Il **GPS** puo essere visto come una composizione di tre passi. Prima il grafo entra in un blocco locale di propagazione, cioe una forma di [[Deep Graph Networks (DGN)#Meccanismo del message passing|message passing]], e in parallelo in un blocco globale di self-attention. Poi le due rappresentazioni vengono combinate, per somma o altra fusione parametrica. Infine la rappresentazione risultante viene passata ai layer successivi o al readout finale.

In questa lettura il GPS non sostituisce ne le DGN ne i graph transformer, ma li usa come moduli all'interno di un framework piu generale di architetture ibride.

## Limite principale
Il **GPS** eredita pero anche il principale limite del transformer globale: la complessita della self-attention. Se il numero di nodi e $n$, il costo della componente globale cresce tipicamente come $O(n^2)$, perche ogni nodo puo interagire con tutti gli altri. Su grafi molto grandi questo diventa rapidamente proibitivo. Il guadagno in diffusione globale va quindi bilanciato contro il costo computazionale.

## Ruolo nel panorama dei modelli
I **Generalized graph Transoformers (GPS)** sono rappresentativi di una tendenza recente del campo: invece di proporre variazioni isolate di singoli modelli, si cerca di consolidare il panorama individuando combinazioni architetturali che separino chiaramente i ruoli dei diversi blocchi. In questo senso il GPS e un esempio di convergenza concettuale: il ramo locale serve a catturare struttura e sottografi rilevanti, il ramo globale serve a trasferire informazione e mitigare i limiti della sola propagazione locale.

## Proprieta chiave
- combinano message passing locale e self-attention globale
- preservano il bias strutturale del grafo meglio di un transformer puro
- migliorano la diffusione dell'informazione rispetto a una DGN puramente locale
- il limite principale e la complessita quadratica della componente globale
