---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# MSA – algoritmi iterativi
---
Gli **algoritmi iterativi** per l’**[[Allineamento di sequenze multiple (MSA)|allineamento di sequenze multiple]]** rappresentano una classe di metodi euristici progettati per **migliorare progressivamente** un MSA iniziale, spesso ottenuto tramite [[MSA - Algoritmi progressivi - CLUSTAL|metodi progressivi]]. A differenza degli approcci puramente progressivi, l’allineamento iniziale non viene considerato definitivo, ma come una soluzione di partenza da **raffinare iterativamente** rispetto a una data [[Problemi di ottimizzazione|funzione obiettivo]].

Il principio fondamentale è quello di **modificare localmente** l’allineamento corrente e accettare solo le modifiche che producono un miglioramento del valore globale della funzione obiettivo, tipicamente una variante della **[[Funzioni obiettivo - sum of pairs (SP)]]**, una misura di accuratezza attesa o un punteggio di consistenza. Questo consente di **annullare decisioni subottimali** introdotte nelle fasi iniziali dell’allineamento progressivo.

Una strategia comune consiste nel **rimuovere temporaneamente** una o più sequenze dall’allineamento e riallinearle rispetto al resto, che viene trattato come un **profilo**. Questo processo può assumere diverse forme:
- una singola sequenza riallineata contro il profilo globale;
- un sottoinsieme di sequenze riallineato rispetto alle rimanenti;
- la suddivisione dell’allineamento in due profili, che vengono riallineati tra loro.

Questi schemi costituiscono i **pattern fondamentali di raffinamento iterativo**. In particolare, una strategia molto diffusa è il **tree-edge refinement**, in cui si costruisce un albero guida a partire dall’MSA corrente, si seleziona un ramo dell’albero e si divide l’allineamento in due profili, che vengono riallineati mediante programmazione dinamica. La modifica viene mantenuta solo se migliora il punteggio globale, e il processo viene ripetuto su più rami e iterazioni.

Un’altra famiglia di metodi iterativi utilizza **informazioni probabilistiche**, in cui le corrispondenze tra posizioni sono valutate in termini di probabilità a posteriori. In questo caso, l’obiettivo non è massimizzare un punteggio di similarità, ma l’**accuratezza attesa** dell’allineamento. Le iterazioni si concentrano spesso sulle regioni a bassa confidenza, che vengono riallineate fino a stabilizzazione.

Ogni iterazione introduce una modifica locale, ma l’effetto cumulativo può produrre un miglioramento significativo della qualità dell’allineamento, in particolare correggendo errori introdotti nelle prime fasi dell’allineamento progressivo. A differenza dei metodi progressivi, le decisioni **non sono irreversibili**, e l’allineamento può evolvere verso configurazioni più coerenti.

Dal punto di vista computazionale, gli algoritmi iterativi sono più costosi rispetto agli approcci progressivi puri, poiché richiedono la valutazione ripetuta della funzione obiettivo e l’esecuzione di riallineamenti multipli. Tuttavia, il costo rimane generalmente gestibile, poiché ogni iterazione opera su una struttura già allineata e non esplora l’intero spazio delle soluzioni.

Un aspetto centrale degli algoritmi iterativi è la definizione di un **criterio di arresto**, che stabilisce quando interrompere il processo di raffinamento. Tale criterio può essere basato:
- sull’assenza di miglioramenti significativi del punteggio;
- sul raggiungimento di un numero massimo di iterazioni;
- sulla stabilizzazione della struttura dell’allineamento.

Nel contesto dell’MSA, gli algoritmi iterativi rappresentano un compromesso tra accuratezza e costo computazionale, collocandosi tra i metodi progressivi, rapidi ma rigidi, e approcci più complessi basati su modelli probabilistici o vincoli globali.
