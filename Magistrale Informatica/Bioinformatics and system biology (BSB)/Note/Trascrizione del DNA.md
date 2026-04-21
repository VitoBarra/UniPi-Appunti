---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Trascrizione del DNA
---
La **trascrizione del DNA** e' il processo biologico con cui una regione di [[DNA|DNA]] viene copiata in una molecola di [[RNA]]. Il prodotto diretto della trascrizione non e' quindi una proteina, ma un **trascritto RNA**.

Nel caso dei geni codificanti, questo RNA puo' essere un **mRNA**, che poi potra' essere tradotto in una [[Proteine|proteina]]. In altri casi il prodotto puo' essere un RNA non codificante, con funzione strutturale o regolatoria.

![[BSB - DNA che contiene geni per codificare proteine.png]]

## Geni ed espressione genica

Il DNA contiene **unita' funzionali** chiamate [[Gene|geni]], cioe' sequenze di nucleotidi che contengono l'informazione necessaria per produrre un RNA funzionale. Quando un gene viene trascritto, si dice che quel gene e' **espresso**.

Per un gene codificante, il flusso generale dell'informazione e':

```text
DNA -> RNA -> proteina
```

La trascrizione corrisponde solo al primo passaggio:

```text
DNA -> RNA
```

La quantita' di RNA prodotto da un gene e' quindi una misura del suo livello di **espressione genica**. Se un gene produce molto mRNA, in generale ha maggiore potenziale di produrre proteina; se non produce mRNA, quel gene non e' espresso in quella condizione.

## Accessibilita' del DNA

Per essere trascritto, un gene deve essere accessibile alla **RNA polimerasi** e ai fattori di trascrizione. Nel nucleo, pero', il DNA non e' libero: e' compattato insieme a proteine, soprattutto istoni, formando la **cromatina**.

![[BSB - compattazione del DNA.png]]

Il grado di compattazione influenza l'espressione genica:

- cromatina piu' aperta: il gene e' piu' accessibile e puo' essere trascritto piu' facilmente;
- cromatina piu' compatta: il gene e' meno accessibile e la trascrizione e' ridotta o impedita.

## RNA polimerasi

La trascrizione e' catalizzata dalla **RNA polimerasi**, un enzima che scorre lungo il DNA e sintetizza una nuova molecola di RNA complementare al filamento stampo.

La RNA polimerasi e' simile concettualmente alla DNA polimerasi, ma ha alcune differenze importanti:

- non richiede un **primer**;
- usa **NTP** invece di **dNTP**;
- produce **RNA**, quindi usa uracile (**U**) al posto della timina (**T**).

![[IMG - RNA trascrizione dal DNA.png]]

La trascrizione parte da una regione regolatoria chiamata **promotore**, che indica dove deve iniziare la sintesi del trascritto. Il processo puo' essere diviso in tre fasi principali:

- **inizio**: la RNA polimerasi riconosce il promotore e apre localmente il DNA;
- **elongazione**: la RNA polimerasi avanza e allunga l'RNA;
- **terminazione**: la RNA polimerasi si stacca e il trascritto RNA viene rilasciato.

![[IMG - meccanismo di trascrizione da DNA a RNA.png]]

## Direzionalita' della trascrizione

Ogni filamento di DNA ha una direzione chimica, definita dalle estremita' **5'** e **3'**. I due filamenti della doppia elica sono **antiparalleli**:

```text
filamento A: 5' ---------------- 3'
filamento B: 3' ---------------- 5'
```

Durante la trascrizione, la RNA polimerasi legge il filamento stampo in direzione **3' -> 5'** e sintetizza l'RNA in direzione **5' -> 3'**:

```text
DNA template letto: 3' -> 5'
RNA sintetizzato:   5' -> 3'
```

Esempio:

```text
DNA template: 3' - T A C G G T - 5'
RNA prodotto: 5' - A U G C C A - 3'
```

Questo e' necessario perche' l'RNA, come il DNA, puo' essere allungato solo aggiungendo nuovi nucleotidi all'estremita' **3'** della catena nascente.

## Template strand e coding strand

Per ogni gene, solo uno dei due filamenti viene usato come stampo per produrre quel trascritto.

Si distinguono:

- **template strand**: filamento letto dalla RNA polimerasi;
- **coding strand** o **sense strand**: filamento complementare al template, con sequenza uguale all'RNA prodotto tranne per la sostituzione **T -> U**.

Esempio:

```text
coding/sense DNA: 5' - A T G C C A - 3'
template DNA:     3' - T A C G G T - 5'
RNA prodotto:     5' - A U G C C A - 3'
```

Il termine **sense** non indica un filamento sempre principale o piu' corretto. E' relativo al gene o al trascritto che si sta considerando.

## Geni sui due filamenti

Non esiste un lato del DNA che viene usato sempre come riferimento funzionale. Geni diversi possono trovarsi su filamenti diversi:

```text
gene A:  ---->
gene B:  <----
gene C:  ---->
```

Questo significa che, in una regione, il filamento `+` puo' essere il coding strand per un gene, mentre in un'altra regione puo' essere il template strand per un altro gene.

## Sense, antisense e NAT

Se due trascritti derivano da filamenti opposti della stessa regione genomica, si parla di trascritti **sense** e **antisense**:

```text
filamento +:  ---- trascritto sense ---->
filamento -:  <---- trascritto antisense ----
```

Un RNA antisense non e' lo stesso RNA letto al contrario. E' una molecola diversa, prodotta usando come template l'altro filamento del DNA e sintetizzata comunque in direzione **5' -> 3'**.

Un **NAT** (*natural antisense transcript*) e' un trascritto RNA endogeno prodotto dal filamento opposto rispetto a un altro gene o trascritto. Nel caso dei **cis-NAT**, i due trascritti provengono dallo stesso [[locus]] o da regioni genomiche sovrapposte/vicine.

Il NAT puo' essere:

- **coding**, se codifica una proteina;
- **non-coding**, se non codifica proteine e ha funzione regolatoria.

Nel caso degli **ncNAT**, l'antisense transcript e' non codificante.

## Collegamento con RNA-seq

Nell'[[Analisi RNA-seq]], se il protocollo non conserva l'informazione sul filamento di origine, diventa difficile distinguere un trascritto sense dal suo antisense.

In una coppia cis-NAT, una RNA-seq non stranded puo' misurare:

```text
espressione osservata = espressione sense + espressione antisense
```

Una RNA-seq **strand-specific** o **stranded** mantiene invece l'informazione sul filamento di origine, permettendo di quantificare separatamente i due trascritti.
