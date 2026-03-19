---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Interactomics
---
La [[Interactomics|interactomics]] studia l'insieme delle interazioni tra biomolecole all'interno di un sistema biologico, cioe' l'**interactoma**. L'oggetto di analisi non e' la singola molecola isolata, ma la struttura delle relazioni che collega [[proteine|proteine]], [[Nucleotidi|acidi nucleici]], metaboliti e altri regolatori in un contesto funzionale comune.
Le interazioni considerate possono includere:
- interazioni **proteina-proteina**;
- interazioni **proteina-DNA**;
- interazioni **proteina-RNA**;
- interazioni tra geni, metaboliti e altri regolatori.
In [[Introduzione al System Biology|systems biology]] questo approccio consente di passare dall'elenco delle componenti alla ricostruzione delle loro dipendenze funzionali.

L'**interactoma** non coincide con una rete completa e definitiva, ma con una ricostruzione progressiva ottenuta integrando esperimenti, curazione manuale e risorse computazionali. Per questo la sua descrizione dipende dalla qualita' dei dati disponibili, dalla tecnologia sperimentale usata e dal contesto biologico in cui l'interazione e' stata osservata.

#### Interactoma proteina-proteina
La componente proteina-proteina dell'interactoma e' una delle piu' studiate e viene comunemente rappresentata tramite [[Protein-Protein interaction network (PPIN)|PPI network]]. In questo caso il punto critico non e' soltanto la rappresentazione della rete, ma soprattutto la qualita' dei database da cui le interazioni vengono recuperate e il grado di copertura effettiva dell'interactoma osservabile.

Dal punto di vista delle fonti, i database si distinguono in modo schematico in:
- **database primari o curati**: raccolgono interazioni supportate da evidenza sperimentale diretta; hanno in genere precisione maggiore ma copertura piu' limitata; risorse tipiche sono [BioGRID](https://thebiogrid.org/) e [IntAct](https://www.ebi.ac.uk/intact/);
- **database integrativi**: aggregano evidenze eterogenee, includendo dati sperimentali, annotazioni derivate, text mining e predizioni computazionali; offrono copertura piu' ampia ma precisione piu' variabile; una risorsa centrale e' [STRING](https://string-db.org/), che associa a ogni interazione uno **score di confidenza** $w\in[0,1]$.![[IMG - Protein-Protein interaction network - STRING.png]]
L'uso dei database integrativi richiede quindi un filtraggio esplicito della confidenza, per esempio imponendo soglie del tipo $w>0.7$, cosi' da ridurre il rumore e selezionare interazioni piu' affidabili. 


Nei [[Data Base (DB)|database]] di interazione, la copertura del **proteoma** indica quante [[proteine|proteine]] compaiono almeno una volta come nodi della rete, cioe' risultano associate ad almeno un'interazione annotata, mentre la copertura dell'**interactoma** riguarda quante interazioni sono effettivamente note rispetto a quelle stimate. Il punto principale e' che il numero di proteine presenti nei database e' gia' relativamente ben coperto, mentre il numero di interazioni note resta molto piu' lontano dal valore stimato per l'interactoma umano. In termini qualitativi, questo significa che e' piu' facile sapere **quali proteine compaiono nella rete** che conoscere in modo completo **con chi interagiscono**.
Nel caso di *Homo sapiens*, l'**interactoma umano** sono state stimate **650.000 interazioni**, mentre le mappe disponibili ne coprono soltanto una frazione. Il limite centrale e' quindi il **problema di copertura**, che riguarda non solo quante interazioni siano note, ma anche quali porzioni della rete risultino effettivamente osservabili:
- **Bias di osservazione**. Le proteine più studiate accumulano più interazioni annotate non necessariamente perchè siano sempre più connesse in senso biologico, ma perchè sono state sottoposte a un numero maggiore di esperimenti; ne segue un effetto di campionamento che altera la forma apparente della rete e condiziona anche le misure topologiche.
- **Specificità di contesto**. Molte interazioni sono valide solo in particolari tessuti, tipi cellulari, condizioni fisiologiche o stati patologici, mentre i database aggregano spesso queste evidenze in una rappresentazione unica e statica. L'interactoma osservato va quindi interpretato come una sovrapposizione parziale di contesti diversi, non come un network universale e immutabile.

Una proprietà caratteristica dei [[Data Base (DB)|database]] di interazione è invece la relativa stabilità degli [[Network Science|hub]]: i nodi ad alto grado sono in genere più facili da osservare sperimentalmente e sono stati probabilmente identificati già nelle fasi iniziali della costruzione dei database, mentre l'espansione successiva riguarda più spesso nodi periferici e interazioni poco documentate.


I database confrontati mostrano inoltre una sovrapposizione elevata a livello di proteine censite, mentre differiscono di più a livello di interazioni annotate; questo indica che la parte meno stabile della ricostruzione non è l'elenco dei nodi, ma quello degli archi. 
**PICKLE** è un **meta-database** che aggrega interazioni provenienti da più risorse, quindi va interpretato come una unione integrata di database diversi, utile per aumentare la copertura ma non sufficiente a eliminare il problema dell'incompletezza.
![[IMG - copertura interactome vs  proteome.png]]

