---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area:
SubTopic:
---

# Grafo bipartito
---
Un [[Graph Theory|grafo]] si dice bipartito se l'insieme dei vertici puo essere suddiviso in due sottoinsiemi disgiunti $V_1$ e $V_2$ tali che:

$$
V = V_1 \cup V_2
$$

$$
V_1 \cap V_2 = \emptyset
$$

ed ogni arco collega sempre un vertice di $V_1$ con un vertice di $V_2$.

In altre parole, in un grafo bipartito non esistono archi tra due vertici dello stesso insieme della partizione.

## Partizione bipartita

La coppia $(V_1,V_2)$ e detta partizione bipartita del grafo. La partizione non e necessariamente unica, ma se il grafo e connesso allora e unica a meno di scambiare i due insiemi.

Se il grafo e orientato, in genere si considera bipartito il grafo sottostante non orientato: la direzione degli archi non cambia la bipartizione, conta solo quali coppie di vertici sono adiacenti.

## Caratterizzazioni equivalenti

Per un grafo finito sono equivalenti le seguenti proprieta:
- il grafo e bipartito
- il grafo e 2-colorabile, cioe i vertici possono essere colorati con due colori in modo che vertici adiacenti abbiano sempre colori diversi
- il grafo non contiene cicli di lunghezza dispari
Questa equivalenza e una delle proprieta fondamentali dei grafi bipartiti.

## Proprieta principali

- ogni cammino che parte da un vertice di $V_1$ alterna i vertici tra $V_1$ e $V_2$
- ogni ciclo in un grafo bipartito ha lunghezza pari
- un grafo bipartito completo con partizione $(V_1,V_2)$ contiene tutti e soli gli archi possibili tra $V_1$ e $V_2$
- se $|V_1|=m$ e $|V_2|=n$, il numero massimo di archi in un grafo bipartito e $mn$

## Grafo bipartito completo

Il grafo bipartito completo si indica con $K_{m,n}$ ed e il grafo in cui:

- il primo insieme della partizione ha $m$ vertici
- il secondo insieme della partizione ha $n$ vertici
- ogni vertice del primo insieme e collegato con tutti i vertici del secondo insieme

In questo caso il numero totale di archi e:

$$
|E| = mn
$$

## Come riconoscere un grafo bipartito

Un modo pratico per verificare se un grafo e bipartito consiste nell'eseguire una visita in ampiezza o in profondita e assegnare alternativamente due colori ai vertici.

- si sceglie un vertice iniziale e lo si colora con il primo colore
- tutti i suoi vicini ricevono il secondo colore
- si continua alternando i colori lungo gli archi
- se si incontra un arco che collega due vertici con lo stesso colore, il grafo non e bipartito

Questo controllo richiede tempo lineare rispetto a vertici e archi.

## Relazione con i cicli dispari

Un grafo e bipartito se e solo se non contiene cicli dispari.

- se un grafo e bipartito, ogni ciclo deve alternare i due insiemi della partizione e quindi ha lunghezza pari
- se un grafo non contiene cicli dispari, allora e possibile dividere i vertici in due classi in base alla parita della distanza da un vertice fissato

## Alberi e grafi bipartiti

Ogni albero e bipartito. Infatti un albero non contiene cicli, quindi in particolare non contiene cicli dispari.

Piu in generale, ogni foresta e bipartita.

## Accoppiamenti

In un grafo bipartito, un accoppiamento e un insieme di archi a due a due non incidenti. Gli accoppiamenti sono importanti perche rappresentano assegnazioni senza conflitti tra elementi delle due partizioni.

Un tema centrale e stabilire se esista un accoppiamento che saturi tutti i vertici di una delle due parti. Questo porta a risultati classici come il teorema di Hall e ai collegamenti con il [[Problema del flusso massimo]].

Un grafo orientato $(N,A)$ e detto bipartito se esistono due insiemi disgiunti $O,D \subseteq N$ tali che $N=O \cup D$ e $A \subseteq O \times D$.

In un grafo bipartito, un accoppiamento e un insieme di archi $M \subseteq A$ tale che su ogni nodo di $N$ incida al piu un arco di $M$.
