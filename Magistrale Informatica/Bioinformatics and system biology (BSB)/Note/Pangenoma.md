---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic: Genomics
SubTopic: Pangenome
---

# Pangenoma
---
Un **pangenoma** rappresenta la diversita' genomica di una specie integrando sequenze provenienti da piu' individui. Nel caso umano, un riferimento pangenomico contiene molte sequenze assemblate e i loro [[Aplotipo|aplotipi]], invece di ridurre la popolazione a un solo [[Genoma di riferimento|riferimento lineare]].

## Rappresentazione a grafo

Una forma comune e' il **grafo pangenomico**. I tratti condivisi formano percorsi comuni, mentre le differenze formano rami alternativi:

```text
          C
         / \
A ------     ------ G
         \ /
          T
```

Ogni percorso completo puo' rappresentare un aplotipo osservato. Il grafo puo' descrivere SNP, inserzioni, delezioni e varianti strutturali senza obbligare tutte le sequenze a seguire un solo percorso principale.

## Perche' non basta un riferimento con gli alleli piu' comuni

Un riferimento lineare costruito scegliendo l'allele piu' frequente in ogni posizione:

- puo' produrre una combinazione che non corrisponde a un aplotipo reale;
- dipende dalla popolazione usata per stimare le frequenze;
- continua a penalizzare alleli rari o specifici di gruppi poco rappresentati;
- non rappresenta bene inserzioni, duplicazioni, inversioni e variazioni del numero di copie;
- sposta il reference bias invece di eliminarlo.

Il pangenoma conserva invece piu' alternative e le relazioni tra varianti osservate insieme.

## Vantaggi

Il pangenoma puo':

- ridurre il reference bias nell'allineamento;
- migliorare il rilevamento di varianti strutturali;
- rappresentare regioni assenti o incomplete in GRCh38;
- includere meglio la diversita' tra popolazioni;
- permettere analisi basate su aplotipi completi.

## Limiti e adozione

Le pipeline pangenomiche sono piu' complesse di quelle basate su una sequenza lineare. Richiedono strumenti capaci di indicizzare e attraversare grafi, maggiori risorse computazionali e nuovi metodi per esprimere coordinate e varianti.

Database, file VCF, annotazioni cliniche e protocolli diagnostici sono ancora in gran parte organizzati sulle coordinate lineari di GRCh37 o GRCh38. Per questo il pangenoma viene gia' usato nella ricerca, soprattutto per varianti strutturali e regioni complesse, ma non ha ancora sostituito GRCh38 in tutte le pipeline standard o cliniche.

Nell'[[Analisi RNA-seq|RNA-seq]] ordinaria si usa ancora comunemente un genoma o trascrittoma lineare associato a una specifica [[Annotazione genomica|annotazione]]. Anche in questo ambito esistono metodi graph-aware, ma richiedono un ecosistema coerente di sequenze, annotazioni e identificativi.

Vedi anche: [[Genoma]], [[Genoma di riferimento]], [[Aplotipo]], [[Annotazione genomica]].
