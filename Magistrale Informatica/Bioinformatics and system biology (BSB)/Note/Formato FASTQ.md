---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Formato file FASTQ
---
Il **formato FASTQ** è il formato standard per rappresentare reads provenienti dalle moderne [[tecnologie di sequenziamento|tecnologie di sequenziamento]].  il FASTQ include anche una stima della **qualità di sequenziamento per ogni base**. Questo lo rende il formato di partenza della maggior parte delle pipeline di [[Analisi di sequenze]] e, in particolare, delle analisi RNA-seq.

Il formato FASTQ rappresenta quindi una sequenza biologica osservata insieme a una misura di quanto sia affidabile ciascun carattere della sequenza. La presenza dei punteggi di qualità riflette il fatto che le reads non sono osservazioni perfette, ma il risultato di un processo sperimentale rumoroso.

Un file FASTQ è costituito da una successione di record indipendenti. Ogni record è formato da **quattro righe** che descrivono una singola read:

```
@identificatore  
SEQUENZA  
+  
QUALITÀ
```


- La prima riga inizia con il simbolo `@` e contiene l’identificatore della read, spesso seguito da informazioni sul sequenziamento (strumento, corsa, posizione).
- La seconda riga contiene la sequenza nucleotidica osservata.
- La terza riga è una riga separatrice che inizia con `+` e può opzionalmente ripetere l’identificatore.
- La quarta riga contiene la stringa di qualità, in cui ogni carattere corrisponde a una base della sequenza.

La lunghezza della stringa di qualità deve essere identica alla lunghezza della sequenza: a ogni nucleotide è associato un punteggio di qualità.

I punteggi di qualità sono codificati usando caratteri ASCII e rappresentano il **Phred score**, cioè una misura logaritmica della probabilità di errore nel sequenziamento di quella base. Valori più alti indicano maggiore affidabilità, mentre valori bassi indicano basi più incerte. Questa informazione è fondamentale per operazioni successive come filtraggio, trimming e allineamento.

All’interno dello stesso file FASTQ possono essere presenti milioni di record, ciascuno corrispondente a una read distinta. Il formato è quindi pensato per contenere grandi volumi di dati grezzi prodotti dal sequenziamento.

A differenza del formato FASTA, il FASTQ rappresenta **osservazioni sperimentali rumorose** e non sequenze di riferimento. Per questo motivo viene tipicamente utilizzato come input nelle fasi iniziali della pipeline RNA-seq (controllo qualità, trimming, allineamento), mentre i file FASTA vengono usati come riferimento per l’assegnazione delle reads.

Non esiste un’unica estensione standard per i file FASTQ; le più comuni sono:''

| Estensione | Contenuto                          |
| ---------- | ---------------------------------- |
| .fastq     | FASTQ generico                     |
| .fq        | abbreviazione di FASTQ             |
| .fastq.gz  | FASTQ compresso (forma più comune) |
| .fq.gz     | FASTQ compresso abbreviato         |

La compressione con gzip è estremamente frequente, poiché i file FASTQ possono essere molto grandi e contenere milioni o miliardi di reads.
