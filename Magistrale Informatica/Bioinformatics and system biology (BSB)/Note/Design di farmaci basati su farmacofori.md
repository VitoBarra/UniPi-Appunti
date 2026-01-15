---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Design di farmaci basati su farmacofori
---
Il **design di farmaci** basati su [[Farmacofori|farmacofori]] è un approccio concettuale e operativo che consente la progettazione di nuove molecole guida a partire da composti biologicamente attivi già noti, purché condividano lo stesso meccanismo d’azione, lo stesso recettore e lo stesso sito di legame. Il principio di base è quello della **molecular mimicry**, secondo cui molecole chimicamente anche molto diverse possono risultare attive se sono in grado di riprodurre un insieme comune di requisiti strutturali e spaziali necessari all’interazione con il bersaglio biologico.

Una [[Molecole|molecola]] biologicamente attiva contiene elementi strutturali
- **essenziali**:  sono direttamente responsabili dell’attività biologica
- **non essenziali**: contribuiscono a mantenere quelli essenziali nella corretta disposizione tridimensionale. 
L’insieme minimo delle caratteristiche strutturali indispensabili per una determinata attività biologica definisce il [[Farmacofori|farmacoforo]].

Un modello farmacoforico è quindi uno schema 3D costituito da un numero definito di feature farmacoforiche, ciascuna associata a un tipo di interazione, e posizionate secondo distanze e angoli caratteristici. Questo livello di astrazione consente di superare il vincolo della somiglianza chimica diretta, permettendo l’identificazione di [[Molecole|molecole]] diverse che soddisfano gli stessi requisiti di interazione del recettore.

Il processo di drug design basato su farmacofori si articola in tre fasi principali: 
1. ***raccolta dei dati***: consiste nell’acquisizione sistematica di tutte le informazioni disponibili relative al target biologico e ai ligandi noti, includendo composti attivi e, quando disponibili, anche inattivi. 
2. ***analisi delle informazioni***: mira a integrare i dati strutturali e biologici per individuare le caratteristiche comuni responsabili dell’attività, tenendo conto anche delle proprietà stereochimiche del sito di legame.
3. ***progettazione di nuove molecole (design)***: utilizza il farmacoforo risultante come vincolo strutturale per la progettazione di nuovi composti compatibili con i requisiti identificati.


Quando sono disponibili più ligandi, anche chimicamente non correlati, di cui si conoscono i conformanti **bio-attivi** per un dato **target** si assume che condividano uno stesso insieme di elementi [[Farmacofori|farmacoforici]]. Ad esempio
![[IMG - esempio molecole con conformanti biattivi non correlate.png]]
L’identificazione degli elementi comuni avviene tramite la **sovrapposizione tridimensionale** delle molecole, che permette di evidenziare similarità e differenze strutturali rilevanti.
![[IMG - superimposizione delle molecole biattive.png]]
da questa sovrapposizione si puo generare un **modello [[Farmacofori|farmacoforo]]** utilizzabile per cercare ligandi simili.
![[IMG - step per ricerca usando le feature.png]]

Nella maggior parte dei progetti farmacoforici, tuttavia, le **conformazioni bioattive** non sono note. In questi casi, le uniche informazioni disponibili sono le strutture chimiche bidimensionali e i dati di attività biologica. È quindi necessario generare un insieme di conformazioni plausibili per ciascuna molecola mediante la  [[Ricerca conformazionale|ricerca conformazionale]]. Vengono selezionati solo i conformeri a bassa energia, tipicamente entro una finestra energetica definita, ad esempio $\Delta E \leq 13\ \text{kJ/mol}$ rispetto al conformero più stabile.

Se una molecola presenta $n$ conformeri e un’altra $m$, tutte le coppie possibili devono essere considerate nella fase di sovrapposizione sistematica, generando $n \times m$ allineamenti. La valutazione della qualità delle sovrapposizioni consente di identificare quelle che massimizzano la coincidenza delle feature rilevanti. I conformeri coinvolti in tali sovrapposizioni sono considerati candidati come conformazioni bioattive probabili.

![[IMG - Schema  di confronto tra confirmanti.png]]

L’analisi diventa progressivamente più complessa all’aumentare del numero di molecole considerate, poiché il numero di combinazioni cresce rapidamente. Per questo motivo, la selezione delle conformazioni più plausibili può essere supportata da ulteriori criteri, come la coerenza con dati di struttura-attività, al fine di distinguere gli elementi realmente farmacoforici da quelli accessori.

Il flusso di lavoro complessivo del design farmacoforico integra il campionamento conformazionale, la sovrapposizione sistematica, l’identificazione delle feature comuni e la costruzione del modello farmacoforico finale, che può essere successivamente impiegato per il virtual screening.
![[IMG - schema del work flow del task di design.png]]

Si distinguono due grandi categorie di modellazione farmacoforica. Nel farmacoforo ligand-based, il modello è derivato esclusivamente dall’analisi dei ligandi noti, in assenza di informazioni strutturali sul complesso recettore-ligando. Questo approccio richiede un’intensa fase di campionamento conformazionale e di allineamento, poiché la modalità di legame non è direttamente osservabile. Nel farmacoforo structure-based, invece, è disponibile almeno una struttura del complesso recettore-ligando. In questo caso, il farmacoforo viene costruito interpretando direttamente le interazioni tra recettore e ligando e considerando sia le caratteristiche chimiche di complementarità sia la complementarità spaziale del sito di legame.

Quando un complesso recettore-ligando è noto, le feature farmacoforiche derivano dall’osservazione diretta delle interazioni fondamentali e dalle regioni dello spazio che possono essere occupate da gruppi chimici compatibili con il bersaglio. In entrambi gli approcci, il farmacoforo rappresenta uno strumento centrale per il virtual screening, poiché consente di individuare molecole in grado di soddisfare i requisiti minimi di interazione richiesti per l’attività biologica.



