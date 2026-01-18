---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Formato GFF
---
Il **formato GFF** (General Feature Format) è un formato testuale standard utilizzato per rappresentare **annotazioni genomiche** in modo strutturato e indipendente dalla sequenza biologica. Esso è impiegato per descrivere la posizione e le caratteristiche di elementi funzionali come geni, trascritti, esoni e regioni codificanti. Il formato GFF svolge un ruolo centrale nell’organizzazione delle informazioni contenute nelle [[Banche dati biologiche]] e nella loro integrazione con strumenti di visualizzazione come il Genome browser.

Un file GFF non contiene la sequenza genomica, ma fa riferimento a una sequenza di riferimento esterna, tipicamente rappresentata in [[Formato FASTA]]. Le annotazioni sono espresse come una collezione di **feature**, ciascuna associata a una regione genomica definita da coordinate. Questa separazione tra sequenza e annotazione consente una maggiore flessibilità nell’aggiornamento delle informazioni e favorisce il confronto tra annotazioni provenienti da fonti diverse.

Dal punto di vista strutturale, il formato GFF è organizzato come un file di testo tab-delimitato composto da **nove colonne**, ciascuna delle quali descrive un aspetto specifico della feature annotata:

- **colonna 1**: identificatore della sequenza di riferimento;
- **colonna 2**: sorgente dell’annotazione, che indica l’origine del dato;
- **colonna 3**: tipo di feature annotata, come gene, esone o regione codificante;
- **colonne 4 e 5**: coordinate genomiche di inizio e fine della feature;
- **colonna 6**: punteggio associato alla feature, quando disponibile;
- **colonna 7**: filamento genomico, che indica l’orientamento della feature;
- **colonna 8**: fase di lettura, rilevante per le regioni codificanti;
- **colonna 9**: insieme di attributi che descrivono proprietà aggiuntive della feature.

La nona colonna svolge un ruolo fondamentale, poiché consente di associare alla feature una serie di coppie chiave–valore che ne specificano l’identità e le relazioni con altre feature. Attraverso questi attributi è possibile rappresentare strutture gerarchiche, come l’organizzazione di più esoni all’interno di un trascritto o di più trascritti associati a uno stesso gene, in accordo con i modelli concettuali dell’annotazione genica.

Esistono diverse versioni del formato GFF. Le versioni più datate supportano solo gerarchie limitate, mentre la versione più recente estende il modello per consentire la rappresentazione di relazioni gerarchiche arbitrarie tra feature. Questa evoluzione rende il formato particolarmente adatto alla descrizione di genomi complessi e di strutture trascrizionali articolate.

Nel contesto dei [[Formati di file biologici]], il formato GFF rappresenta una soluzione modulare per la gestione delle annotazioni, complementare ai formati integrati che combinano sequenza e annotazione nello stesso file. La sua diffusione è dovuta alla semplicità sintattica, alla flessibilità semantica e alla compatibilità con la maggior parte degli strumenti di analisi e visualizzazione genomica.
