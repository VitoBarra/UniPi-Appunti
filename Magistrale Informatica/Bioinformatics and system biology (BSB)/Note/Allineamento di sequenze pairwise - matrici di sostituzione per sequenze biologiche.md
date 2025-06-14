---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Allineamento di sequenze pairwise - matrici di sostituzione per sequenze biologiche
---
L’**allineamento di sequenze pairwise per sequenze biologiche** rappresenta una specializzazione dell’[[Allineamento di sequenze pairwise]] in cui la **funzione obiettivo** viene adattata alle proprietà [[Chimica|chimiche]], strutturali ed evolutive delle sequenze biologiche. In questo contesto, l’allineamento non è soltanto un confronto simbolico, ma un modello computazionale che incorpora ipotesi sul processo evolutivo che ha generato le sequenze.

A differenza del caso astratto, nelle sequenze biologiche i simboli non sono equivalenti. In particolare, la sostituzione di un simbolo con un altro non ha un effetto uniforme: alcune sostituzioni sono più plausibili di altre in funzione delle proprietà chimico-fisiche e del contesto evolutivo. Per questo motivo, nel pairwise alignment biologico non si utilizzano funzioni obiettivo uniformi, ma **schemi di punteggio specializzati**.

Un elemento centrale è la valutazione delle **sostituzioni** nelle sequenze proteiche. La sostituzione di un [[Aminoacidi|amminoacido]] con un altro viene modellata tramite **matrici di sostituzione**, che assegnano un punteggio specifico a ciascuna coppia di residui. Tali matrici non definiscono una distanza metrica nel senso matematico, ma una misura di similarità basata su frequenze osservate in allineamenti considerati biologicamente affidabili.

Tra le matrici di sostituzione più utilizzate rientra la famiglia **BLOSUM** (*BLOcks SUbstitution Matrix*), costruita a partire da regioni altamente conservate di allineamenti di proteine evolutivamente correlate. Il punteggio associato a una coppia di [[Aminoacidi|amminoacidi]] $a,b$ riflette il rapporto logaritmico tra la [[Definizione di Probabilita|probabilità]] osservata $P(a,b)$ di trovarli allineati e la probabilità attesa assumendo [[Indipendenza Stocastica|indipendenza delle frequenze]]:
$$
s(a,b)=\operatorname{round}\left(2\log_2\frac{P(a,b)}{P(a)P(b)}\right)
$$
In questo modo, sostituzioni osservate più frequentemente del caso ricevono punteggi positivi, mentre sostituzioni rare sono penalizzate. 
Un esempio è il seguente. Si consideri un insieme di $1000$ coppie di amminoacidi allineate, in cui la coppia **Serina–Leucina (S,L)** compare $9$ volte. Supponendo una frequenza marginale della Serina pari a $15\%$ e della Leucina pari a $10\%$, il punteggio di sostituzione è calcolato come:$$s(S,L)=\operatorname{round}\!\left(2\log_2\frac{9/1000}{0.15\cdot0.10}\right)$$Il valore ottenuto riflette il confronto tra la frequenza osservata della sostituzione e quella attesa sotto l’ipotesi di indipendenza delle frequenze dei singoli residui.


La matrice **BLOSUM62** è costruita utilizzando allineamenti di sequenze con un livello di similarità superiore al $62\%$ ed è una delle versioni più utilizzate nella pratica. Essa rappresenta un compromesso tra sensibilità e specificità, risultando adatta al confronto di sequenze con una distanza evolutiva intermedia. La matrice riflette implicitamente la classificazione degli amminoacidi in gruppi con proprietà simili, come residui idrofobici, polari non carichi, polari positivi e polari negativi.
![[IMG - Allineamento di sequenze pairwise per sequenze biologiche BLOSUM62 matrice di sostituzione.png]]
Un’altra famiglia di matrici di sostituzione è rappresentata dalle **PAM** (*Point Accepted Mutations*). Le matrici PAM sono derivate dallo studio di famiglie di proteine strettamente correlate, per le quali la distanza evolutiva è nota. A differenza delle BLOSUM, le PAM sono costruite come **modelli evolutivi espliciti**, in cui il numero associato alla matrice indica la distanza evolutiva: valori più bassi corrispondono a sequenze più simili, mentre valori più alti modellano sequenze più divergenti.

Nel pairwise alignment biologico, la funzione obiettivo combina quindi:
- il **punteggio di sostituzione**, determinato dalla matrice scelta (ad esempio BLOSUM62 o PAM);
- la **penalità dei gap**, che modella eventi di inserzione e cancellazione.

Per quanto riguarda i **gap**, nei sistemi biologici le inserzioni e cancellazioni tendono a coinvolgere segmenti contigui piuttosto che posizioni isolate. Per questo motivo, si utilizzano penalità non uniformi. Il modello più comune è la **penalità affine**, in cui l’apertura di un gap è penalizzata più severamente rispetto alla sua estensione. Valori tipici delle penalità dipendono dal tipo di sequenza considerata e riflettono ipotesi biologiche sulla frequenza di tali eventi.

Nel contesto biologico, il risultato di un pairwise sequence alignment può essere interpretato come una stima della **relazione evolutiva** o della **similarità funzionale** tra due sequenze. Allineamenti diversi possono emergere come ottimali in base alla matrice di sostituzione e al modello di penalità dei gap adottati, rendendo la funzione obiettivo parte integrante dell’interpretazione biologica del risultato.
