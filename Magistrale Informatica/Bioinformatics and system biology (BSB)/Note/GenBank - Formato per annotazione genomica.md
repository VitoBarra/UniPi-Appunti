---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GenBank - Formato per annotazione genomica
---
Il **formato GenBank** e' un formato testuale ricco utilizzato per rappresentare **sequenze biologiche annotate** in modo integrato. A differenza di formati che separano sequenza e annotazioni, il formato GenBank combina in un'unica struttura la sequenza nucleotidica, i metadati descrittivi e le [[Annotazione genomica|annotazioni genomiche]] strutturali e funzionali. Questo approccio lo rende particolarmente adatto alla consultazione e alla documentazione delle informazioni contenute nelle [[Banche dati biologiche|banche dati biologiche]].

Un file GenBank e' organizzato in sezioni logiche ben definite, ciascuna delle quali contribuisce a descrivere un aspetto specifico della sequenza. Le sezioni iniziali contengono informazioni generali, come identificatori, organismo di origine e riferimenti bibliografici, fornendo il contesto biologico e sperimentale della sequenza. Questi metadati permettono di collocare la sequenza all'interno di un quadro informativo piu' ampio, facilitando l'integrazione con altre risorse.

La parte centrale del file e' dedicata alle **annotazioni**, organizzate nella sezione delle feature. In questa sezione, le entita' biologiche rilevanti vengono descritte come elementi strutturali associati a intervalli di coordinate sulla sequenza. Le feature rappresentano concetti come geni, trascritti, esoni e regioni codificanti, e sono accompagnate da attributi che ne specificano l'identita', la funzione e le relazioni. Questo modello consente di rappresentare in modo esplicito la struttura genica e la complessita' trascrizionale, inclusa la presenza di isoforme alternative.

Dal punto di vista concettuale, la struttura di un file GenBank puo' essere schematizzata in tre componenti principali:

- **informazioni generali**, che descrivono l'identita' e il contesto della sequenza;
- **annotazioni strutturali e funzionali**, che collegano regioni della sequenza a entita' biologiche;
- **sequenza biologica**, rappresentata come una stringa di simboli nucleotidici.

La sequenza e' riportata nella parte finale del file ed e' coerente con la rappresentazione utilizzata nel [[Formato FASTA|formato FASTA]], pur essendo integrata in una struttura piu' complessa. Le coordinate utilizzate nelle annotazioni fanno riferimento diretto a questa sequenza, rendendo immediato il collegamento tra struttura e funzione.

Nel contesto dei formati di file biologici, il formato GenBank rappresenta una soluzione **integrata**, in contrapposizione ai formati modulari che mantengono separate sequenza e annotazioni. Questa integrazione favorisce la leggibilita' umana e la completezza informativa, ma riduce la flessibilita' nell'aggiornamento indipendente delle annotazioni. Nonostante cio', il formato GenBank rimane uno standard ampiamente utilizzato per la distribuzione e l'archiviazione di sequenze annotate, nonche' come fonte primaria per l'estrazione di informazioni genomiche e trascrizionali.
