---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# HISAT2 - Software di allineamento per RNAseq
---
**HISAT2** è un software di allineamento utilizzato nello [[analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 2: Alignment|Step 2: Alignment]], progettato per mappare reads su genomi complessi in modo efficiente e con basso consumo di memoria.

HISAT2 si basa su una strategia di ricerca **graph-based**, che rappresenta la sua caratteristica fondamentale.

Caratteristiche principali:
- Strategia basata su grafi:
  - costruisce inizialmente una rappresentazione lineare del genoma di riferimento
  - aggiunge mutazioni, inserzioni e delezioni come percorsi alternativi nel grafo
- Rappresentazione compatta:
  - utilizza strutture derivate da FM-index e [[Burrows-Wheeler Transform (BWT)|Burrows-Wheeler Transform]]
  - integra varianti genomiche in un unico indice
- Allineamento splice-aware:
  - adatto a reads RNA-seq che attraversano junction introniche

Vantaggi dichiarati:
- Maggiore efficienza in termini di utilizzo della memoria rispetto a rappresentazioni puramente lineari
- Buon compromesso tra velocità e accuratezza
- Indice relativamente leggero rispetto ad altri aligner splice-aware

Considerazioni:
- Prestazioni fortemente dipendenti dalla qualità dell’indice e delle annotazioni
- In alcuni scenari può risultare leggermente meno veloce di [[STAR - Software di allineamento per RNAseq|STAR]] su dataset molto grandi