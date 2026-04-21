---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GFF - Formato per annotazione genomica
---
Il **formato GFF** (General Feature Format) e' un formato testuale standard utilizzato per rappresentare [[Annotazione genomica|annotazioni genomiche]] in modo strutturato e indipendente dalla sequenza biologica. Esso e' impiegato per descrivere la posizione e le caratteristiche di elementi funzionali come geni, trascritti, esoni e regioni codificanti. Il formato GFF svolge un ruolo centrale nell'organizzazione delle informazioni contenute nelle [[Banche dati biologiche|banche dati biologiche]] e nella loro integrazione con strumenti di visualizzazione come i genome browser.

Un file GFF non contiene la sequenza genomica, ma fa riferimento a una sequenza di riferimento esterna, tipicamente rappresentata in [[Formato FASTA|formato FASTA]]. Le annotazioni sono espresse come una collezione di **feature**, ciascuna associata a una regione genomica definita da coordinate. Questa separazione tra sequenza e annotazione consente una maggiore flessibilita' nell'aggiornamento delle informazioni e favorisce il confronto tra annotazioni provenienti da fonti diverse.

Dal punto di vista strutturale, il formato GFF e' organizzato come un file di testo tab-delimitato composto da **nove colonne**, ciascuna delle quali descrive un aspetto specifico della feature annotata:

- **colonna 1**: identificatore della sequenza di riferimento;
- **colonna 2**: sorgente dell'annotazione, che indica l'origine del dato;
- **colonna 3**: tipo di feature annotata, come gene, esone o regione codificante;
- **colonne 4 e 5**: coordinate genomiche di inizio e fine della feature;
- **colonna 6**: punteggio associato alla feature, quando disponibile;
- **colonna 7**: filamento genomico, che indica l'orientamento della feature;
- **colonna 8**: fase di lettura, rilevante per le regioni codificanti;
- **colonna 9**: insieme di attributi che descrivono proprieta' aggiuntive della feature.

La nona colonna svolge un ruolo fondamentale, poiche' consente di associare alla feature una serie di coppie chiave-valore che ne specificano l'identita' e le relazioni con altre feature. Attraverso questi attributi e' possibile rappresentare strutture gerarchiche, come l'organizzazione di piu' esoni all'interno di un trascritto o di piu' trascritti associati a uno stesso gene, in accordo con i modelli concettuali dell'annotazione genica.

Esistono diverse versioni del formato GFF. Le versioni piu' datate supportano solo gerarchie limitate, mentre la versione piu' recente estende il modello per consentire la rappresentazione di relazioni gerarchiche arbitrarie tra feature. Questa evoluzione rende il formato particolarmente adatto alla descrizione di genomi complessi e di strutture trascrizionali articolate.

Nel contesto dei formati di file biologici, il formato GFF rappresenta una soluzione modulare per la gestione delle annotazioni, complementare ai formati integrati che combinano sequenza e annotazioni nello stesso file. La sua diffusione e' dovuta alla semplicita' sintattica, alla flessibilita' semantica e alla compatibilita' con la maggior parte degli strumenti di analisi e visualizzazione genomica.
