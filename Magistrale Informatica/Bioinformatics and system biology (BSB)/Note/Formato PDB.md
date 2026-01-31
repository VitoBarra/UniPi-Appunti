---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Formato PDB
---
Il **formato PDB** (Protein Data Bank) è un formato testuale standard utilizzato per rappresentare la **struttura tridimensionale** di macromolecole biologiche, in particolare proteine, acidi nucleici e complessi molecolari. Esso costituisce il principale mezzo di distribuzione dei dati strutturali ottenuti tramite tecniche sperimentali come la cristallografia a raggi X, la risonanza magnetica nucleare e la microscopia crioelettronica, collocandosi nel contesto delle [[Banche dati biologiche]] e in continuità con i concetti trattati in [[Proteine]] e [[Biochimica]].

Un file PDB descrive una macromolecola come un insieme di **atomi nello spazio tridimensionale**, ciascuno caratterizzato da coordinate cartesiane $(x, y, z)$. Questa rappresentazione consente di modellare la geometria molecolare e di analizzare la relazione tra struttura e funzione, aspetto centrale in ambiti come la [[Chimica computazionale]] e la [[Progettazione di farmaci basata sul recettore]]. La struttura tridimensionale rappresentata in un file PDB costituisce spesso il punto di partenza per simulazioni di [[Dinamica molecolare]] e per studi di interazione molecolare.

Dal punto di vista strutturale, il formato PDB è organizzato come una sequenza di record testuali, ciascuno dei quali descrive un particolare aspetto della struttura. Tra i record più rilevanti vi sono quelli che definiscono l’identità della molecola, le catene polipeptidiche, i residui amminoacidici e le coordinate atomiche. Ogni atomo è identificato da un nome, appartiene a un residuo specifico e viene associato a una catena, permettendo di ricostruire la gerarchia strutturale della macromolecola.

Le coordinate atomiche sono espresse in unità di lunghezza standard e consentono di calcolare distanze, angoli e relazioni spaziali tra gli atomi. Queste informazioni sono fondamentali per la descrizione della [[Modellazione Molecolare]] e per la valutazione dell’[[Energia Molecolare e conformazioni]] nei modelli computazionali. Il formato PDB include inoltre campi dedicati alla descrizione di legami, fattori di occupazione e parametri di incertezza, che riflettono la natura sperimentale dei dati strutturali.

Nel contesto dei [[Formati di file biologici]], il formato PDB si distingue dai formati di sequenza e annotazione, poiché non rappresenta una sequenza lineare di simboli biologici, ma una configurazione spaziale tridimensionale. Questa differenza concettuale rende il formato PDB complementare ai formati come [[Formato FASTA]] e [[Formato GenBank]], che descrivono la struttura primaria e l’annotazione funzionale, ma non la conformazione spaziale. Il formato PDB costituisce quindi un elemento centrale per l’integrazione tra bioinformatica strutturale, chimica computazionale e modellistica molecolare.

![[IMG - Esempio file Formato PDB.png]]