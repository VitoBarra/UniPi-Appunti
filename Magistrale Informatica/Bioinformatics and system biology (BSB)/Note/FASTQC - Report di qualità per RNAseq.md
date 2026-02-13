---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# FASTQC - Report di qualità per RNAseq
---
**FASTQC** è un software per la valutazione della qualità dei dati di sequenziamento e si colloca nello step iniziale della pipeline di [[analisi RNA-seq]], ovvero nello [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: Quality assessment]].

FASTQC non esegue trimming né rimozione di adattatori, ma genera report diagnostici sui file FASTQ per identificare:
- qualità per base (Phred score) lungo la read
- distribuzione delle quality scores
- contenuto GC
- sequenze sovrarappresentate
- presenza di adattatori
- duplicazione delle reads

![[IMG - FASTQC report.png]]

Nel modulo *Per base sequence quality* vengono riportati:
- boxplot delle quality scores per posizione
- mediana, quartili e range
- soglie cromatiche tipiche: verde (buona qualità), giallo (attenzione), rosso (bassa qualità)

L’analisi comparativa *Before trimming* vs *After trimming* consente di verificare:
- rimozione delle code a bassa qualità
- eliminazione di adattatori
- miglioramento della distribuzione delle Phred scores nelle regioni terminali

FASTQC è quindi uno strumento di controllo qualità preliminare e post-trimming, utile per:
- decidere parametri di trimming (es. lunghezza minima, soglia Phred)
- verificare l’efficacia di software di trimming come [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Cutadapt]], [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Trimmomatic]] o [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|fastp]]

Output:
- report HTML
- file .zip con metriche dettagliate

Ruolo nella pipeline:
Quality Control → Trimming → (nuovo QC con FASTQC) → [[Analisi RNA-seq#Step 2: Alignment|Alignment]] → quantificazione → DE analysis
