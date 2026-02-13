---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Kallisto - Software di allineamento per RNAseq
---
**Kallisto** è un software utilizzato nello [[analisi RNA-seq]] durante lo [[Analisi RNA-seq|Step 2: alineamento]], progettato per stimare rapidamente l’abbondanza dei trascritti a partire da reads RNA-seq e da un riferimento trascrittomico.

Kallisto implementa una strategia di **pseudoalignment basata su k-mer**, evitando l’allineamento base-per-base al genoma.

![[IMG - Software di allineamento per RNAseq - Kallisto.png]]

Cosa fa:
- Riceve in input:
  - reads RNA-seq ([[Formato FASTQ|FASTQ]])
  - transcriptome [[Formato FASTA|FASTA]]
- Stima quante reads provengono da ciascun trascritto
- Produce:
  - TPM
  - estimated counts
  - file per bootstrap (opzionale)

Come funziona:
- Costruisce un indice k-mer di tutti i trascritti
- Per ogni read:
  - identifica i k-mer contenuti nella read
  - determina l’insieme dei trascritti compatibili (pseudoalignment)
  - non esegue allineamento completo nucleotide-per-nucleotide
- Applica un algoritmo EM:
  - assegna probabilisticamente le reads ai trascritti compatibili
  - stima le abbondanze finali

Key points:
- Molto veloce e memory-efficient
- Ottimo per quantificazione a livello di trascritto
- Non produce file BAM genomici (assenza di full alignment)

Pro:
- Molto veloce e leggero:
  - pseudoalignment con indice k-mer
  - tempi di esecuzione ridotti anche su hardware modesto
- Basso uso di memoria
- Workflow semplice:
  - build index → quantify
- Strumento maturo e ampiamente utilizzato

Contro:
- Correzione bias meno estesa rispetto a [[Salmon - Software di allineamento per RNAseq|Salmon]]
- Transcriptome-only:
  - nessuna modalità alignment-based su BAM genomici
- Diagnostica meno dettagliata rispetto a Salmon

Good choice when:
- Si desidera quantificazione trascrittomica molto rapida
- Si dispone di un buon riferimento di trascritti
- Non è necessaria modellazione avanzata dei bias
