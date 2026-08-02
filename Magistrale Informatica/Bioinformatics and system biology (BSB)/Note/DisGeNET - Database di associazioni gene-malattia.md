---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic: Network Medicine
SubTopic: Gene-disease associations
---

# DisGeNET - Database di associazioni gene-malattia
---
**DisGeNET** è una [[Banche dati biologiche|banca dati biologica]] che integra associazioni tra geni, varianti e malattie provenienti da risorse curate, letteratura scientifica, modelli animali e fonti computazionali.

Una **gene-disease association** (GDA) rappresenta una relazione:$$g \leftrightarrow d$$dove $g$ è un gene e $d$ è una malattia o un fenotipo. 
L'esistenza di un'associazione indica che sono disponibili evidenze che collegano il gene alla malattia, ma non dimostra necessariamente un rapporto causale.

Per ciascuna associazione possono essere disponibili:
- identificatore e simbolo del gene;
- nome e identificatore della malattia;
- fonte dell'associazione;
- pubblicazioni che supportano l'associazione;
- tipo di evidenza;
- **gene-disease association score**.

Lo score riassume la quantità e il tipo di evidenze disponibili. Non rappresenta direttamente la probabilità che il gene causi la malattia.

## Identificatori delle malattie

DisGeNET può rappresentare le malattie mediante identificatori **UMLS CUI** (*Unified Medical Language System Concept Unique Identifier*). Questi identificatori permettono di riconciliare nomi e sinonimi provenienti da vocabolari differenti.

Esempi:
- Rheumatoid Arthritis (RA): `C0003873`;
- Diabetes Mellitus (DM): `C0011849`.

## Utilizzo nella network medicine

In [[Medicine network|network medicine]], DisGeNET viene utilizzato per ottenere un insieme iniziale di geni associati a una malattia. Dopo il filtraggio delle associazioni, questi geni costituiscono i **seed** del [[Medicine network|disease module]].

Il workflow generale è:
1. selezionare una malattia mediante il suo identificatore;
2. recuperare le associazioni gene-malattia;
3. filtrare le associazioni in base a score, fonte e tipo di evidenza;
4. uniformare gli identificatori e i simboli genici;
5. mappare i geni su una [[Protein-Protein interaction network (PPIN)|rete PPI]];
6. analizzare il disease module mediante misure topologiche e di prossimità.

Per rendere l'analisi riproducibile bisogna documentare:
- versione della risorsa e data di accesso;
- identificatore della malattia;
- fonti ed evidenze considerate;
- soglia dello score o altra regola di selezione;
- associazioni eliminate e geni non mappati.

-
## Limiti
- Le malattie e i geni più studiati tendono ad avere più associazioni annotate.
- Le fonti possono avere qualità e livelli di evidenza differenti.
- Alcune associazioni sono predette o inferite.
- I simboli genici possono essere obsoleti o non direttamente mappabili sulla PPI.
- Un'associazione non implica necessariamente causalità.
- L'utilizzo di soglie diverse può modificare dimensione e composizione del disease module.


Vedi anche: [[Medicine network]], [[Protein-Protein interaction network (PPIN)]], [[STRING - Tool per reti PPI ed enrichment]], [[Interactomics]].
