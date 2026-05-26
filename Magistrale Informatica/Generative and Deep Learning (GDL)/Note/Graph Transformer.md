---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Global attention
---

# Graph Transformer
Il **Graph Transformer** applica il paradigma dei [[Transformer|transformer]] al dominio dei grafi sostituendo o affiancando il [[Deep Graph Networks (DGN)#Meccanismo del message passing|message passing]] locale con meccanismi di attenzione globale. L'idea centrale e che ogni nodo possa interagire direttamente con tutti gli altri, senza dover propagare l'informazione hop dopo hop lungo gli archi.

## Idea di base
Il **Graph Transformer** nasce da una generalizzazione molto diretta. Se un grafo ha nodi con feature $x_1,\dots,x_n$, si possono trattare queste feature come una sequenza di token e passarle a un transformer standard. Dal punto di vista dell'implementazione, l'operazione e immediata: si prende l'insieme delle feature nodali, lo si impacchetta in una sequenza e lo si usa come input del modello. In questo senso il graph transformer e una generalizzazione diretta del transformer classico a input grafici.

## Perdita del bias strutturale
Il **Graph Transformer** ottiene pero questo risultato al prezzo di perdere il bias strutturale del grafo. In un transformer standard l'attenzione globale non usa in modo nativo la topologia: se si rimuovessero gli embedding posizionali, il modello non avrebbe alcun criterio per distinguere una permutazione della sequenza da un'altra. Nei grafi il problema e ancora piu netto, perche non esiste neppure un ordinamento canonico dei nodi; se i nodi vengono trattati solo come token, dal punto di vista del transformer due grafi con la stessa collezione di feature ma struttura diversa possono apparire identici o quasi.

Il punto concettuale e quindi questo: il message passing guarda il grafo dalla prospettiva locale di ciascun nodo e usa esplicitamente la struttura degli archi; il graph transformer, invece, lascia che **tutti parlino con tutti**. Questo risolve il problema della propagazione lenta dell'informazione, ma getta via proprio quel bias strutturale per cui si era scelto un grafo come rappresentazione del dato.

![[IMG - graph transofrmer.png]]

## Structural encodings
Il **Graph Transformer** cerca di recuperare parte della struttura tramite **structural encodings**, cioe vettori ausiliari che descrivono la posizione del nodo nel grafo o la relazione tra coppie di nodi. L'analogia con i transformer classici e diretta: come nelle sequenze si introducono positional embeddings per reintrodurre l'ordine, nei grafi si introducono encoding strutturali per reintrodurre la topologia.

Tra le soluzioni piu comuni compaiono autovettori del Laplaciano, feature derivate da random walk, distanze tra coppie di nodi, encoding locali e globali. Questi vettori non ricostruiscono un vero ordinamento del grafo, ma forniscono al modello informazione aggiuntiva su dove un nodo si collochi nella struttura. Operativamente, il transformer non recupera da solo il bias strutturale: lo riceve come informazione extra in input.

Questo punto e importante: gli encoding strutturali non sostituiscono il bias induttivo di una GNN locale. Possono aiutare il modello a orientarsi nella struttura, ma non trasformano l'attenzione globale in una propagazione nativamente sensibile agli archi. In altre parole, la struttura viene **riaggiunta**, non realmente incorporata nel meccanismo fondamentale del modello.

![[IMG - inductive bias.png]]

## Vantaggi e limiti
Il **Graph Transformer** ha un vantaggio forte: ogni nodo puo accedere in un solo layer a informazione proveniente da qualunque altro nodo del grafo. Questo riduce drasticamente i problemi di propagazione a lungo raggio tipici delle architetture puramente locali e rende molto efficace il trasferimento di informazione globale.

Il limite principale e duplice. Da un lato il costo computazionale dell'attenzione globale cresce tipicamente come $O(n^2)$ nel numero di nodi, quindi la scalabilita puo diventare critica su grafi grandi. Dall'altro lato il modello ha un bias strutturale molto piu debole di quello delle architetture basate su vicinati locali, quindi puo risultare meno naturale quando la topologia del grafo e parte essenziale del problema.

## Proprieta chiave
- trattano le feature nodali come token e applicano self-attention globale
- migliorano fortemente l'accesso a dipendenze a lungo raggio
- perdono il bias strutturale del grafo se la topologia non viene reintrodotta
- usano structural encodings come analogo dei positional embeddings
- spesso vengono combinati con message passing locale in architetture ibride
