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
La **dinamica molecolare** rappresenta un’estensione della [[Meccanica molecolare|meccanica molecolare]] e costituisce un approccio computazionale per individuare **conformeri** preferenziali e [[Energia Molecolare||minimi energetici]] globali attraverso la simulazione del moto **atomico nel tempo**, considerando vibrazioni e rotazioni interne. ![[IMG - tipi di movimenti dei legami.png]]
Gli atomi vengono trattati come particelle che rispondono alle [[equazioni di Newton|equazioni di Newton]], dove la forza determina l’accelerazione secondo $F=ma$. L’integrazione numerica delle equazioni del moto, lungo passi temporali successivi, produce traiettorie che riportano **posizioni e velocità**. ![[IMG - simulazione.png]]
La distribuzione dell’energia tra componente potenziale e cinetica consente al sistema di superare barriere energetiche quando l’energia cinetica è comparabile con l’altezza della barriera. ![[IMG - barriera energetica.png]]
Con energia sufficiente, correlata alla temperatura di simulazione, l’esplorazione della superficie di energia potenziale diventa più ampia, pur restando limitata dai tempi computazionali. l’energia cinetica media segue $$E_K = \frac{1}{2} m \langle v^2 \rangle = \frac{f}{2} k_B T$$L’energia potenziale dipende dalle coordinate di tutti gli atomi e, per la complessità della funzione, non esiste una soluzione analitica; l’integrazione viene quindi effettuata con algoritmi numerici come Verlet, Velocity Verlet, LeapFrog e Beeman, suddividendo il moto in intervalli $\Delta t$. La scelta di $\Delta t$ richiede che le variazioni di $V$ restino trascurabili entro il passo; il vincolo principale è imposto dagli atomici più rapidi, portando tipicamente a $\Delta t \approx 10^{-15}$ s. Ne deriva che simulazioni estese richiedono un numero molto elevato di passi, con tempi effettivi nell’ordine di decine o centinaia di nanosecondi e capacità di attraversare solo barriere relativamente basse.

Durante la simulazione è possibile estrarre configurazioni a intervalli regolari e sottoporle a minimizzazione per ottenere diversi minimi locali. 
Per descrivere sistemi biologici realistici è necessario includere il **solvente e gli ioni**, scegliendo tra 
- **trattamenti impliciti**, basati su costanti dielettriche e modelli continuo (Generalized Born, Poisson–Boltzmann)
- **trattamenti espliciti**: in cui il solvente interagisce direttamente con il soluto, con maggiore affidabilità ma costo computazionale superiore.
 Per riprodurre un fluido in condizioni di massa, si impiegano condizioni periodiche al bordo della simulazione,, mantenendo cosi costante il numero di particelle.
![[IMG - Loop boundaries 3D.png]] 

una simulazione di **dinamica molecolare** segue i seguenti step ![[IMG - step di una simulazione di dinamica molecolare.png]]
La dinamica atomica mostra un’evoluzione complessa: inizialmente le collisioni frequenti rendono i moti apparentemente irregolari, mentre su scale temporali più lunghe emergono fluttuazioni collettive che rivelano differenze di mobilità tra regioni strutturali. Parametri di controllo come minimizzazione, restart, gestione delle velocità, condizioni periodiche, cutoff non legati, vincoli (SHAKE), valutazione delle forze, temperatura di riferimento $T$, algoritmi di termostato e frequenze di collisione $\gamma$, numero di passi $N$, passo temporale $dt$, e intervalli di scrittura per energie, coordinate e file di restart consentono di modulare l’accuratezza del campionamento e la stabilità numerica.

L’analisi delle traiettorie comprende la valutazione della deviazione quadratica media (RMSD) degli atomi pesanti di proteina e ligando rispetto alle coordinate iniziali, utile per descrivere l’andamento strutturale globale. ![[IMG - analosi di traiettoria, grafico d errorre.png]] Viene inoltre considerata la fluttuazione quadratica media (RMSF) dei $C_\alpha$, indicativa dello spostamento medio residuo nel corso della simulazione. ![[IMG - analisi di traiettoria errore.png]]





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
