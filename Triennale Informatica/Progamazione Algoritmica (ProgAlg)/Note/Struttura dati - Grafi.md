---
Course: "[[Programmazione e Algoritmica (PEA)]]"
tags:
  - PEA
topic: Strutture Dati
---
# Struttura dati - Grafo

I **grafi** sono una tipologia di [[Strutture Dati|Struttura Dati]] utilizzata per rappresentare relazioni tra oggetti. Formalmente, un grafo $G$ è definito come una coppia $G = (V, E)$ dove:
- $V$ è un insieme finito di **vertici** (o nodi).
- $E$ è un insieme di **archi** (o lati), che connettono coppie di vertici.
Gli archi possono essere **orientati** (nel qual caso il grafo è detto **orientato**) o **non orientati**.


![[IMG - Esempio grafo complesso.png]]

Un **cammino semplice** in un grafo è una sequenza di vertici $(v_1, v_2, ..., v_k)$ tale che ciascuna coppia consecutiva $(v_i, v_{i+1})$ è un arco del grafo, e tutti i vertici sono distinti.

Un **ciclo** è un cammino che inizia e termina nello stesso vertice e in cui nessun altro vertice viene ripetuto.

Un **taglio** in un grafo è una partizione dell'insieme dei vertici in due sottoinsiemi disgiunti $S$ e $T$. Il taglio separa il grafo in due componenti e gli archi che lo attraversano sono chiamati **archi del taglio**. I tagli giocano un ruolo fondamentale negli algoritmi di ottimizzazione, come il **Min-Cut** per la separazione ottimale dei grafi.

### Rappresentazione dei grafi
Un grafo può essere rappresentato in diversi modi a seconda delle necessità computazionali:
1. **Matrice di adiacenza**:
    - Una matrice quadrata $A$ di dimensione $|V| \times |V|$ in cui l'elemento $A[i][j]$ è uguale al peso dell'arco $(v_i, v_j)$ se esiste, altrimenti è 0 (o infinito se il grafo è pesato).
    - Vantaggi: Accesso rapido agli archi.
    - Svantaggi: Occupazione di memoria elevata per grafi sparsi.
2. **Lista di adiacenza**:
    - Ogni vertice è associato a una lista che contiene i suoi vicini.
    - Vantaggi: Efficiente in termini di memoria per grafi sparsi.
    - Svantaggi: Accesso meno immediato agli archi rispetto alla matrice di adiacenza.
3. **Lista degli archi**:
    - L'insieme degli archi viene rappresentato come una lista di coppie (o triplette se il grafo è pesato) $(u, v, w)$ dove $w$ è il peso.
    - Utile per algoritmi di elaborazione sugli archi (come Kruskal).



