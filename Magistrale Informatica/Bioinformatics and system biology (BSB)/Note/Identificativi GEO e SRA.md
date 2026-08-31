---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Identificativi GEO, BioProject, BioSample e SRA
---
Negli studi di trascrittomica e genomica pubblica non esiste un unico identificativo di «campione». GEO, BioProject, BioSample e SRA descrivono livelli differenti dello studio e assegnano accession number distinti. Nella pratica, gli analisti conservano una tabella di corrispondenza tra questi identificativi e gli identificativi locali del progetto.

La parola *sample* è quindi ambigua. Può indicare il paziente, il prelievo biologico, una preparazione di RNA, una libreria di sequenziamento oppure una colonna della matrice di espressione. È preferibile usare nomi espliciti come `patient_id`, `biosample_accession`, `experiment_accession` e `run_accession`.

## Archivi e responsabilità

- **GEO — Gene Expression Omnibus** conserva studi di genomica funzionale, metadati biologici, protocolli e dati processati. Per i dati ottenuti mediante sequenziamento, i file grezzi sono normalmente archiviati in SRA.
- **BioProject** descrive lo scopo e il contesto generale di un progetto di ricerca. Gli accession number NCBI hanno forma `PRJNA...`.
- **BioSample** descrive il materiale biologico sottoposto ad analisi. Gli accession number NCBI hanno forma `SAMN...`.
- **SRA — Sequence Read Archive** descrive esperimenti e run di sequenziamento e conserva i dati grezzi.

BioProject e BioSample non sono semplicemente sinonimi di SRA Study e SRA Sample: sono record in database distinti, collegati tra loro. Un BioProject viene rappresentato anche come Study nei metadati SRA; un BioSample viene rappresentato anche come Sample SRA.

## Identificativi GEO

- **GSE — GEO Series**: studio o serie GEO. Raggruppa GSM correlati e descrive il disegno sperimentale.
- **GSM — GEO Sample**: record GEO relativo a un materiale o a una preparazione analizzata, con metadati biologici e protocolli. Non deve essere interpretato automaticamente come identificativo del paziente.
- **GPL — GEO Platform**: piattaforma usata per generare i dati, come un array o un modello di sequenziatore. Un GSM fa riferimento a una sola GPL, mentre una GPL può essere condivisa da molti GSM e studi.
- **GDS — GEO DataSet**: raccolta curata da GEO derivata da alcune Series. Non tutte le GSE possiedono una GDS corrispondente.

Un GSM può comparire in più GSE. Negli studi di sequenziamento può inoltre contenere collegamenti a BioSample, BioProject, SRX o SRR, ma non tutti i record espongono gli stessi tipi di collegamento.

## Identificativi BioProject e BioSample

- **PRJNA — NCBI BioProject**: progetto generale al quale appartengono i dati.
- **SAMN — NCBI BioSample**: descrizione di un materiale biologico con determinate proprietà. Più librerie, esperimenti o run possono riferirsi allo stesso BioSample. La politica di registrazione delle repliche dipende dal tipo di studio e dalle regole dell'archivio, quindi il numero di BioSample non va usato da solo per dedurre il numero di repliche biologiche.

BioSample è spesso il riferimento più utile per integrare attributi biologici tra archivi. Non equivale però necessariamente a un paziente: dallo stesso paziente possono provenire più tessuti, tempi, aliquote o condizioni, ciascuno potenzialmente registrato come BioSample distinto.

## Modello SRA

SRA organizza i dati in quattro livelli pubblici:

- **SRP — SRA Study**: studio SRA collegato a un BioProject.
- **SRS — SRA Sample**: rappresentazione SRA di un campione collegata a un BioSample.
- **SRX — SRA Experiment**: descrive la libreria e la combinazione di strategia, selezione, layout e piattaforma applicata a un determinato sample.
- **SRR — SRA Run**: manifest dei file prodotti eseguendo il sequenziamento dell'esperimento. È l'accession usato più spesso per scaricare o identificare le reads.

La struttura concettuale è:

```text
BioProject (PRJNA) ↔ SRA Study (SRP)
                         │
BioSample (SAMN)  ↔ SRA Sample (SRS)
                         │
                    Experiment (SRX)
                         │
                      Run (SRR)
                         │
                  FASTQ / SRA / CRAM
```

Questa è una struttura logica, non una garanzia di cardinalità uno-a-uno:

- uno Study contiene molti Sample, Experiment e Run;
- un BioSample/SRS può essere usato in più Experiment, per esempio per librerie o strategie differenti;
- un Experiment può avere uno o più Run;
- un Run paired-end può essere distribuito come due FASTQ, ma i due file appartengono allo stesso Run;
- multiplexing, pooling e studi single-cell possono rendere la corrispondenza tra campione biologico, libreria e file più complessa.

## Relazione tra GEO e SRA

GEO e SRA non formano un'unica gerarchia rigida. Un collegamento frequente è:

```text
GSE → GSM → SAMN/SRS → SRX → SRR → FASTQ
```

ma un record GSM può puntare direttamente a `SRX` o `SRR`, oppure fornire `SAMN` e `PRJNA`. Perciò non è corretto assumere che nel file GEO sia sempre presente una relazione esplicita `GSM → SRS`.

Il collegamento deve essere ricostruito usando le relazioni dichiarate nei record e verificato nei metadati SRA/BioSample. Anche la corrispondenza biologica non va dedotta soltanto dalla somiglianza dei nomi.

## Prefissi INSDC

SRA fa parte dell'International Nucleotide Sequence Database Collaboration insieme a ENA e DDBJ. Gli stessi livelli possono quindi apparire con prefissi diversi a seconda dell'archivio che ha originariamente assegnato l'accession:

| Livello | NCBI SRA | ENA | DDBJ |
|---|---|---|---|
| Study | `SRP` | `ERP` | `DRP` |
| Sample | `SRS` | `ERS` | `DRS` |
| Experiment | `SRX` | `ERX` | `DRX` |
| Run | `SRR` | `ERR` | `DRR` |
| BioProject | `PRJNA` | `PRJEB` | `PRJDB` |
| BioSample | `SAMN` | `SAMEA` | `SAMD` |

I record vengono scambiati tra i partner INSDC. Una pipeline generale non dovrebbe quindi accettare soltanto accession che iniziano con `SR` o `SAMN`.



## Integrità dei file

Checksum e dimensioni devono riferirsi allo specifico file distribuito:

- l'**MD5** verifica l'integrità byte per byte ed è il controllo principale;
- il numero di **byte** è un controllo aggiuntivo utile per individuare download troncati;
- per un run paired-end bisogna conservare, preferibilmente, checksum e dimensione di ciascun FASTQ oppure verificare esplicitamente la somma dei file;
- checksum e dimensioni pubblicati da ENA per i suoi FASTQ non devono essere applicati automaticamente a FASTQ rigenerati con SRA Toolkit: conversione, compressione e intestazioni possono produrre file byte-per-byte differenti pur derivando dallo stesso Run.

## Documentazione ufficiale

- [GEO Overview — organizzazione di Platform, Sample e Series](https://www.ncbi.nlm.nih.gov/geo/info/overview.html)
- [GEO — submission di dati da sequenziamento e collegamenti SRA](https://www.ncbi.nlm.nih.gov/geo/info/seq.html)
- [SRA Metadata and Submission Overview](https://www.ncbi.nlm.nih.gov/sra/docs/submitmeta/)
- [SRA — BioProject e BioSample](https://www.ncbi.nlm.nih.gov/sra/docs/submitbio/)
- [SRA Entrez — livelli e prefissi INSDC](https://www.ncbi.nlm.nih.gov/sra/docs/srasearch/)
- [SRA cloud metadata table — campi e accession](https://www.ncbi.nlm.nih.gov/sra/docs/sra-cloud-based-metadata-table/)
