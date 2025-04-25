---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Ricostruzione di superfici del mondo reale con rappresentazioni point base
---
Per **ricostruzione di una superficie** si intende il costruire una [[Mesh Poligonali|Mesh Poligonale]], che rappresenta una superfice originale, a partire da un campionamento **point base** di quella superfice reale.
I campionamenti sono fatti tramite [[Point Cloud (nuvola di punti)|nuvola di punti]] o [[Range map|range map]].

le problematica **ricostruzione di superfici** dipendono dal fatto che un **campionamento discreto** è difficile da interpretare univocamente.
![[IMG - Ricostruzione di superfici Problem statemente.png]]
I metodi di **ricostruzione** si dividono in **espliciti** e **impliciti**:  
- Gli **espliciti** assumono che la [[Point Cloud (nuvola di punti)|nuvola di punti]] sia un campionamento perfetto e che quindi ogni punti partecipa esattamente alla superfice. Costruiscono quindi una tassellatura diretta, utilizzando i punti come [[Mesh Poligonali|vertici della mesh]] ottenendo un interpolazione dei punti![[IMG - Ricostruzione di superfici esplicite.png]]
- Gli **impliciti** assumono che la [[Point Cloud (nuvola di punti)|nuvola di punti]] sia un campionamento con rumore e quindi ogni punto **guida** la superfice. Definiscono la superficie come l'insieme di zeri di una funzione $f_P: \mathbb{R}^3 \to \mathbb{R}$, per poi tassellare la [[Superfici implicite|superfice implicita]] $\{x \mid f_P(x) = 0\}$, ottenendo un approssimazione dei punti ![[IMG - Ricostruzione di superfici implicite.png]]
Questi due **approcci ortogonali** riflette la necessità di bilanciare fedeltà ai dati e regolarizzazione, specialmente in presenza di rumore o campionamento imperfetto.

**metodi espliciti**:
- [[Alpha Shape]]
- [[Ball Pivoting]]
- [[Mesh zippering]]