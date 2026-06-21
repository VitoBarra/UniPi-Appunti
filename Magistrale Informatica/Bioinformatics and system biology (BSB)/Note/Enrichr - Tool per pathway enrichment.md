---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Enrichr - Tool per pathway enrichment
---
**Enrichr** è un tool web per enrichment di liste di geni, orientato soprattutto ad analisi rapide ed esplorative. Nel contesto di [[Analisi RNA-seq|RNA-seq]] è utile quando si ha una lista di geni differenzialmente espressi e si vuole esplorare rapidamente molte collezioni di gene set.

Enrichr è focalizzato soprattutto su analisi di tipo **ORA-style**, cioè prende una lista di geni e cerca annotazioni sovra-rappresentate. Non è lo strumento principale per una GSEA completa su lista rankata.

La sua forza è la ricchezza delle librerie disponibili, tra cui:
- pathway e ontologie;
- target di transcription factor;
- firme di malattia;
- firme di perturbazione farmacologica;
- interazioni proteina-proteina;
- marker di tipi cellulari;
- dataset e annotazioni da molte sorgenti pubbliche.

Input tipico:
- lista di geni, spesso gene symbol;
- scelta di una o più librerie di gene set.

Output tipici:
- termini arricchiti;
- p-value e adjusted p-value;
- combined score;
- geni della lista che contribuiscono al termine;
- grafici come bar chart e viste di rete.

Enrichr è indicato quando:
- si vuole una prima esplorazione veloce;
- si vogliono confrontare molte librerie diverse;
- interessano ipotesi su transcription factor, farmaci, malattie o marker cellulari;
- serve un'interfaccia web immediata o accesso via API.

Limiti:
- è meno controllato per pipeline statistiche rigorose rispetto a strumenti scriptabili come [[clusterProfiler - Tool per pathway enrichment]];
- l'analisi dipende fortemente dalla libreria scelta;
- una lista di risultati molto lunga può contenere associazioni ridondanti o indirette;
- il background non sempre è gestito con la stessa granularità di altri workflow.

Vedi anche: [[gProfiler - Tool per pathway enrichment]], [[WebGestalt - Tool per pathway enrichment]], [[STRING - Tool per reti PPI ed enrichment]].
