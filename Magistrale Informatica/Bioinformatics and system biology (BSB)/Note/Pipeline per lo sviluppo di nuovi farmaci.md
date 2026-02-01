---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Pipeline per lo sviluppo di nuovi farmaci
---
La **pipeline per lo sviluppo di nuovi farmaci** è un processo sequenziale che comprende fasi scientifiche, tecnologiche, regolatorie ed economiche, progettate per garantire che una molecola immessa sul mercato sia sicura, efficace e di qualità adeguata. L’intero percorso richiede in media 10–13 anni e comporta investimenti elevati, con un tasso di fallimento significativo soprattutto nelle fasi avanzate.  
![[IMG - pipeline per lo sviluppo di una farmaco.png]]

Il processo inizia con l’identificazione della patologia e la comprensione dei meccanismi biologici coinvolti. Questa fase porta all’individuazione e validazione di un **target molecolare** rilevante (enzima, recettore, [[proteine|proteina]] strutturale), la cui modulazione può produrre un beneficio terapeutico.

Segue la fase di **drug discovery**, in cui si ricercano molecole in grado di interagire con il target. In questa fase assume un ruolo centrale il **[[Virtual screeaning|virtual screening]]**, che permette di valutare rapidamente grandi librerie di composti tramite metodi computazionali ([[docking|docking]], [[farmacofori|farmacofori]], similarità), selezionando un numero ristretto di molecole potenzialmente attive.

Attraverso screening sperimentale o virtual screening vengono individuati gli **hit**, ossia composti che mostrano una prima attività biologica misurabile, ma spesso con potenza limitata e proprietà farmacologiche non ancora ottimizzate.

Successivamente gli hit vengono modificati e migliorati per ottenere i **lead compounds**, molecole caratterizzate da maggiore potenza e da proprietà più favorevoli in termini di selettività e stabilità chimica. Il passaggio da hit a lead è iterativo, poiché richiede un bilanciamento tra attività biologica e proprietà chimico-fisiche.  
![[IMG - workflow di generazione di hit-lead counpound.png]]

La fase di **lead optimization** mira a migliorare in modo sistematico parametri come potenza, selettività, solubilità, permeabilità e stabilità metabolica, includendo anche le prime valutazioni di tossicità e farmacocinetica. L’obiettivo è selezionare uno o più **drug candidates**, molecole che soddisfano requisiti sufficienti per essere testate in sistemi biologici complessi.

I drug candidates entrano quindi nella fase **preclinica**, che comprende studi in vitro e in vivo volti a valutare tossicità, farmacodinamica, farmacocinetica e sicurezza generale, oltre a definire un intervallo di dosaggio iniziale.

Superata la preclinica, il composto accede alla **sperimentazione clinica**, articolata in tre fasi principali. La fase I valuta sicurezza e tollerabilità in pochi soggetti, la fase II verifica l’efficacia preliminare e ottimizza il dosaggio, mentre la fase III conferma efficacia e sicurezza su ampie popolazioni.

Dopo il completamento con successo delle fasi cliniche, viene presentata la documentazione alle autorità regolatorie per l’approvazione all’immissione in commercio. Una volta approvato, il farmaco entra nell’utilizzo clinico, ma rimane sottoposto a farmacovigilanza continua nella **fase IV**, che monitora reazioni avverse rare o tardive.

L’elevata complessità e il costo della pipeline rendono fondamentali le fasi iniziali: errori nella selezione del target o nell’identificazione di hit e lead possono condurre a fallimenti tardivi con conseguenze economiche rilevanti. Per questo motivo, strategie integrate sperimentali e computazionali, come il virtual screening, sono essenziali per aumentare la probabilità di successo nello sviluppo di nuovi farmaci.

