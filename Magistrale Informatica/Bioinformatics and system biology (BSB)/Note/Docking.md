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
Il **docking** rappresenta un’operazione basata sull’[[Energia Molecolare e conformazioni|energia]], finalizzata all’esplorazione dei possibili modi di legame tra due molecole che interagiscono. Serve come guida per individuare l’orientamento preferenziale di un ligando rispetto a una macromolecola, consentendo al ligando di adattarsi attraverso piccole variazioni conformazionali per evitare repulsioni steriche e favorire interazioni stabilizzanti con il recettore. In questo contesto, il complesso molecolare tende verso configurazioni caratterizzate da una diminuzione dell’energia complessiva, riconducibile in modo schematico al minimo di $$E_{tot}$$.  
![[IMG - esmpio di Docking.png]]

A partire dalla struttura tridimensionale di una proteina bersaglio, è possibile progettare composti in grado di inserirsi in una cavità specifica. L’orientamento iniziale del ligando viene progressivamente modificato, insieme alla sua conformazione, con l’obiettivo di massimizzare le interazioni intermolecolari favorevoli. Il processo termina quando il complesso raggiunge una condizione di minima energia, interpretabile come configurazione più stabile dal punto di vista termodinamico.  
![[IMG - docking molecola bioattiva.png]]

I software di docking più diffusi eseguono generalmente un docking flessibile del ligando, considerando il recettore come entità rigida. Nel caso di DOCK e FlexX, l’algoritmo genera numerose possibili posizioni e conformazioni del ligando all’interno del sito di legame, descrivendo la cavità tramite insiemi di sfere i cui centri fungono da potenziali posizioni per gli atomi del ligando. La valutazione delle pose avviene tramite una funzione di scoring che permette di stimare la qualità dell’assetto ottenuto.  
![[IMG - dockering software.png]]

La flessibilità del ligando viene trattata tramite la strategia anchor-first, individuando la porzione più grande e rigida della molecola e orientandola rigidamente nel sito attivo. Le diverse orientazioni dell’anchor vengono ottimizzate sulla base della funzione di scoring e successivamente classificate, raggruppate per RMSD e filtrate. Le parti flessibili del ligando vengono poi ricostruite attorno all’anchor in modo progressivo, sfruttando la geometria del sito di legame come vincolo naturale alla ricerca conformazionale.  
![[IMG - layer in docking.png]]

Autodock e GOLD impiegano algoritmi genetici per esplorare lo spazio conformazionale dei ligandi flessibili. Le variabili strutturali sono codificate come geni riuniti in cromosomi, valutati tramite una funzione di fitness correlata all’energia di interazione. Le operazioni di mutazione, crossover e migrazione consentono l’evoluzione iterativa di popolazioni di soluzioni, favorendo quelle con fitness più elevata e guidando il sistema verso configurazioni energeticamente più favorevoli.  
![[IMG - procedura Autodock.png]]

Nel caso di F.R.E.D., l’approccio è basato su un’esplorazione esaustiva e rigida delle possibili posizioni dei conformeri precalcolati del ligando nel sito attivo, mediante rotazioni e traslazioni. Questa strategia riduce i problemi di campionamento tipici dei metodi stocastici, richiedendo però una generazione accurata delle librerie multiconformazionali. Le funzioni di scoring assumono che l’affinità di legame possa essere descritta come somma di contributi indipendenti, consentendo il confronto tra pose di uno stesso ligando e tra ligandi differenti.

Le interazioni che dominano il riconoscimento molecolare comprendono principalmente il contributo idrofobico, i legami a idrogeno e le interazioni elettrostatiche. Il contributo idrofobico è associato alla tendenza delle superfici non polari a interagire tra loro, riducendo l’esposizione all’acqua e favorendo un aumento di entropia; tale comportamento contribuisce in modo cumulativo all’aumento dell’affinità di legame.  
![[IMG - effetti edrofobici.png]]

I legami a idrogeno sono direzionali e favoriscono il corretto posizionamento dei frammenti molecolari nel sito attivo. Il loro contributo alla libera energia di legame non è sempre dominante, poiché la formazione di nuovi legami avviene contestualmente alla desolvatazione di ligando e recettore, con compensazioni energetiche. In termini schematici, il bilancio può essere espresso come $$\Delta G_{legame} \approx \Delta H - T\Delta S$$, dove i contributi entalpici e entropici concorrono al riconoscimento.

Le interazioni elettrostatiche coinvolgono gruppi polari o carichi e risultano spesso più intense rispetto ai legami a idrogeno neutri. Residui carichi o polari nel sito di legame contribuiscono alla stabilizzazione del complesso attraverso attrazioni coulombiane, modulando in modo significativo l’affinità complessiva del sistema.


## Affidabilità del docking
![[IMG - affidabilita docking self docking.png]]
![[IMG - affidabilita self docking multiple.png]]
![[IMG - cross docking.png]]
![[IMG - cross-docking analysis.png]]