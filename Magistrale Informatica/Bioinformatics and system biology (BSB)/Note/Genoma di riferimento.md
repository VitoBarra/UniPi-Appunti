---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic: Genomics
SubTopic: Reference genome
---

# Genoma di riferimento
---
Un **genoma di riferimento** e' una sequenza curata usata come rappresentazione comune del [[Genoma|genoma]] di una specie e come sistema di coordinate. Permette di allineare read, descrivere [[Varianti germinali e somatiche|varianti]], collocare [[Gene|geni]] e confrontare risultati prodotti da esperimenti diversi.

Non e' il genoma di una persona media, non contiene tutte le varianti umane e non coincide necessariamente con il genoma completo di un singolo individuo. Il riferimento umano storico e' un **mosaico**: regioni diverse derivano da materiale sequenziato proveniente da piu' donatori, con contributi non uniformi.

## Come viene costruito

La costruzione di un riferimento richiede di trasformare molti frammenti sequenziati in una rappresentazione cromosomica ordinata:

```text
campioni biologici
        ↓
sequenziamento di molti frammenti
        ↓
assemblaggio in contig e sequenze piu' lunghe
        ↓
ordinamento e orientamento sui cromosomi
        ↓
correzione degli errori e controllo di qualita'
        ↓
scelta della sequenza principale e delle alternative
```

Il riferimento umano storico e' stato costruito integrando sequenze di librerie genomiche, assemblaggi e successive correzioni. Le regioni sono state selezionate e curate per ottenere una rappresentazione continua, accurata e stabile. Le nuove tecnologie a read lunghe hanno poi permesso di risolvere regioni ripetitive e lacune prima difficili da assemblare.

## Perche' non e' una media

Le basi del DNA sono categorie, non valori numerici: non esiste una media biologica tra `A`, `C`, `G` e `T`. Si potrebbe scegliere l'allele piu' frequente in ogni posizione, ma il risultato avrebbe diversi limiti.

Le varianti vicine sono spesso ereditate insieme in [[Aplotipo|aplotipi]]. Scegliere indipendentemente l'allele piu' frequente in ogni posizione puo' costruire una combinazione artificiale che non corrisponde a nessun cromosoma realmente osservato:

```text
aplotipo 1: A - C
aplotipo 2: G - T

scelta indipendente dei due alleli piu' frequenti: A - T
```

Inoltre, l'allele piu' comune puo' cambiare tra popolazioni. Un riferimento basato sulla frequenza globale favorirebbe comunque alcuni gruppi e penalizzerebbe gli altri. Le varianti rare, che possono essere importanti in medicina, resterebbero poco rappresentate.

## Come vengono gestite le varianti

La sequenza principale mostra un solo allele per posizione. Le differenze osservate nei campioni vengono registrate separatamente come varianti:

```text
riferimento: ... A C G T ...
campione:    ... A C A T ...
                    ↑
               variante G>A
```

In un file VCF la base del riferimento e' indicata come `REF` e quella osservata come `ALT`. `ALT` significa soltanto diversa dal riferimento: non implica che sia rara, patologica o comparsa recentemente. In alcune posizioni l'allele `ALT` puo' essere piu' frequente dell'allele `REF`.

Per distinguere una variante ereditaria da una acquisita non basta confrontare il campione con il riferimento. In oncologia si confrontano normalmente tumore e tessuto normale dello stesso paziente: una differenza presente in entrambi e' compatibile con una variante germinale, mentre una differenza rilevata soltanto nel tumore e' candidata come somatica.

## Perche' mantenere una sequenza lineare stabile

Una coordinata come `chr17:7673803` e' interpretabile soltanto rispetto a una specifica versione del riferimento. A queste coordinate sono collegati database clinici, pubblicazioni, file VCF, pannelli diagnostici e [[Annotazione genomica|annotazioni]]. Cambiare spesso la sequenza principale richiederebbe di convertire e rivalidare tutti questi dati; la conversione non e' sempre univoca nelle regioni aggiunte, eliminate o riordinate.

La stabilita' e' quindi una proprieta' progettuale importante: il riferimento deve essere abbastanza accurato da supportare le analisi, ma anche abbastanza stabile da consentire lo scambio e il confronto dei risultati.

## Versioni

Un riferimento viene pubblicato in versioni dette *assembly* o *build*. Per l'uomo sono molto usati:

- **GRCh37**, spesso chiamato **hg19** nell'ecosistema UCSC;
- **GRCh38**, spesso chiamato **hg38**, che corregge e amplia diverse regioni di GRCh37.

La stessa coordinata numerica puo' indicare sequenze diverse nei due assembly. La conversione tra versioni, detta **lift-over**, puo' fallire o essere ambigua nelle regioni modificate. Il riferimento deve inoltre essere compatibile con la release dell'annotazione: non e' corretto applicare direttamente coordinate GTF/GFF di GRCh37 a un FASTA GRCh38.

## Limiti del riferimento lineare

Una sequenza lineare puo' rappresentare un solo percorso principale e produce **reference bias**: le read simili al riferimento tendono ad allinearsi piu' facilmente di quelle che contengono sequenze differenti. Il problema e' evidente per inserzioni, delezioni, inversioni, duplicazioni e variazioni del numero di copie, che non possono essere riassunte scegliendo una singola base alternativa.

Sequenze alternative e *alternate loci* riducono alcuni limiti, ma non rappresentano tutta la diversita' umana. Il [[Pangenoma|pangenoma]] affronta il problema conservando piu' sequenze e aplotipi invece di comprimerli in un unico percorso lineare.

Vedi anche: [[Genoma]], [[Annotazione genomica]], [[Aplotipo]], [[Pangenoma]], [[Varianti germinali e somatiche]].
