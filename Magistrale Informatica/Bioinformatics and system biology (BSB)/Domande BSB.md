---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Domande BSB
---

## Galfrè

- Matrici di similarità: perché esistono e come sono calcolate; include anche contesto su sequenze, ricerca globale e locale.
  Risposta: le matrici di similarità servono a dare un punteggio biologicamente sensato agli allineamenti, perché non tutte le sostituzioni fra simboli hanno lo stesso significato. Nel DNA spesso si distingue almeno fra match, mismatch, transizioni e transversioni; nelle proteine si usano matrici derivate da sostituzioni osservate in sequenze omologhe. In questo modo l'allineamento non massimizza solo l'uguaglianza letterale, ma la plausibilità evolutiva. La ricerca globale allinea idealmente tutta la sequenza, mentre quella locale cerca solo la regione più simile.
  Note collegate: [[Confronto tra sequenze | confronto tra sequenze]], [[Allineamento di sequenze | allineamento di sequenze]], [[Allineamento di sequenze pairwise | allineamento pairwise]], [[Allineamento di sequenze pairwise - matrici di sostituzione per sequenze biologiche | matrici di sostituzione]], [[Allineamento di sequenze - Algoritmo Needleman-Wunsch | Needleman-Wunsch]], [[Allineamento di sequenze - Algoritmo Smith-Waterman | Smith-Waterman]].
- Cosa sono le substitution matrix e da dove vengono i numeri.
  Risposta: le substitution matrix sono tabelle di punteggi che assegnano un valore a ogni possibile sostituzione fra nucleotidi o amminoacidi. I numeri derivano da osservazioni sperimentali o da modelli statistici su sequenze omologhe: sostituzioni frequenti o conservative ricevono punteggi più alti, quelle rare o biologicamente sfavorevoli punteggi più bassi o negativi.
  Note collegate: [[Allineamento di sequenze pairwise - matrici di sostituzione per sequenze biologiche | matrici di sostituzione]], [[Aminoacidi | aminoacidi]], [[Proteine | proteine]].
- Cosa ritorna BLAST e cosa si fa dopo.
  Risposta: BLAST ritorna una lista di hit ordinate per significatività, con allineamenti locali, score, bit score, E-value, percentuale di identità, coverage e informazioni sul database matchato. Dopo il risultato si interpreta se gli hit sono plausibilmente omologhi, si filtrano quelli significativi, si controlla la copertura, si può annotare la sequenza, cercare domini o costruire analisi successive come filogenesi o inferenza funzionale.
  Note collegate: [[Allineamento di sequenze - Basic Local Alignment Search Tool (BLAST) | BLAST]], [[Analisi filogenetica | analisi filogenetica]], [[Gene Ontology (GO) | Gene Ontology]].
- Confronti fra stringhe: a cosa serve fare un alignment; differenze fra global e local alignment; differenze fra DNA e protein alignment.
  Risposta: un alignment serve a confrontare sequenze per trovare similarità, omologia, funzione o relazioni evolutive. Il global alignment confronta l'intera lunghezza delle sequenze ed è adatto a sequenze simili e comparabili in estensione; il local alignment cerca solo la sottoregione più simile ed è utile quando le sequenze condividono solo domini o tratti conservati. Nel DNA l'alfabeto è piccolo e il punteggio è più semplice; nelle proteine l'alfabeto è di 20 simboli e si usano matrici di sostituzione perché alcune sostituzioni sono conservative.
  Note collegate: [[Confronto tra sequenze | confronto tra sequenze]], [[Allineamento di sequenze | allineamento di sequenze]], [[Allineamento di sequenze pairwise | allineamento pairwise]], [[Allineamento di sequenze - Algoritmo Needleman-Wunsch | allineamento globale]], [[Allineamento di sequenze - Algoritmo Smith-Waterman | allineamento locale]], [[DNA | DNA]], [[Proteine | proteine]].
- Matrici di sostituzione: BLOSUM; quali cluster di amminoacidi esistono.
  Risposta: le matrici BLOSUM sono costruite da blocchi conservati di allineamenti proteici osservando quanto spesso un amminoacido sostituisce un altro. Il numero, per esempio BLOSUM62, dipende dalla soglia di clustering delle sequenze simili usata per evitare bias. Gli amminoacidi si raggruppano spesso per proprietà chimico-fisiche, come idrofobici, polari non carichi, positivi, negativi, aromatici e speciali; sostituzioni dentro lo stesso gruppo tendono a essere più conservative.
  Note collegate: [[Allineamento di sequenze pairwise - matrici di sostituzione per sequenze biologiche | matrici di sostituzione]], [[Aminoacidi | aminoacidi]], [[Proteine | proteine]].
- BLAST: funzionamento e possibili campi di utilità attuali, ad esempio nella costruzione di un phylogenetic tree.
  Risposta: BLAST usa un approccio euristico basato su parole/semi ad alta similarità, estende i match e produce allineamenti locali molto più velocemente di un algoritmo esatto. Serve per trovare omologhi, annotare geni o proteine, identificare specie o domini conservati e selezionare sequenze da usare in un multiple sequence alignment, che può poi essere la base per costruire un phylogenetic tree.
  Note collegate: [[Allineamento di sequenze - Basic Local Alignment Search Tool (BLAST) | BLAST]], [[Analisi filogenetica | analisi filogenetica]], [[Analisi Filogenetica  - Metodo su distanza UPGMA | UPGMA]], [[Analisi Filogenetica  - Metodo su distanza Neighbour-Joining | Neighbour-Joining]], [[Analisi Filogenetica - Massima verosimiglianza | massima verosimiglianza]].
- Protein motif.
  Risposta: un protein motif è un pattern corto e conservato nella sequenza o nella struttura proteica associato spesso a una funzione, a un sito catalitico o a un sito di legame. Può essere usato per riconoscere famiglie proteiche, inferire funzione e cercare regioni conservate anche quando l'omologia globale è debole.
  Note collegate: [[Motif discoverey | motif discovery]], [[Proteine | proteine]].

## Milazzo

- Cos'è l'inferenza nelle GRN e a cosa serve, con alcuni metodi utilizzati.
  Risposta: l'inferenza nelle Gene Regulatory Networks consiste nel ricostruire le interazioni regolatorie fra geni a partire da dati, tipicamente di espressione. Serve a capire chi regola chi, formulare ipotesi biologiche e costruire modelli predittivi. Metodi comuni includono approcci basati su informazione mutua come ARACNE, metodi tree-based come GENIE3 e approcci che integrano conoscenza a priori sui transcription factor.
  Note collegate: [[Gene Regulatory Networks (GRN) | GRN]], [[GRN - inferenza | inferenza GRN]], [[GRN - inferenza - ARACNE | ARACNE]], [[GRN - inferenza - GENIE3 | GENIE3]], [[GRN - inferenza con transcriptor factor noti | inferenza con TF noti]].
- Nelle Boolean Networks: come funzionano quelle probabilistiche.
  Risposta: nelle Probabilistic Boolean Networks ogni gene resta rappresentato da uno stato discreto, spesso 0 o 1, ma la regola di aggiornamento non è unica o deterministica. Per uno stesso nodo possono esserci più funzioni booleane scelte con una certa probabilità, così il modello descrive meglio incertezza, rumore biologico e variabilità fra condizioni o cellule.
  Note collegate: [[GRN - Boolean Networks | Boolean Networks]], [[GRN - Probabilistic Boolean Networks | Probabilistic Boolean Networks]].
- Cos'è l'algoritmo di Gillespie e come funziona; come si calcola `tau`; pro e contro di ODE vs Gillespie.
  Risposta: l'algoritmo di Gillespie è un metodo di simulazione stocastica per reaction networks che genera esplicitamente il tempo del prossimo evento e quale reazione avviene. Si calcolano le propensity di tutte le reazioni, si sommano in `a0`, poi `tau` si ottiene come variabile casuale esponenziale con parametro `a0`, tipicamente `tau = (1/a0) ln(1/r1)`, e una seconda variabile casuale decide quale reazione scatta. Rispetto alle ODE, Gillespie cattura rumore e discrezze ma è più costoso; le ODE sono più veloci e trattabili analiticamente, ma descrivono solo l'andamento medio continuo.
  Note collegate: [[CRN - Algoritmo di simulazione stocastico di Gillespie | algoritmo di Gillespie]], [[CRN - Modelli stocastici | modelli stocastici]], [[Chemical Reaction Network (CRN) | CRN]], [[Ordinary Differential Equation (ODE) | ODE]].
- Attrattori nelle BN; reti sincrone e asincrone.
  Risposta: nelle Boolean Networks un attrattore è uno stato o un insieme ciclico di stati verso cui la dinamica converge, ed è spesso interpretato come fenotipo stabile o comportamento ricorrente. Nell'aggiornamento sincrono tutti i nodi vengono aggiornati insieme, mentre in quello asincrono i nodi si aggiornano uno alla volta o secondo un ordine non simultaneo; questo può cambiare traiettorie e attrattori osservati.
  Note collegate: [[GRN - Boolean Networks | Boolean Networks]], [[GRN - Probabilistic Boolean Networks | probabilistiche]], [[GRN - Multy-value Networks | multi-value networks]].
- GRN threshold.
  Risposta: una Threshold Boolean Network è una variante delle BN in cui lo stato di un gene dipende dal confronto fra una somma pesata degli input regolatori e una soglia. Se il contributo totale supera la threshold il gene si attiva, altrimenti si spegne. È utile perché introduce una rappresentazione semplice ma più espressiva delle interazioni attivatorie e inibitorie.
  Note collegate: [[GRN - Threshold Boolean Networks | Threshold Boolean Networks]], [[Gene Regulatory Networks (GRN) | GRN]].
- Cinetiche viste a lezione e differenze rispetto a Gillespie: mass-action, Michaelis-Menten, Hill, logistic; Gillespie come approccio stocastico.
  Risposta: mass-action descrive velocità proporzionali al prodotto delle concentrazioni dei reagenti; Michaelis-Menten modella cinetiche enzimatiche saturabili; Hill descrive cooperatività; la logistic viene usata per crescite o reazioni autocatalitiche con saturazione. Queste sono descrizioni deterministiche della velocità media, mentre Gillespie non definisce solo una velocità istantanea media ma simula eventi discreti e casuali di reazione.
  Note collegate: [[CRN - Modello mass-action | mass-action]], [[CRN - Michaelis-menten kinetics | Michaelis-Menten]], [[CRN - Hill kinetics | Hill]], [[CRN - Funzione logistica per reazioni autocatalitiche | logistic]], [[CRN - Modelli stocastici | modelli stocastici]], [[CRN - Algoritmo di simulazione stocastico di Gillespie | Gillespie]].
- Boolean Networks: come funzionano; quali varianti abbiamo visto oltre a quelle classiche. Nota: NO inferenza.
  Risposta: una Boolean Network rappresenta ogni gene con uno stato discreto e aggiorna tale stato tramite una funzione logica che dipende dai regolatori. Le varianti estendono questo schema base: threshold networks introducono pesi e soglie, multi-value networks permettono più di due stati, probabilistic networks introducono incertezza nelle regole, fuzzy networks usano gradi di attivazione invece di soli 0 e 1. Qui l'idea centrale è il modello dinamico, non la ricostruzione della rete dai dati.
  Note collegate: [[GRN - Boolean Networks | Boolean Networks]], [[GRN - Threshold Boolean Networks | Threshold]], [[GRN - Multy-value Networks | multi-value]], [[GRN - Probabilistic Boolean Networks | probabilistiche]], [[GRN - Fuzzy Boolean Networks | fuzzy]].
- Sensitivity analysis: Morris e Sobol.
  Risposta: la sensitivity analysis serve a capire quanto l'output di un modello dipende dai parametri in ingresso. Il metodo di Morris è uno screening globale qualitativo o semi-quantitativo: è più economico e individua parametri influenti e possibili non linearità o interazioni. Sobol è un metodo globale basato sulla decomposizione della varianza: fornisce indici first-order e total-order ed è più informativo, ma anche più costoso computazionalmente.
  Note collegate: [[Sensitivity analisys | sensitivity analysis]], [[Sensitivity analisys - Morris method | Morris]], [[Sensitivity analisys - Sobol Method | Sobol]].
- Attrattori.
  Risposta: gli attrattori sono configurazioni stabili o cicliche della dinamica della rete. In biologia dei sistemi vengono spesso interpretati come stati cellulari stabili, tipi cellulari o programmi di espressione ricorrenti.
  Note collegate: [[GRN - Boolean Networks | Boolean Networks]], [[GRN - Threshold Boolean Networks | Threshold Boolean Networks]].
- Boolean network.
  Risposta: una Boolean Network è un modello discreto di rete regolatoria in cui ogni nodo ha stato binario e viene aggiornato tramite una funzione logica definita dai suoi ingressi. È utile per studiare la dinamica qualitativa del sistema quando i dettagli quantitativi non sono noti.
  Note collegate: [[GRN - Boolean Networks | Boolean Networks]].
- Attractor.
  Risposta: un attractor è l'insieme finale verso cui evolve la rete dopo un certo numero di aggiornamenti; può essere un punto fisso o un ciclo. Dal punto di vista biologico rappresenta un comportamento stabile o ricorrente del sistema.
  Note collegate: [[GRN - Boolean Networks | Boolean Networks]], [[GRN - Threshold Boolean Networks | Threshold Boolean Networks]].
