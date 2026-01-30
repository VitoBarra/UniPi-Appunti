---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Tecniche di visualizzazione molecolare
---
Nel contesto della [[Modellazione molecolare|modellazione molecolare]], le [[molecole|molecole]] possono essere visualizzate tramite diversi metodi di [[Rendering|rendering]] ciascuno dei quali evidenzia aspetti differenti della struttura:
- **Line** (*wireframe*): rappresentazione basata su segmenti che delineano i legami  
- **Stick**: legami rappresentati come cilindri  
- **Ball & Stick**: atomi rappresentati come sfere e legami come cilindri  
- **CPK**: molecola rappresentata come insieme di sfere basate sui raggi di van der Waals  

Queste modalità sono riassunte in:
![[IMG - tipi di rappresentazione di una molecola.png]]

Le **[[molecole|macromolecole]]**, come le [[proteine|proteine]], possono essere visualizzate con tecniche analoghe a quelle delle piccole molecole oppure tramite rappresentazioni specifiche.

Una visualizzazione generale in modalità **stick** è mostrata in:
![[IMG - rappresentazione di una proteina.png]]

Una rappresentazione specifica è il **Cα trace**, che mostra solamente la catena degli atomi di $\alpha$-Carbon ignorando le catene laterali (**gruppi R**):![[IMG - rapresentazione delle proteine Calpha trace.png]]

Le rappresentazioni **ribbon** prendono in considerazione la struttura secondaria, evidenziando elementi come $\alpha$-eliche e $\beta$-foglietti:
![[IMG - Ribon rapresentation.png]]

L’**$\alpha$-elica**, visibile in:
![[IMG - rapresentazione ribon alpha helix.png]]
è una conformazione destrorsa in cui ogni gruppo N–H dello scheletro peptidico forma un legame a idrogeno con il gruppo C=O del residuo situato quattro posizioni prima, secondo lo schema $(i + 4)$.

Il **$\beta$-foglietto**, illustrato in:![[IMG - rapresentazione di proteine beta foglietti.png]]
    è costituito da filamenti $\beta$ affiancati e stabilizzati da una rete estesa di legami a idrogeno tra gruppi N–H e C=O appartenenti ai filamenti adiacenti.