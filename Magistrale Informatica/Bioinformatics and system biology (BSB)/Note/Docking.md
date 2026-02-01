---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Docking
---
Il **docking** è una tecnica di modellizzazione molecolare basata sull’[[Energia Molecolare e conformazioni|energia]], utilizzata per prevedere come due [[molecole|molecole]] possano riconoscersi e legarsi tra loro, tipicamente un [[Recettori e ligandi|ligando e un recettore]] macromolecolare. Il problema centrale del docking consiste nel determinare la **posa di legame**, cioè la specifica configurazione con cui il ligando si inserisce nel sito attivo del recettore. Una **posa** è definita da:
- posizione del ligando nella cavità  
- orientamento spaziale  
- [[Energia Molecolare e conformazioni|conformazione]] interna del ligando  

L’obiettivo è identificare configurazioni compatibili dal punto di vista sterico e capaci di massimizzare interazioni stabilizzanti (legami a idrogeno, contatti idrofobici, interazioni elettrostatiche). Il docking assume quindi che l’assetto più plausibile corrisponda a un minimo della superficie energetica del complesso, interpretabile come configurazione di legame più stabile.  
![[IMG - esmpio di Docking.png]]

Poiché la struttura tridimensionale di molte proteine bersaglio può essere determinata sperimentalmente (ad esempio tramite [[Cristallografia a raggi X|cristallografia a raggi X]]), è possibile analizzare cavità e siti di legame specifici. Il docking permette allora di valutare se un ligando sia in grado di inserirsi in tali regioni, esplorando rotazioni, traslazioni e piccole variazioni conformazionali per adattarsi [[Geometrica Molecolare|geometricamente]] e ridurre repulsioni steriche.  
![[IMG - docking molecola bioattiva.png]]

## Software per l’auto-docking
I software per l’auto-docking eseguono automaticamente la generazione e valutazione di molte pose candidate. Nella maggior parte dei casi il [[Recettori e ligandi|ligando]] viene trattato come flessibile, mentre il [[Recettori e ligandi|recettore]] viene spesso considerato rigido per semplificare il problema computazionale.

### DOCK e FlexX
Il **DOCK** è un algoritmo di [[docking|docking]] che genera numerose pose del ligando all’interno del sito di legame, descrivendo la cavità tramite insiemi di sfere (*spheres*). Queste sfere approssimano il volume del pocket e i loro centri rappresentano punti geometrici accessibili, cioè posizioni probabili che possono essere occupate dagli atomi del ligando. I centri delle sfere vengono quindi utilizzati come guide per collocare il ligando in configurazioni stericamente compatibili con la cavità. Le pose ottenute vengono valutate tramite una funzione di scoring, che permette di stimare l’affinità di legame e selezionare le configurazioni più plausibili.  
![[IMG - dockering software.png]]

La flessibilità del ligando in DOCK viene trattata tramite la strategia **anchor-first**, in cui la porzione più grande e rigida della molecola (anchor) viene prima orientata rigidamente nel sito attivo facendo coincidere i centri degli atomi pesanti dell’anchor con i centri delle sfere che descrivono la geometria della cavità recettoriale. Diverse orientazioni dell’anchor vengono ottimizzate mediante scoring e minimizzazione energetica, quindi classificate e raggruppate tramite **root mean squared deviation (RMSD)** per eliminare pose ridondanti. L’RMSD misura quanto due pose del ligando siano simili tra di lodo  dal punto di vista geometrico, confrontando le coordinate degli stessi atomi (tipicamente atomi pesanti) dopo sovrapposizione rigida:  $$RMSD=\sqrt{\frac{1}{N}\sum_{i=1}^{N}\big|\vec r_i-\vec r_i^{\,ref}\big|^2}$$
Una volta selezionate le migliori orientazioni dell’anchor, la molecola viene suddivisa in segmenti flessibili non sovrapposti, che vengono ricostruiti progressivamente attorno all’anchor a partire dagli strati più interni del sito di legame. I segmenti vengono riattaccati in modo incrementale, assumendo che la forma del binding site limiti naturalmente lo spazio conformazionale accessibile e favorisca solo le conformazioni più rilevanti per la geometria del recettore.  
![[IMG - layer in docking.png]]


Il **FlexX** è un algoritmo di [[docking|docking]] che utilizza anch’esso una costruzione incrementale per trattare la flessibilità del ligando. A differenza di DOCK, il posizionamento del frammento rigido principale e dei sostituenti avviene guidato da interazioni geometricamente restrittive, sfruttando tecniche di clustering delle pose per selezionare configurazioni compatibili con il sito attivo.

### AutoDock e GOLD
Gli algoritmi **AutoDock** e **GOLD** sono metodi di [[docking|docking]] basati su [[Ricerca Generativa-Evolutiva|algoritmi genetici]] per esplorare lo spazio conformazionale del ligando. In entrambi i casi, le variabili strutturali (rotazioni, traslazioni e torsioni interne) sono codificate come geni riuniti in cromosomi, e ogni posa viene valutata tramite una funzione di fitness legata all’energia di interazione.
L’esplorazione conformazionale avviene tramite evoluzione iterativa di una popolazione di soluzioni:
- **inizializzazione**: generazione casuale di pose candidate  
- **selezione**: scelta delle pose con fitness più elevata (miglior scoring energetico)  
- **riproduzione**: creazione di nuove pose tramite crossover e mutazione  
- **migrazione**: scambio di soluzioni tra sottopopolazioni per aumentare la diversità  
Ogni generazione produce nuove configurazioni che condividono caratteristiche delle pose migliori, guidando la ricerca verso minimi energetici sempre più favorevoli.  
![[IMG - procedura Autodock.png]]
**AutoDock** e **GOLD** usano entrambi algoritmi genetici, ma differiscono principalmente per strategia di ottimizzazione e funzione di scoring:
- **AutoDock** impiega un **Lamarckian Genetic Algorithm**, in cui ogni posa viene migliorata anche tramite minimizzazione locale; il risultato dell’ottimizzazione viene incorporato nelle generazioni successive, favorendo una convergenza più rapida verso minimi energetici.
- **GOLD** utilizza invece funzioni di scoring più empiriche e calibrate su complessi sperimentali, risultando particolarmente efficace nel ranking delle pose e nella selezione delle configurazioni più compatibili con il sito di legame.


### F.R.E.D.
Il **F.R.E.D.** (*Fast Rigid Exhaustive Docking*) è un metodo di [[docking|docking]] che utilizza come input una libreria multiconformazionale di ligandi precalcolati e un recettore rigido. La strategia di F.R.E.D. consiste nel valutare in modo esaustivo tutte le possibili posizioni di ciascun conformero all’interno del sito attivo, tramite rotazioni e traslazioni rigide.

Questo approccio evita completamente i problemi di campionamento tipici dei metodi stocastici (come Monte Carlo o algoritmi genetici), poiché l’esplorazione è deterministica ed esaustiva. Tuttavia, l’efficacia del metodo dipende fortemente dalla qualità della libreria multiconformazionale iniziale: è quindi necessario un campionamento conformazionale accurato prima del docking, affinché i conformeri disponibili rappresentino realisticamente quelli accessibili al ligando.

### Funzioni di scoring
Le **funzioni di scoring** sono basate sull’assunzione che l’affinità di legame possa essere rappresentata come somma di contributi energetici indipendenti. Esse sono necessarie sia dal punto di vista qualitativo che quantitativo, poiché un algoritmo di docking genera per ogni ligando un grande numero di pose candidate.
Il ruolo di una scoring function è quindi duplice:
- classificare le pose generate per uno stesso ligando, selezionando quella migliore (*top-scored pose*)  
- confrontare ligandi diversi, stimandone le affinità relative di legame  
In generale, le scoring functions valutano le principali forze responsabili del riconoscimento molecolare, tra cui:
- **interazioni idrofobiche**  
- **legami a idrogeno**  
- **interazioni elettrostatiche**
Le **interazioni idrofobiche** derivano dalla tendenza di superfici non polari a ridurre il contatto con l’acqua. Un soluto idrofobico induce un ordine nelle molecole di solvente circostanti, diminuendo l’entropia; l’aggregazione di gruppi non polari minimizza tale effetto e libera molecole d’acqua, producendo un guadagno entropico complessivo. L’occupazione di tasche idrofobiche del recettore aumenta inoltre le attrazioni van der Waals, contribuendo significativamente all’affinità di legame.  
![[IMG - effetti edrofobici.png]]
I **legami a idrogeno** sono interazioni fortemente direzionali che contribuiscono al corretto posizionamento del ligando nel sito attivo, fornendo elevata specificità geometrica. Tuttavia, il loro contributo alla libera energia di legame non è sempre dominante, poiché la formazione di un nuovo legame avviene a spese di legami preesistenti con il solvente. La desolvatazione di donatori e accettori può compensare parzialmente il guadagno energetico. In modo schematico: $$\Delta G_{legame}\approx\Delta H-T\Delta S$$Le **interazioni elettrostatiche** avvengono tra gruppi polari o carichi e possono includere attrazioni coulombiane e salt bridges. Esse risultano spesso più intense dei legami a idrogeno neutri e contribuiscono in modo rilevante alla stabilizzazione del complesso ligando-recettore, in particolare in presenza di residui carichi nel sito di legame.  
![[IMG - Positively and negatively charded.png]]


## Affidabilità del docking
L’**affidabilità del docking** valuta quanto un algoritmo sia capace di ricostruire pose di legame realistiche. Il criterio operativo consiste nel confrontare pose predette con pose sperimentali note (tipicamente da [[Cristallografia a raggi X|cristallografia]]), misurando lo scostamento geometrico tramite **RMSD** calcolato sugli atomi del ligando (di norma atomi pesanti) dopo sovrapposizione rigida del recettore.

Il **self-docking** è il test standard per valutare l’affidabilità di un algoritmo di docking. Si parte da un **complesso ligando–proteina cristallografico**, in cui la posa sperimentale del ligando è nota, e si procede secondo lo schema
- separazione del complesso in recettore e ligando  
- eventuale **ricerca conformazionale** del ligando per generare conformeri accessibili  
- docking dello stesso ligando nel sito attivo della stessa proteina  
- confronto tra posa predetta e posa cristallografica tramite **RMSD**  
Un valore basso di RMSD indica che l’algoritmo ricostruisce correttamente l’assetto sperimentale, mentre valori elevati segnalano una predizione non accurata. Poiché il recettore è già conformazionalmente “adattato” a quel ligando, il self-docking rappresenta un test relativamente favorevole.  
![[IMG - affidabilita docking self docking.png]]

Il **self-docking multiplo** ripete lo stesso test su molte coppie ligando–proteina, producendo una collezione di valori RMSD. L’obiettivo è stimare la robustezza media del protocollo e identificare casi sistematicamente difficili (es. ligandi molto flessibili, siti molto aperti, contributi di solvatazione importanti).  
![[IMG - affidabilita self docking multiple.png]]

Il **cross-docking** valuta la capacità dell’algoritmo di generalizzare, dockando ligandi in recettori diversi ma correlati (tipicamente strutture diverse della stessa proteina o proteine omologhe). Il flusso è:
- si dispone di più complessi cristallografici (Lig A–Prot A, Lig B–Prot B, …)  
- ogni ligando viene dockato non solo nella propria proteina, ma anche nelle altre (Lig A in Prot B, Prot C, …)  
- si confrontano le pose predette con le rispettive pose sperimentali tramite RMSD  

Questo test è più severo perché introduce il problema dell’**adattamento del sito attivo**: la struttura del recettore può essere conformazionalmente “modellata” sul proprio ligando cristallografico, quindi un ligando diverso potrebbe richiedere un riarrangiamento che un docking con recettore rigido non può descrivere completamente.  
![[IMG - cross docking.png]]
L’analisi di cross-docking viene spesso riassunta in una matrice ligandi × proteine, in cui ogni cella contiene l’RMSD ottenuto per quel docking specifico. La matrice evidenzia:
- quanto un ligando riesca a posarsi correttamente su recettori alternativi  
- quali recettori siano “più permissivi” o “più selettivi”  
- pattern di fallimento legati a flessibilità del sito, presenza di acqua strutturata, o cambiamenti di side chains  

Spesso si calcola anche un valore medio (es. **average RMSD**) come indicatore globale della qualità del protocollo, interpretando in modo qualitativo che RMSD più bassi corrispondono a docking più affidabili.  
![[IMG - cross-docking analysis.png]]
