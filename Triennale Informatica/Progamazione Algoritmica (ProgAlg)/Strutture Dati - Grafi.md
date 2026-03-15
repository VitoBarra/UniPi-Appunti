---
Course: "[[Programmazione e Algoritmica (PEA)]]"
tags:
  - PEA
topic: 
SubTopic:
---

# Strutture Dati - Grafi
---
un **grafo** in **comuter cience** è una **[[Strutture Dati|struttura dati]]** la rappresentazione computazionale della struttura matematica [[Graph Theory|grafo]]. In questo contesto un grafo non è soltanto un oggetto teorico, ma una **struttura dati utilizzata per modellare e manipolare relazioni tra entità all’interno di un programma**.

Formalmente la struttura implementa il modello matematico $$G=(V,E)$$ dove $V$ rappresenta l’insieme dei **vertici (nodi)** ed $E$ l’insieme degli **archi (edges)** che collegano coppie di vertici. L’obiettivo dell’implementazione informatica è permettere **memorizzazione efficiente**, **accesso alle relazioni** e **esecuzione di algoritmi sui grafi**.

Dal punto di vista computazionale, la progettazione di una struttura dati per grafi riguarda principalmente:
- **rappresentazione della topologia** della rete  
- **complessità spaziale** della struttura  
- **complessità temporale** delle operazioni sui nodi e sugli archi  

Le rappresentazioni più comuni sono:

**Adjacency list**  
Ogni nodo mantiene la lista dei vertici adiacenti. Questa rappresentazione richiede memoria $$O(|V|+|E|)$$ ed è particolarmente efficiente per **grafi sparsi**.

**Adjacency matrix**  
La struttura utilizza una matrice $|V|\times|V|$ che indica la presenza o assenza di archi tra coppie di vertici. Richiede memoria $$O(|V|^2)$$ ma consente **accesso diretto agli archi in tempo costante**.

Queste strutture dati permettono l’esecuzione efficiente di algoritmi fondamentali sui grafi, come **ricerca di cammini**, **visita del grafo**, **analisi della connettività** e **ottimizzazione su reti**, collegando così l’astrazione matematica della [[Graph Theory]] con le esigenze computazionali delle [[strutture dati]].

### Rappresentazione dei grafi
Un grafo può essere rappresentato in diversi modi a seconda delle necessità computazionali:
1. **[[Spectral Graph Theory|Matrice di adiacenza]]**:
    - Vantaggi: Accesso rapido agli archi.
    - Svantaggi: Occupazione di memoria elevata per grafi sparsi.
2. **Lista di adiacenza**:
    - Ogni vertice è associato a una lista che contiene i suoi vicini.
    - Vantaggi: Efficiente in termini di memoria per grafi sparsi.
    - Svantaggi: Accesso meno immediato agli archi rispetto alla matrice di adiacenza.
3. **Lista degli archi**:
    - L'insieme degli archi viene rappresentato come una lista di coppie (o triplette se il grafo è pesato) $(u, v, w)$ dove $w$ è il peso.
    - Utile per algoritmi di elaborazione sugli archi (come Kruskal).
