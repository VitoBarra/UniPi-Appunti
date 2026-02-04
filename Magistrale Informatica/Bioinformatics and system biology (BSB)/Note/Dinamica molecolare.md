---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Dinamica molecolare
---
La **dinamica molecolare** è un ambito della [[chimica computazionale|chimica computazionale]] che rappresenta un’estensione della [[Meccanica molecolare|meccanica molecolare]] e costituisce un approccio per individuare conformazioni preferenziali e generare diversi [[Energia Molecolare e conformazioni|minimi energetici locali]] attraverso la simulazione del moto **atomico nel tempo**, considerando vibrazioni, rotazioni interne e traslazioni.  
![[IMG - tipi di movimenti dei legami.png]]
La dinamica molecolare tratta ogni atomo come una particella soggetta alle [[equazioni di Newton|equazioni di Newton]], in cui la forza determina l’accelerazione secondo $F=ma$. L’[[Integrali notevoli|integrazione]] numerica delle equazioni del moto, lungo passi temporali successivi, produce una traiettoria che descrive l’evoluzione di **posizioni e velocità** del sistema.  

(Update)
![[IMG - simulazione.png]]

Durante la simulazione, l’energia totale è distribuita tra componente potenziale e cinetica. Questo permette al sistema di superare barriere energetiche che separano minimi locali, purché l’energia cinetica sia comparabile con l’altezza della barriera.  
![[IMG - barriera energetica.png]]
L’energia cinetica media $E_K$ è legata alla temperatura di simulazione secondo $$E_K=\frac{1}{2}m\langle v^2\rangle=\frac{f}{2}k_BT$$ dove:
- $m$ è la massa dell’atomo (o particella considerata)  
- $\langle v^2\rangle$ è il valore medio del quadrato della velocità, calcolato lungo la traiettoria  
- $f$ è il numero di gradi di libertà del sistema (tipicamente $f=3N$ per $N$ atomi, al netto di eventuali vincoli)  
- $k_B$ è la costante di Boltzmann  
- $T$ è la temperatura assoluta della simulazione  
Questa relazione esprime il principio di equipartizione, secondo cui a ogni grado di libertà traslazionale o vibrazionale è associato in media un contributo energetico proporzionale alla temperatura.

Poiché l’energia potenziale dipende dalle coordinate di tutti gli atomi, le equazioni del moto non ammettono soluzione analitica e devono essere risolte numericamente tramite algoritmi come Verlet, Velocity Verlet, LeapFrog e Beeman, suddividendo il moto in intervalli $\Delta t$. La scelta di $\Delta t$ è vincolata dai moti atomici più rapidi: tipicamente $\Delta t\approx10^{-15}$ s (1 fs). Ne deriva che anche simulazioni di poche centinaia di nanosecondi richiedono milioni o miliardi di passi.

Di conseguenza, con temperature realistiche e tempi accessibili (decine–centinaia di ns), la dinamica molecolare campiona principalmente la regione locale attorno alla conformazione iniziale e consente di superare solo barriere relativamente basse (pochi kcal/mol). Minimi locali diversi possono essere generati selezionando configurazioni a intervalli regolari e sottoponendole successivamente a minimizzazione.

Per descrivere sistemi biologici realistici è necessario includere anche **solvente e ioni**, scegliendo tra:
- **trattamenti impliciti**, basati su modelli continui (Generalized Born, Poisson–Boltzmann)  
- **trattamenti espliciti**, in cui acqua e ioni interagiscono direttamente con il soluto, con maggiore affidabilità ma costo computazionale superiore  

Per simulare un fluido bulk ed evitare effetti di bordo si impiegano condizioni periodiche al contorno (*periodic boundary conditions*): il sistema viene racchiuso in una scatola replicata nello spazio, e le particelle che escono da un lato rientrano dal lato opposto come immagini periodiche.  
![[IMG - Loop boundaries 3D.png]]

Una simulazione di **dinamica molecolare** (*molecular dynamics, MD*) segue tipicamente una sequenza ordinata di fasi, finalizzate a ottenere una descrizione realistica dell’evoluzione temporale del sistema e a produrre traiettorie utili per analisi strutturali e dinamiche.  
![[IMG - step di una simulazione di dinamica molecolare.png]]

Come illustrato nello schema dei *Steps of a MD simulation*, il protocollo standard comprende:
- **minimizzazione iniziale** (*system minimization*), necessaria per eliminare contatti sterici e rilassare la struttura di partenza  
- **riscaldamento** (*heating dynamics*), in cui il sistema viene portato gradualmente alla temperatura desiderata  
- **equilibratura** (*equilibration dynamics*), fase in cui le proprietà termodinamiche si stabilizzano e il sistema raggiunge condizioni di equilibrio  
- **dinamica di produzione** (*production dynamics*), durante la quale vengono generate le traiettorie che descrivono il moto atomico nel tempo  
- **analisi finale delle traiettorie** (*trajectory analysis*), utile per calcolare grandezze come RMSD, RMSF, legami idrogeno e altre proprietà strutturali  
Questa progressione consente di ottenere simulazioni affidabili e di interpretare i movimenti molecolari su scale temporali accessibili alla MD.  

al inizio della simulazione i moti appaiono irregolari per effetto delle collisioni, mentre su tempi più lunghi emergono fluttuazioni collettive che distinguono regioni più mobili e regioni più stabili della struttura.  L’analisi delle traiettorie comprende la valutazione della deviazione quadratica media (RMSD) degli atomi pesanti di proteina e ligando rispetto alla struttura iniziale, utile per descrivere l’andamento globale della stabilità conformazionale.  
![[IMG - analosi di traiettoria, grafico d errorre.png]]
Viene inoltre considerata la fluttuazione quadratica media (RMSF) dei $C_\alpha$, indicativa dello spostamento medio di ciascun residuo durante la simulazione.  
![[IMG - analisi di traiettoria errore.png]]




# Simulazione di una proteina mutata 
La proteina hRPE65 svolge un ruolo centrale nel ciclo visivo e diverse mutazioni a carico della sua sequenza aminoacidica sono associate a forme ereditarie di degenerazione retinica. L’analisi tramite dinamica molecolare permette di valutare come le mutazioni influenzino il ripiegamento della proteina e la stabilità conformazionale nel tempo, con particolare attenzione agli effetti locali e alle possibili perturbazioni strutturali di lungo raggio.  

![[IMG - proteina mutata.png]]

La riduzione delle dimensioni del sistema rappresenta una strategia per accelerare i calcoli, poiché il costo computazionale cresce approssimativamente in modo lineare con il numero di atomi. L’uso di position restraints consente di ancorare le porzioni terminali della sequenza quando la proteina viene “tagliata”, mantenendo la stabilità complessiva del modello. Sistemi più piccoli permettono di estendere le simulazioni e aumentare la probabilità di osservare movimenti conformazionali che emergono su scale temporali più lunghe, con ulteriori accorgimenti pensati per incrementare ulteriormente la velocità del campionamento.  

![[IMG - analisi di stabilita proteina modificata.png]]
![[IMG - analisi di stabilita con 2 mutazioni diverse.png]]
![[IMG - analisi di stabilita di due mutazioni 2.png]]
![[IMG - analisi di stabilita di proteina con due mutazioni diverse posizione.png]]
![[IMG - analisi di stabilita interazioni.png]]

La tecnica del simulated annealing prevede un riscaldamento iniziale del sistema a temperature elevate, tipicamente comprese tra 2000 e 3000 K. Successivamente, durante l’esecuzione della dinamica, la temperatura viene ridotta progressivamente. Nelle fasi iniziali la molecola esplora un ampio spazio conformazionale, mentre nella fase finale tende a restare intrappolata in un minimo energetico. La ripetizione del processo consente di ottenere più conformazioni a bassa energia, con un’analogia concettuale con i processi di tempra dei materiali. In termini schematici, il paesaggio energetico può essere descritto come una funzione $E(x)$ che presenta minimi locali e globali, con la riduzione controllata della temperatura che favorisce la discesa verso regioni a energia più bassa.  

![[IMG - simulated anealing.png]]

La dinamica molecolare classica rimane spesso limitata a tempi dell’ordine delle centinaia di nanosecondi e a sistemi contenenti alcune centinaia di migliaia di atomi. L’approccio coarse-grained consente di superare tali limiti rappresentando insiemi di atomi mediante bead, riducendo il numero di gradi di libertà e semplificando le interazioni. La diminuzione dei dettagli atomistici rende possibile estendere sia le scale temporali sia quelle spaziali, con un guadagno di ordini di grandezza rispetto alla descrizione completamente atomica. In forma schematica, si passa da un numero di coordinate $3N$ a un numero ridotto $3M$ con $M < N$, migliorando il rapporto tra accuratezza e costo computazionale. Le simulazioni coarse-grained risultano quindi particolarmente utili nello studio del folding proteico.  

![[IMG - corse grained Molecular dinamics.png]]
![[IMG - step totali di simulazione con dinamica molecolarecourse grained.png]]

Lo studio dei processi di associazione e dissociazione tra macromolecole richiede strumenti in grado di descrivere transizioni tra stati di equilibrio separati da barriere energetiche elevate e caratterizzati da eventi rari. L’applicazione di forze esterne controllate permette di superare tali barriere e di analizzare il percorso di dissociazione o riconoscimento molecolare in modo diretto, in analogia con tecniche sperimentali come la microscopia a forza atomica o le pinzette ottiche. Nella prospettiva della dinamica forzata, la variabile reazione può essere descritta come una coordinata $s$ lungo la quale viene applicata una forza $F(s)$ che guida il sistema attraverso il paesaggio energetico. Questo approccio è impiegato nello studio di complessi proteina–proteina, nel rilascio di ligandi e nella deformazione controllata di biopolimeri.  

![[IMG - Steered dinamica molecolare.png]]
