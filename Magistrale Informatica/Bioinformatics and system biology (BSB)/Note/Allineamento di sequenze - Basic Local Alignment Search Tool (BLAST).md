---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Allineamento di sequenze - Basic Local Alignment Search Tool (BLAST)
---
Il **BLAST** (*Basic Local Alignment Search Tool*) è un metodo **euristico** per il calcolo di **[[Allineamento di sequenze|allineamenti locali]]** tra una sequenza query e un insieme molto ampio di sequenze bersaglio. BLAST rinuncia alla garanzia di ottimalità globale in favore di un forte guadagno in efficienza computazionale, rendendo possibile la ricerca su grandi banche dati.

Dal punto di vista concettuale, BLAST implementa una strategia di **ricerca per semi** (*seed-and-extend*). Il confronto non viene avviato su tutte le possibili coppie di posizioni, ma solo in corrispondenza di brevi sottosequenze ad alto punteggio, riducendo drasticamente lo spazio di ricerca. La procedura si articola in tre fasi principali.

Nella fase di **indicizzazione del pattern**, la sequenza query viene scomposta in parole di lunghezza fissata $w$. A ciascuna parola vengono associate varianti che superano una soglia di punteggio $T$, calcolato tramite una funzione di sostituzione coerente con il [[Allineamento di sequenze pairwise - matrici di sostituzione per sequenze biologiche|contesto biologico]]. Questo passaggio consente di tenere conto di sostituzioni conservative già nella fase iniziale.

La fase di **ricerca dei match** individua nel database le occorrenze esatte delle parole (o delle loro varianti ammissibili). Ogni corrispondenza individua un punto candidato da cui avviare un’estensione. In questa fase il confronto è puramente locale e non introduce gap.

La fase di **estensione** procede a partire dai semi individuati, espandendo l’allineamento in entrambe le direzioni finché il punteggio cumulativo continua a crescere. Nelle versioni moderne di BLAST l’estensione consente l’introduzione di gap, utilizzando modelli di penalità analoghi a quelli degli algoritmi di allineamento locale esatti. Il risultato di questa fase è un insieme di **allineamenti locali ad alto punteggio**.

Il punteggio di ciascun allineamento viene valutato mediante la stessa logica additiva utilizzata negli allineamenti [[Allineamento di sequenze pairwise - matrici di sostituzione per sequenze biologiche|pairwise biologici]], basata su matrici di sostituzione come **BLOSUM62** e penalità di gap. Tuttavia, a differenza degli algoritmi esatti, BLAST non esplora sistematicamente tutte le possibilità, ma solo quelle ritenute promettenti secondo il criterio dei semi.

L’interpretazione dei risultati di BLAST non si basa esclusivamente sul punteggio grezzo, ma su una misura di **significatività statistica**, che stima quanto sia probabile osservare un allineamento di pari o maggiore punteggio per puro caso. Questa misura è formalizzata tramite l’[[E-value]], che dipende dal punteggio dell’allineamento, dalla lunghezza delle sequenze e dalla dimensione del database interrogato.