---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Unique Molecular Identifier (UMI)
---
Un **Unique Molecular Identifier (UMI)**, o **identificatore molecolare univoco**, è una breve sequenza casuale di [[Nucleotidi|nucleotidi]] aggiunta fisicamente a ciascuna molecola originale durante la preparazione sperimentale della [[Tecnologie di sequenziamento#Libreria di sequenziamento|libreria di sequenziamento]], prima dell'amplificazione tramite [[Polymerase chain reaction (PCR)|PCR]]. L'aggiunta avviene in laboratorio, per esempio mediante adattatori o primer che contengono una regione nucleotidica casuale destinata a essere sequenziata insieme al frammento.

L'UMI funziona come un'etichetta molecolare: le copie generate dalla stessa molecola iniziale conservano lo stesso identificatore. Dopo il sequenziamento, reads che si allineano nella stessa posizione e possiedono lo stesso UMI possono quindi essere ricondotte, con maggiore affidabilità, a un'unica molecola originale.

## UMI e duplicati

Reads con sequenza identica possono avere due origini differenti:

- **duplicazione tecnica**: una singola molecola è stata amplificata più volte durante la PCR;
- **duplicazione biologica**: molecole originali distinte producono reads identiche perché provengono, per esempio, da un trascritto molto espresso.

Senza UMI è spesso difficile distinguere questi due casi considerando soltanto la sequenza e la posizione delle reads. Eliminare tutte le reads duplicate può quindi rimuovere segnale biologico reale, soprattutto nell'[[Analisi RNA-seq|RNA-seq]], dove alcuni trascritti sono naturalmente molto abbondanti.

Con gli UMI, invece, molecole originali distinte possono conservare identificatori differenti anche quando producono reads uguali. Le copie con lo stesso UMI possono essere raggruppate in una singola osservazione molecolare mediante **deduplicazione basata su UMI**.

## Limiti

Due molecole originali possono ricevere per caso lo stesso identificatore: questo fenomeno è chiamato **collisione degli UMI**. La probabilità di collisione aumenta quando l'UMI è corto o quando il numero di molecole marcate è elevato rispetto al numero di combinazioni disponibili. Per un UMI casuale lungo $n$ nucleotidi esistono teoricamente $4^n$ sequenze differenti; per esempio, un UMI di 8 nucleotidi può assumere $4^8 = 65.536$ combinazioni. Una collisione può far apparire due molecole originali distinte come copie della stessa molecola.

Anche errori di sequenziamento nella sequenza dell'UMI possono creare identificatori falsamente differenti. La progettazione della libreria e il software di analisi devono quindi considerare lunghezza, qualità, collisioni e correzione degli UMI.

Gli UMI devono essere aggiunti fisicamente durante la preparazione sperimentale della libreria, prima della PCR. La pipeline bioinformatica può leggere ed elaborare gli UMI presenti nei dati di sequenziamento, ma non può ricostruirli quando non sono stati inseriti nell'esperimento originale.

## Relazione con FASTQC

Il modulo **Sequence duplication levels** di [[FASTQC - Report di qualità per RNAseq|FASTQC]] segnala quanto frequentemente ricorrono sequenze identiche, ma non usa da solo questa informazione per determinare l'origine tecnica o biologica delle duplicazioni. La presenza di molti duplicati è quindi un'indicazione da interpretare nel contesto del tipo di libreria, dell'espressione dei trascritti e dell'eventuale disponibilità degli UMI.
