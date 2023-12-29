---
type: nota
course: Data Base
topic: 
tags:
  - FDI
Parent MOC: "[[Data Base (DB)]]"
---

# Modello dati - Modello Entita-Relazioni
---
Il _modello entità-relazione_ è  [[Modelli di dati|modello dati]] per la _[[Aspetti della modellazione della conoscenza|Modellazione della conoscenza]]_ .
é il modello più popolare per il disegno concettuale di basi di dati. Verrà presentato nella sua forma originaria, estesa successivamente per trattare altri aspetti, in particolare la generalizzazione.

Rispetto al [[Modello dati - Modello ad oggetti|modello ad oggetti]], questo modello non tratta aspetti procedurali (metodi) né gerarchie di inclusione tra collezioni, non distingue collezioni e tipi, non supporta alcun meccanismo di ereditarietà. 
Definisce però un meccanismo per modellare direttamente le associazioni, e in particolare le associazioni non binarie o con proprietà.

Più in dettaglio, il modello prevede due meccanismi di astrazione distinti: uno per modellare insiemi di entità, con le relative proprietà, ed un altro per modellare le associazioni (chiamate "relazioni"). Le collezioni sono qui chiamate tipi di entità, e gli attributi dei loro elementi possono assumere solo valori di tipo primitivo.

Il formalismo grafico usato per rappresentare i meccanismi di astrazione del modello entità-relazione è chiamato diagrammi entità-relazione (entity-relationship diagrams), o diagrammi ER, e, come nel caso del modello ad oggetti, i rettangoli rappresentano tipi di entità e gli archi interrotti da un rombo rappresentano associazioni. Anche qui gli archi sono etichettati con le proprietà strutturali delle associazioni, codificate da una coppia di interi (min, max) che rappresentano, come nei descrittori testuali presentati in precedenza per le associazioni nel formalismo ad oggetti, il numero minimo e massimo di volte che un elemento di un tipo di entità può partecipare alla relazione.


![[IMG_1043.jpeg]]
Questo modello è stato successivamente esteso per trattare attributi con valori non primitivi e le gerarchie fra tipi di entità, rendendo la notazione grafica molto simile a quella di un modello ad oggetti. 
![[IMG_1045.jpeg]]