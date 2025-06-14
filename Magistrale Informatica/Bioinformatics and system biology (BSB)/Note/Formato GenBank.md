---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Formato GenBank
---
Il **formato GenBank** è un formato testuale ricco utilizzato per rappresentare **sequenze biologiche annotate** in modo integrato. A differenza di formati che separano sequenza e annotazioni, il formato GenBank combina in un’unica struttura la sequenza nucleotidica, i metadati descrittivi e le annotazioni strutturali e funzionali, secondo i principi dell’[[Annotazione genica e trascrizionale]]. Questo approccio lo rende particolarmente adatto alla consultazione e alla documentazione delle informazioni contenute nelle [[Banche dati biologiche]].

Un file GenBank è organizzato in sezioni logiche ben definite, ciascuna delle quali contribuisce a descrivere un aspetto specifico della sequenza. Le sezioni iniziali contengono informazioni generali, come identificatori, organismo di origine e riferimenti bibliografici, fornendo il contesto biologico e sperimentale della sequenza. Questi metadati permettono di collocare la sequenza all’interno di un quadro informativo più ampio, facilitando l’integrazione con altre risorse.

La parte centrale del file è dedicata alle **annotazioni**, organizzate nella sezione delle feature. In questa sezione, le entità biologiche rilevanti vengono descritte come elementi strutturali associati a intervalli di coordinate sulla sequenza. Le feature rappresentano concetti come geni, trascritti, esoni e regioni codificanti, e sono accompagnate da attributi che ne specificano l’identità, la funzione e le relazioni. Questo modello consente di rappresentare in modo esplicito la struttura genica e la complessità trascrizionale, inclusa la presenza di isoforme alternative.

Dal punto di vista concettuale, la struttura di un file GenBank può essere schematizzata in tre componenti principali:
- **informazioni generali**, che descrivono l’identità e il contesto della sequenza;
- **annotazioni strutturali e funzionali**, che collegano regioni della sequenza a entità biologiche;
- **sequenza biologica**, rappresentata come una stringa di simboli nucleotidici.

La sequenza è riportata nella parte finale del file ed è coerente con la rappresentazione utilizzata nel [[Formato FASTA]], pur essendo integrata in una struttura più complessa. Le coordinate utilizzate nelle annotazioni fanno riferimento diretto a questa sequenza, rendendo immediato il collegamento tra struttura e funzione.

Nel contesto dei [[Formati di file biologici]], il formato GenBank rappresenta una soluzione **integrata**, in contrapposizione ai formati modulari che mantengono separate sequenza e annotazioni. Questa integrazione favorisce la leggibilità umana e la completezza informativa, ma riduce la flessibilità nell’aggiornamento indipendente delle annotazioni. Nonostante ciò, il formato GenBank rimane uno standard ampiamente utilizzato per la distribuzione e l’archiviazione di sequenze annotate, nonché come fonte primaria per l’estrazione di informazioni genomiche e trascrizionali.
