---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Salmon - Software di allineamento per RNAseq
---
**Salmon** è un software utilizzato nello [[analisi RNA-seq]] durante lo [[Analisi RNA-seq|Step 2: alineamento]], progettato per quantificare l’espressione trascrittomica in modo rapido e accurato senza richiedere necessariamente un allineamento genomico completo.

Salmon implementa una strategia di **quasi-mapping (pseudoalignment)** su un riferimento trascrittomico.

Contesto d’uso:
- Possibile:
  - generare un’assembly trascrittomica (de novo o reference-based) e quantificare su di essa
  - mappare su trascrittoma con aligner tradizionali (es. [[HISAT2 - Software di allineamento per RNAseq|HISAT2]], [[Tophat 2 - Software di allineamento per RNAseq|Tophat 2]])
- Salmon evita il mapping genomico completo utilizzando direttamente un indice del trascrittoma

Salmon pseudoalignment:
- Richiede un insieme di trascritti di riferimento (annotazione o de novo)
- Strategia in tre fasi:
  1. Modello di mapping semplificato (quasi-mapping)
  2. Stima iniziale dei livelli di espressione e dei parametri del modello
  3. Raffinamento delle abbondanze tramite Expectation–Maximization o Variational Bayes
- Costruisce un modello probabilistico che stima la probabilità condizionata che un frammento appartenga a un determinato trascritto

Cosa fa:
- Quantifica l’espressione a livello di trascritto
- Aggregabile a livello genico
- Output:
  - TPM
  - conteggi stimati (estimated counts)
  - lunghezze efficaci
  - bootstrap / Gibbs samples per stimare l’incertezza

Come funziona (concettualmente):
- Costruisce un indice leggero del trascrittoma
- Mappa rapidamente le reads ai trascritti compatibili
- Applica modelli avanzati di correzione bias:
  - GC bias
  - bias posizionale
  - bias di sequenza
  - distribuzione della lunghezza dei frammenti
- Ottimizza le abbondanze tramite EM/VB

Modalità operative:
- Lightweight quasi-mapping mode (direttamente da FASTQ)
- Alignment-based mode (da BAM genomici pre-calcolati)

Pro:
- Molto veloce (comparabile o superiore a Kallisto)
- Forte enfasi sulla correzione dei bias
- Output ricchi e compatibili con tool downstream (tximport, sleuth, DRIMSeq)
- Ampia integrazione in workflow moderni (Snakemake, Nextflow)

Contro:
- Molti parametri configurabili (rischio misconfigurazione)
- Più “feature-heavy” rispetto a soluzioni minimaliste
- Produce principalmente valori normalizzati (TPM) e conteggi stimati:
  - la scelta del metodo di analisi differenziale deve essere coerente con il tipo di input atteso (raw counts vs valori normalizzati)

