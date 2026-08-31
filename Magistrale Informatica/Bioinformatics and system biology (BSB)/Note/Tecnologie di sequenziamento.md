---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Tecnologie di sequenziamento
---
Una **tecnologia di sequenziamento** è una tecnologia che permette di determinare la sequenza di [[Nucleotidi|nucleotidi]] di una molecola di [[DNA|DNA]] o [[RNA|RNA]]. In generale, l'obiettivo è trasformare molecole biologiche non direttamente leggibili in sequenze digitali che possano essere analizzate computazionalmente.

Le tecnologie di sequenziamento moderne non leggono quasi mai una molecola intera in un unico passaggio: producono molti frammenti di sequenza, chiamati **read**, che devono poi essere controllati, allineati, assemblati o contati a seconda dell'esperimento.

## Libreria di sequenziamento

Prima del sequenziamento il materiale biologico viene preparato in una **libreria di sequenziamento**. Una libreria è l'insieme dei frammenti di DNA o RNA preparati per essere letti dalla macchina.

La preparazione della libreria può includere passaggi come:

- frammentazione delle molecole;
- conversione dell'RNA in cDNA, nel caso di esperimenti su [[RNA|RNA]];
- aggiunta di adattatori necessari alla piattaforma di sequenziamento;
- eventuale aggiunta di [[Unique Molecular Identifier (UMI)|identificatori molecolari univoci (UMI)]] prima dell'amplificazione;
- eventuale amplificazione tramite PCR;
- selezione di frammenti con una certa lunghezza.

Questi passaggi sono importanti perché introducono possibili **bias tecnici**: alcune molecole possono essere rappresentate più o meno di altre non per motivi biologici, ma per effetto della preparazione sperimentale.

## Read e read length

Un **read** è una breve sequenza prodotta dal sequenziatore. Ogni read rappresenta una porzione della molecola originale o di un frammento della libreria.

La **read length** è la lunghezza del read, cioè il numero di basi lette. Read più lunghi possono aiutare in alcuni compiti, come l'assemblaggio o il riconoscimento di regioni ripetute, mentre read più corti possono essere comunque sufficienti per compiti come il conteggio dell'espressione genica in [[Analisi RNA-seq|RNA-seq]].

## Single-end e paired-end

Nel sequenziamento **single-end** viene letto un solo estremo di ciascun frammento.

Nel sequenziamento **paired-end** vengono letti entrambi gli estremi dello stesso frammento. Questo fornisce più informazione sulla posizione e sulla distanza tra i due read, ed è utile per migliorare l'allineamento, riconoscere varianti strutturali o distinguere trascritti simili.

## Profondità, coverage e library size

La **sequencing depth** indica quanta sequenza viene prodotta per un campione. In modo intuitivo, più read vengono generati, più il campione è stato sequenziato in profondità.

La **coverage** o **copertura** indica quante volte, in media, una posizione di una sequenza di riferimento viene letta. Per esempio, una copertura media 30x significa che ogni posizione del genoma è stata osservata circa 30 volte. Il concetto di coverage è particolarmente naturale in esperimenti di DNA-seq o genome sequencing.

Una copertura media non garantisce che ogni posizione sia stata osservata lo stesso numero di volte. Le reads possono concentrarsi in alcune regioni e lasciare altre regioni con copertura bassa o nulla. Le cause comprendono campionamento casuale, profondità insufficiente, bias di frammentazione o amplificazione, composizione GC, sequenze ripetitive e diversa abbondanza delle molecole originali.

Nei dati paired-end, `R1` e `R2` leggono le due estremità dello stesso frammento. Se il frammento è più lungo della somma delle due read length, la regione centrale non viene osservata direttamente da quella coppia:

```text
frammento: ├──────────────────────────────────┤
R1:        ├────────→
R2:                              ←────────────┤
                     regione non letta
```

La copertura complessiva deriva da molti frammenti ottenuti da molecole differenti e spezzati in posizioni diverse. Le loro reads possono sovrapporsi e osservare regioni non lette da una singola coppia. Se nessun frammento campionato copre una posizione, rimane una lacuna e la sua sequenza non può essere determinata direttamente dai dati.

Quando il frammento è più corto della somma delle lunghezze di `R1` e `R2`, le due reads possono sovrapporsi. Questa sovrapposizione può aiutare a riconoscere adattatori, verificare la concordanza tra i mate e correggere alcuni errori di sequenziamento.

La **library size** indica invece il numero totale di read, o di count, associati a un campione dopo il sequenziamento e spesso dopo l'allineamento. In una matrice di conteggi RNA-seq corrisponde circa alla somma dei count di tutti i geni per quel campione.

Questi concetti non indicano direttamente il numero di geni univoci trovati. Un campione può avere molti read concentrati su pochi geni, oppure lo stesso numero totale di read distribuito su molti geni. Il numero di geni osservati dipende anche da quanto sono espressi, dalla profondità di sequenziamento e da soglie tecniche di rilevamento.

Il significato di **sequenziamento completo** dipende quindi dall'obiettivo. Nella ricostruzione de novo servono reads sovrapposte che colleghino tutte le regioni; una lacuna impedisce di ricostruire con certezza le basi mancanti. Nella quantificazione RNA-seq non è necessario osservare ogni base di ogni trascritto: un insieme sufficiente di frammenti compatibili può consentire di stimarne l'abbondanza. Le tecnologie long-read possono leggere molecole o trascritti molto più lunghi e ridurre alcune ambiguità di ricostruzione, ma rimangono soggette a profondità, errori e bias di campionamento.

Per questo, nelle analisi di espressione differenziale, i count grezzi non sono confrontabili direttamente tra campioni con library size diverse: un campione con più read totali tende ad avere count più alti anche senza una reale differenza biologica. Servono quindi metodi di normalizzazione, come quelli usati da DESeq o TMM, per correggere questi effetti tecnici.

## Qualità delle basi

Il sequenziatore assegna a ogni base letta un valore di qualità, spesso espresso come **Phred score**. Questo punteggio stima quanto è probabile che quella base sia stata chiamata in modo errato.

La qualità dei read è importante perché errori di sequenziamento possono influenzare allineamento, chiamata di varianti, assemblaggio e quantificazione. Per questo, una pipeline di analisi include spesso controlli di qualità e, se necessario, rimozione di adattatori o basi di bassa qualità.

## Dopo il sequenziamento

Il risultato grezzo di una tecnologia di sequenziamento non è ancora direttamente una risposta biologica. Di solito i read devono essere elaborati con passaggi computazionali come:

- controllo di qualità;
- trimming di adattatori o basi di bassa qualità;
- allineamento a un genoma o trascrittoma di riferimento;
- assemblaggio, se non si usa un riferimento o se si vogliono ricostruire sequenze;
- conteggio o quantificazione, per esempio dei geni o dei trascritti;
- normalizzazione e analisi statistica.

Il tipo di analisi dipende dall'esperimento: DNA-seq, RNA-seq, ChIP-seq, single-cell sequencing e metagenomica usano tecnologie simili per produrre read, ma rispondono a domande biologiche diverse.

## Bias tecnici comuni

Le tecnologie di sequenziamento possono introdurre o amplificare diversi bias tecnici, tra cui:

- bias legato al contenuto GC;
- bias introdotto dall'amplificazione PCR;
- bias dovuto alla lunghezza dei frammenti;
- duplicati tecnici, che possono essere riconosciuti con maggiore affidabilità quando la libreria contiene [[Unique Molecular Identifier (UMI)|UMI]];
- differenze di library size tra campioni;
- composizione sbilanciata della libreria, quando poche molecole molto abbondanti consumano molti read.

Questi bias non rendono inutili i dati, ma spiegano perché il sequenziamento richiede passaggi di controllo, normalizzazione e modellazione statistica prima dell'interpretazione biologica.
