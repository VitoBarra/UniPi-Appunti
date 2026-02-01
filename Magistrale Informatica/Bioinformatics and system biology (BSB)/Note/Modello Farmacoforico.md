---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Modello Farmacoforico
---
Un **modello farmacoforico** è una rappresentazione tridimensionale astratta dei requisiti minimi necessari affinché una molecola possa essere riconosciuta e legarsi a un determinato [[Recettori e ligandi|target biologico]]. Esso descrive l’organizzazione spaziale di un insieme definito di **[[Farmacofori|feature farmacoforiche]]** (donatori e accettori di legame a idrogeno, regioni idrofobiche, cariche, centri aromatici), caratterizzate da distanze e vincoli geometrici specifici.

La costruzione di un modello farmacoforico dipende dalle informazioni disponibili e si basa sul principio della **molecular mimicry**, secondo cui molecole chimicamente diverse possono risultare **biologicamente attive** se in grado di riprodurre lo stesso schema di interazioni richiesto dal bersaglio. In una molecola attiva si distinguono elementi strutturali:
- **Essenziali**, direttamente responsabili delle interazioni determinanti per l’attività biologica,  **[[Farmacofori|feature farmacoforiche]]**
- **Non essenziali**, utili solo a mantenere gli elementi essenziali nella corretta disposizione tridimensionale  

In base ai dati noti, si distinguono due approcci di **modellazione farmacoforica**:
- **ligand-based pharmacophore**: il modello è derivato dall’analisi dei ligandi attivi, in assenza di informazioni strutturali sul complesso [[Recettori e ligandi|recettore–ligando]]  
- **structure-based pharmacophore**: il modello è costruito a partire da strutture note del complesso, deducendo le feature dalle interazioni nel sito di legame  
![[IMG - modello farmacoforo Receptor-base.png]]

Quando sono disponibili più [[Recettori e ligandi|ligandi]] di cui si conoscono i conformanti **bioattivi**, si assume che essi condividano lo stesso insieme di elementi farmacoforici responsabili del riconoscimento molecolare.  
![[IMG - esempio molecole con conformanti biattivi non correlate.png]]

L’identificazione degli elementi comuni avviene tramite **sovrapposizione tridimensionale**, evidenziando similarità e differenze strutturali rilevanti. Da questa procedura si può generare un **modello [[Farmacofori|farmacoforo]]** utilizzabile per cercare ligandi compatibili.  
![[IMG - step per ricerca usando le feature.png]]

Nella maggior parte dei progetti farmacoforici, tuttavia, le **conformazioni bioattive** non sono note. Si dispone solo di molecole sperimentalmente attive senza informazioni sulla geometria assunta durante il legame. Poiché una stessa molecola può presentare molti conformeri a bassa energia, è necessario generare un insieme di conformazioni plausibili mediante la [[Ricerca conformazionale|ricerca conformazionale]]. Vengono selezionati solo i [[Energia Molecolare e conformazioni|conformeri a bassa energia]], tipicamente entro una finestra definita, ad esempio $\Delta E \leq 13\ \text{kJ/mol}$ rispetto al conformero più stabile.

Se una molecola presenta $n$ conformeri e un’altra $m$, tutte le combinazioni devono essere considerate nella sovrapposizione sistematica, generando $n \times m$ allineamenti. Le sovrapposizioni che massimizzano la coincidenza delle feature farmacoforiche vengono interpretate come le più rappresentative delle conformazioni bioattive.  
![[IMG - Schema  di confronto tra confirmanti.png]]
