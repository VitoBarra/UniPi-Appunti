---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# FASTQC - Report di qualità per RNAseq
---
**FASTQC** è un **software** per la valutazione della qualità dei dati di sequenziamento e si colloca nello step iniziale della pipeline di [[analisi RNA-seq]], ovvero nello [[Analisi RNA-seq#Step 1: Quality assessment and sequence trimming|Step 1: Quality assessment]].

FASTQC non esegue trimming né rimozione di adattatori, ma genera report diagnostici sui file [[Formato FASTQ|FASTQ]] per identificare:
- qualità per base (Phred score) lungo la read, codificata nel file [[Formato FASTQ|FASTQ]]
- distribuzione delle quality scores
- contenuto GC
- sequenze sovrarappresentate
- presenza di adattatori
- duplicazione delle reads

L'obiettivo non è modificare i dati, ma capire se i reads grezzi sono compatibili con l'analisi a valle oppure se è necessario intervenire con trimming, filtering o rimozione di adattatori.

FASTQC accetta tipicamente in input uno o più file [[Formato FASTQ|FASTQ]] e produce:
- un report `HTML`, facilmente consultabile
- un archivio `.zip` con metriche dettagliate e file testuali

Le icone `pass`, `warning` e `fail` servono come diagnostica rapida, ma non devono essere interpretate in modo assoluto: in [[Analisi RNA-seq|RNA-seq]] alcuni warning possono riflettere proprietà biologiche o bias tecnici attesi, non necessariamente un dataset inutilizzabile.
![[IMG - FASTQC icone di segnalazione qualita veloce.png]]

##### **Per base sequence quality**
**Per base sequence quality** riassume la distribuzione delle quality scores per posizione lungo la read. In questo modulo vengono riportati:
- [[Statistica Descrittiva - Box-plot|boxplot]] delle quality scores per posizione
- mediana, quartili e range
- una linea continua blu che rappresenta la **media** delle quality scores in ciascuna posizione
- soglie cromatiche tipiche: verde (buona qualità), giallo (attenzione), rosso (bassa qualità)

In questo grafico:
- l'asse $x$ rappresenta la **posizione della base all'interno della read**
- l'asse $y$ rappresenta il **Phred score**

Per ogni posizione, **FASTQC** aggrega le basi che si trovano in quella stessa posizione ma in reads diverse. Queste basi possono anche essere [[Nucleotidi|nucleotidi]] diversi (`A`, `C`, `G`, `T`), ma in questo modulo non interessa quale base sia stata letta: interessa quanto sia **affidabile** la chiamata di quella base in quella posizione della read. In questo modo si può vedere se la qualità tende a degradare verso la fine delle reads, che è un pattern tecnico molto comune.

I baffi del boxplot non rappresentano semplicemente minimo e massimo: in FASTQC vengono letti come percentili estremi della distribuzione, tipicamente intorno al $10°$-percentile per il baffo inferiore e al $90°$-percentile per quello superiore. Per questo una piccola coda della distribuzione può spostare la media senza modificare molto quartili e baffi.
![[IMG - FASTQC report.png]]

##### **Per sequence quality scores**
**Per sequence quality scores** mostra la distribuzione globale della [[Formato FASTQ|qualità]] media delle reads

Nel modulo ***Per sequence quality scores*** non si guarda più la qualità base per base lungo la read, ma la **qualità media complessiva di ciascuna read**. Per ogni read si calcola quindi una media dei **Phred** score delle sue basi, e poi FASTQC costruisce la distribuzione di queste medie su tutte le reads del file.

In questo grafico:
- l'asse $x$ rappresenta la **quality score media della read**
- l'asse $y$ rappresenta il **numero di reads** che hanno quella qualità media

Questo modulo serve quindi a capire se il dataset contiene molte reads globalmente scadenti oppure se quasi tutte le reads hanno una qualità media elevata.

Se la distribuzione è concentrata su quality scores alte, il dataset è globalmente buono. Se invece compare una quota importante di reads con qualità media bassa, questo può indicare un dataset rumoroso o la necessità di filtrare e rifinire i dati prima delle analisi a valle.
![[IMG - FASTQC - per sequence quality scores.png]]
##### **Per base sequence content**
**Per base sequence content** mostra la composizione percentuale di `A`, `T`, `C` e `G` lungo la read.

Nel modulo ***Per base sequence content*** FASTQC mostra, per ogni posizione della read, quale percentuale di basi osservate è `A`, `T`, `C` oppure `G`. A differenza dei moduli precedenti, qui non si guarda la qualità della chiamata ma il **contenuto nucleotidico** lungo la read.

In questo grafico:
- l'asse $x$ rappresenta la **posizione della base all'interno della read**
- l'asse $y$ rappresenta la **percentuale** di `A`, `T`, `C` e `G` osservata in quella posizione

Per ogni posizione, FASTQC aggrega tutte le reads e calcola quante basi sono `A`, quante `T`, quante `C` e quante `G`. Il risultato è quindi una curva per ciascun nucleotide che mostra come cambia la composizione lungo la read.

Questo modulo serve a capire se la composizione delle basi è relativamente stabile oppure se ci sono sbilanciamenti forti in certe regioni della read. In un dataset ideale ci si aspetta in genere curve abbastanza regolari; deviazioni marcate, soprattutto all'inizio o alla fine delle reads, possono riflettere bias tecnici di sequenziamento, preparazione della libreria o trimming incompleto.
![[IMG - FASTQC per base sequence content.png]]
##### **Per sequence GC content**
**Per sequence GC content** mostra la distribuzione del contenuto GC tra le reads.

Nel modulo ***Per sequence GC content*** FASTQC guarda il **contenuto GC complessivo di ciascuna read**. Per ogni read si calcola quindi quale percentuale delle sue basi è costituita da `G` e `C`, e poi si costruisce la distribuzione di questi valori su tutte le reads del file.

In questo grafico:
- l'asse $x$ rappresenta il **contenuto GC della read**, espresso in percentuale
- l'asse $y$ rappresenta il **numero di reads** che hanno quel contenuto GC

Questo modulo serve a capire se il dataset ha una distribuzione del contenuto GC compatibile con quella attesa per il campione analizzato. In molti casi ci si aspetta una distribuzione abbastanza regolare e con un picco principale ben definito.

Se la distribuzione osservata è molto spostata, molto larga o presenta più picchi, questo può suggerire contaminazione, presenza di popolazioni di sequenze diverse oppure bias introdotti durante preparazione della libreria o sequenziamento.
![[IMG - Per Sequence GC content.png]]
##### **Per base N content**
**Per base N content** mostra, per ogni posizione della read, la percentuale di basi chiamate come `N`.

Nel modulo ***Per base N content*** FASTQC misura quante volte il sequenziatore non è riuscito ad assegnare con affidabilità un nucleotide specifico e ha quindi riportato un carattere `N` che rappresenta una qualsiasi base fosse `A`, `T`, `C` o `G` 

In questo grafico:
- l'asse $x$ rappresenta la **posizione della base all'interno della read**
- l'asse $y$ rappresenta la **percentuale di basi chiamate `N`** in quella posizione

Una presenza elevata di `N`, soprattutto concentrata in certe regioni della read, può indicare posizioni problematiche o qualità molto bassa.
![[IMG - FASTQC - per base N content.png]]

##### **Sequence Length Distribution**
**Sequence Length Distribution** mostra la distribuzione delle lunghezze delle reads nel dataset.

Nel modulo ***Sequence Length Distribution*** FASTQC conta quante reads hanno una certa lunghezza e costruisce la distribuzione complessiva.

In questo grafico:
- l'asse $x$ rappresenta la **lunghezza della read**
- l'asse $y$ rappresenta il **numero di reads** con quella lunghezza

Se tutte le reads hanno la stessa lunghezza, il grafico mostra in genere un picco molto netto. Se invece il dataset contiene reads di lunghezza variabile, ad esempio dopo trimming, la distribuzione può essere più larga.
![[IMG - FASTQC - Sequence Length Distribution.png]]

##### **Sequence duplication levels**
**Sequence duplication levels** mostra quanto frequentemente le stesse sequenze compaiono più volte nel dataset.

Nel modulo ***Sequence duplication levels*** FASTQC raggruppa le reads in base al numero di volte in cui compaiono e costruisce una distribuzione dei livelli di duplicazione. Questo permette di capire se il dataset contiene molte reads uniche oppure una quota elevata di reads ripetute.

In questo grafico:
- l'asse $x$ rappresenta il **livello di duplicazione** della read, cioè quante volte la stessa sequenza compare nel dataset
- l'asse $y$ rappresenta la **percentuale di reads** che appartiene a quel livello di duplicazione

Nel grafico FASTQC compaiono tipicamente due curve:
- una curva relativa a **tutte le sequenze osservate**, che descrive la duplicazione reale del dataset
- una curva **deduplicated** o teoricamente normalizzata, che mostra come apparirebbe la distribuzione se ogni sequenza fosse contata una sola volta

Il confronto tra queste curve serve a capire quanto il dataset sia ridondante. Se la curva reale è molto concentrata verso bassi livelli di duplicazione, il dataset contiene soprattutto reads uniche. Se invece resta alta anche per livelli di duplicazione elevati, significa che molte sequenze compaiono molte volte.

Nel contesto RNA-seq questo modulo va interpretato con cautela: una certa duplicazione può essere normale, perché trascritti molto espressi generano molte reads identiche o molto simili. Tuttavia una duplicazione molto forte e diffusa può anche suggerire bassa complessità della libreria, artefatti di PCR o over-sequencing di poche molecole.

In pratica:
- una distribuzione dominata da reads uniche suggerisce una libreria più complessa
- una lunga coda verso livelli di duplicazione alti indica maggiore ridondanza
- una grande distanza tra curva osservata e curva deduplicated indica che il dataset è fortemente dominato da sequenze ripetute
![[IMG - FASTQC - sequence duplication levels.png]]

##### **Overrepresented sequences**
**Overrepresented sequences** elenca le sequenze che compaiono con frequenza molto più alta del previsto nel dataset.

Nel modulo ***Overrepresented sequences*** FASTQC identifica reads o frammenti di reads particolarmente abbondanti e prova, quando possibile, ad associarli a sorgenti note come adattatori, contaminanti o sequenze tecniche.

Questo modulo è utile perché la presenza di sequenze sovrarappresentate può indicare:
- adattatori non rimossi
- contaminazione tecnica o biologica
- amplificazione preferenziale di alcune sequenze
- reads dominate da poche sequenze molto abbondanti

L'interpretazione dipende dal tipo di sequenza riportata: alcune overrepresented sequences sono chiaramente artefatti tecnici, altre possono riflettere proprietà reali del campione.
![[IMG - FASTQC - overrepresented sequences.png]]

##### **Adapter content**
**Adapter content** mostra la presenza residua di adattatori lungo la read.

Nel modulo ***Adapter content*** FASTQC confronta le sequenze osservate con adattatori noti e stima, per ogni posizione della read, quale frazione di reads contiene ancora tracce di adattatore.

In questo grafico:
- l'asse $x$ rappresenta la **posizione della base all'interno della read**
- l'asse $y$ rappresenta la **percentuale di reads** in cui viene rilevato adattatore in quella posizione

Questo modulo è particolarmente utile per capire se il trimming degli adattatori è necessario oppure se è stato efficace. Un aumento del segnale verso la fine della read è un pattern tipico di adattatori residui non rimossi completamente.
![[IMG - FASTQC - adapter content.png]]

## Come interpretare il report
L’analisi comparativa *Before trimming* vs *After trimming* consente di verificare:
- rimozione delle code a bassa qualità
- eliminazione di adattatori
- miglioramento della distribuzione delle Phred scores nelle regioni terminali

In pratica, alcuni pattern tipici suggeriscono azioni specifiche:
- calo della qualità nelle basi terminali: possibile quality trimming sulle code
- presenza di `adapter content`: trimming degli adattatori con software dedicati
- forte overrepresentation di sequenze note: verifica di contaminazioni o sequenze tecniche residue
- distribuzione GC molto anomala: possibile contaminazione, bias di libreria o campione peculiare
- duplicazione elevata: possibile bassa complessità di libreria, artefatti PCR o trascritti altamente espressi

FASTQC è quindi uno strumento di controllo qualità preliminare e post-trimming, utile per:
- decidere parametri di trimming (es. lunghezza minima, soglia Phred)
- verificare l’efficacia di software di trimming come [[Cutadapt - Software di trimming per RNAseq|Cutadapt]], [[Trimmomatic - Software di trimming per RNAseq|Trimmomatic]] o [[fastp - Software di trimming per RNAseq|fastp]]

## FASTQC e MultiQC
Quando si hanno molti campioni, leggere separatamente decine di report FASTQC diventa poco pratico. In questo contesto si usa spesso **[[MultiQC - Report aggregato per RNAseq|MultiQC]]**, un tool che aggrega in un unico report i risultati prodotti da **FASTQC** e da molti altri software bioinformatici.

Nel contesto RNA-seq, MultiQC è utile perché:
- riassume i risultati di FASTQC di tutti i campioni in una singola dashboard
- permette confronti rapidi tra campioni diversi
- evidenzia outlier, batch sospetti o campioni con qualità anomala
- semplifica il confronto *before trimming* vs *after trimming* su tutto il dataset

FASTQC e MultiQC quindi non sono strumenti alternativi:
- **FASTQC** produce il report diagnostico per singolo campione
- **MultiQC** integra molti report FASTQC e li presenta in forma comparativa
