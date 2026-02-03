---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Formato Mol2
---
Il **formato Mol2** è un formato testuale standard impiegato per descrivere la **struttura tridimensionale** di piccole molecole e ligandi, in particolare nel contesto della [[Chimica computazionale|Chimica computazionale]] e della [[Progettazione di farmaci basata sul recettore|Progettazione di farmaci basata sul recettore]]. Nato come formato di supporto per i software SYBYL, il Mol2 si è affermato come uno dei principali formati utilizzati per rappresentare molecole organiche in modo più ricco rispetto ai formati puramente geometrici, collocandosi tra i [[Formati di file biologici|Formati di file biologici]] complementari al [[Formato PDB|Formato PDB]].

Un file Mol2 descrive una molecola come insieme di **atomi e legami**, includendo non solo le coordinate cartesiane $(x,y,z)$, ma anche informazioni chimiche fondamentali come il tipo atomico, la natura dei legami e la carica parziale. Questa caratteristica rende il formato particolarmente adatto alla rappresentazione di ligandi in docking molecolare e simulazioni di [[Dinamica molecolare|Dinamica molecolare]], dove la descrizione della connettività chimica è essenziale per valutare interazioni e stabilità conformazionale.

Dal punto di vista strutturale, il formato Mol2 è organizzato in sezioni identificate da record introdotti dal simbolo `@<TRIPOS>`. Le sezioni principali sono `MOLECULE`, `ATOM` e `BOND`, che contengono le informazioni atomiche e topologiche necessarie alla ricostruzione completa della molecola.

Nella sezione `@<TRIPOS>ATOM`, ogni riga rappresenta un atomo ed è suddivisa in campi con significato chimico preciso:

- **Atom ID**: identificatore numerico progressivo che distingue univocamente ogni atomo.
- **Atom name**: nome simbolico dell’atomo, spesso associato alla convenzione del gruppo funzionale.
- **X, Y, Z**: coordinate cartesiane tridimensionali $(x,y,z)$ dell’atomo nello spazio, espresse in ångström.
- **Atom type**: tipo atomico secondo una classificazione chimica (ad esempio `C.3`, `N.am`, `O.co2`), utilizzata nei campi di forza.
- **Substructure ID**: identificatore della sottostruttura o residuo a cui l’atomo appartiene.
- **Substructure name**: nome della sottostruttura, utile per distinguere frammenti molecolari o residui.
- **Charge**: carica parziale associata all’atomo, fondamentale per descrivere interazioni elettrostatiche.

La sezione `@<TRIPOS>BOND` definisce invece la connettività tra atomi, permettendo di rappresentare esplicitamente la struttura chimica:

- **Bond ID**: numero progressivo che identifica il legame.
- **Origin atom ID**: identificatore dell’atomo di origine del legame.
- **Target atom ID**: identificatore dell’atomo di destinazione del legame.
- **Bond type**: natura chimica del legame, ad esempio singolo (`1`), doppio (`2`), triplo (`3`), aromatico (`ar`) o ammidico (`am`).

Questa doppia descrizione, geometrica e topologica, permette di ricostruire la molecola non solo come configurazione spaziale, ma anche come grafo chimico. In questo senso il formato Mol2 rappresenta uno strumento centrale nella [[Modellazione Molecolare|Modellazione Molecolare]] e nello studio dell’[[Energia Molecolare e conformazioni|Energia Molecolare e conformazioni]], poiché consente di associare alla geometria anche proprietà elettroniche e parametri utili nei campi di forza computazionali.

Nel confronto con il [[Formato PDB|Formato PDB]], il Mol2 si distingue per una maggiore enfasi sulla descrizione chimica dettagliata delle molecole di piccole dimensioni. Mentre il PDB è principalmente orientato alla rappresentazione strutturale di macromolecole biologiche e complessi proteici, il Mol2 è particolarmente adatto per ligandi, cofattori e composti farmaceutici, integrandosi nei flussi di lavoro che combinano bioinformatica strutturale e chimica dei farmaci.
![[IMG - Esempio Formato Mol2.png]]
