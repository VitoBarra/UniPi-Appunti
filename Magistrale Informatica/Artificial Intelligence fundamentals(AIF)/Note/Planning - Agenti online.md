---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning - Agenti online
---
gli [[Agenti Razionali|agenti]] di **planning online** per [[Planning - Domini incerti|domini incerti]] operano in [[Definizione di Problemi-Ambienti|ambienti dinamici o parzialmente sconosciuti]], l’agente non può pianificare completamente ***a priori*** e deve pertanto adottare strategie di **online planning** integrate con meccanismi di **replanning**. In questo approccio, pianificazione ed esecuzione si alternano ciclicamente, consentendo all’agente di adattare il comportamento in tempo reale sulla base delle informazioni percepite e degli esiti delle azioni già eseguite.  
Durante l’esecuzione, l’agente effettua un monitoraggio continuo che comprende tre livelli principali:  
- **Action monitoring**, per verificare che le precondizioni delle azioni siano ancora soddisfatte prima dell’esecuzione;  
- **Plan monitoring**, per assicurarsi che il piano residuo sia ancora applicabile e conducente al goal;  
- **Goal monitoring**, per accertare che l’obiettivo non sia già stato raggiunto o modificato nel frattempo.  
Quando una di queste condizioni viene violata, l’agente attiva un processo di **replanning**, generando un nuovo piano coerente con il proprio stato epistemico aggiornato. Questo meccanismo permette di recuperare da azioni fallite, precondizioni non modellate o eventi esogeni, incrementando la **robustezza** e la **flessibilità** dell’agente. Il processo di online planning combina quindi la valutazione delle precondizioni e degli effetti delle azioni con l’integrazione dei nuovi percetti, aggiornando iterativamente il belief state e riprogrammando eventuali azioni future. L’agente può scegliere tra diverse strategie di monitoraggio: l’**action monitoring** consente di reagire immediatamente a singole discrepanze, ma può portare a comportamenti meno intelligenti se il piano complessivo diventa inefficace; il **plan monitoring** valuta la validità dell’intero piano residuo, permettendo di interrompere l’esecuzione di sequenze destinate al fallimento e di sfruttare eventuali successi accidentali per ridurre i costi complessivi.  In questo contesto, il replanner può selezionare sequenze alternative di azioni o cercare punti di recupero nel piano originale per minimizzare il costo totale, composto dalla parte di riparazione e dalla prosecuzione verso il goal. La scelta tra risolvere un problema in anticipo o lasciare margine al replanning dipende dai costi e dalle probabilità degli eventi previsti, mentre l’apprendimento dai fallimenti consente di aggiornare il modello del mondo, migliorando progressivamente l’efficacia delle strategie di ripristino.

![[IMG - Planning - online replanning.png]]
