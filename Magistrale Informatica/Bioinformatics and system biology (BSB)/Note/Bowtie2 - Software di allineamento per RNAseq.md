---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Bowtie2 - Software di allineamento per RNAseq
---
**Bowtie2** è un software di allineamento utilizzato nello [[analisi RNA-seq]] durante lo [[Analisi RNA-seq#Step 2: Alignment|Step 2: Alignment]], basato sulla **[[Burrows-Wheeler Transform (BWT)|Burrows-Wheeler Transform (BWT)]]** e sull’uso dell’**FM-index** per eseguire ricerche efficienti nel genoma di riferimento.

Bowtie2 è progettato per allineare reads su genomi di grandi dimensioni in modo rapido e con un uso contenuto della memoria.

Principi algoritmici:
- Utilizza la ****[[Burrows-Wheeler Transform (BWT)|Burrows-Wheeler Transform (BWT)]]** per comprimere e indicizzare il genoma.
- Impiega l’**FM-index** per supportare la ricerca efficiente di pattern arbitrari.
- Applica una strategia di ricerca denominata *walk-left* nell’indice FM.

Per ciascuna read, Bowtie2 esegue quattro passaggi principali:
1. Estrazione dei *seed*:
   - suddivisione della read in frammenti (sequence snippets)
   - considerazione anche del reverse complement
2. Allineamento dei seed:
   - mapping dei seed sul genoma
   - produzione di bande di allineamento basate su BWT
3. Selezione e raffinamento:
   - selezione iterativa e pesata delle bande candidate
   - utilizzo dell’FM-index per esplorare possibili estensioni
   - compressione della suffix matrix per mantenere efficienza
4. Risoluzione delle ambiguità:
   - confronto tra allineamenti simili
   - scelta dell’allineamento ottimale in base a score e bordi

Caratteristiche:
- Elevata efficienza in termini di memoria
- Buona gestione di mismatch e indel
- Non nativamente ottimizzato per splice junction (a differenza di [[STAR - Software di allineamento per RNAseq|STAR]] o [[HISAT2 - Software di allineamento per RNAseq|HISAT2]])

Uso tipico:
- Allineamento DNA-seq
- RNA-seq in combinazione con wrapper splice-aware (es. [[Tophat 2 - Software di allineamento per RNAseq|TopHat2]])