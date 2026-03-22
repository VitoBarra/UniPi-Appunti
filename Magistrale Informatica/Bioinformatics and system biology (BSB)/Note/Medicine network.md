---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Medicine network
---
La **Medicine network** è l'applicazione delle [[Protein-Protein interaction network (PPIN)|protein-protein interaction networks]] allo studio congiunto di malattie, target terapeutici e farmaci. L'idea centrale è che una patologia corrisponda a una regione funzionale dell'interactoma e che l'effetto di un farmaco possa essere valutato osservando la posizione topologica dei suoi target rispetto a tale regione.

In questo contesto si introducono due nozioni fondamentali:
- **disease [[Network Science - Community|module]]**: insieme delle proteine associate a una malattia nell'interactoma;
- **drug [[Network Science - Community|module]]**: insieme delle proteine bersaglio di un farmaco.
Il confronto tra questi moduli permette di stimare la relazione topologica tra stato patologico e intervento terapeutico.

La costruzione di un'analisi di medicine network richiede in genere l'integrazione di più banche dati:
- database di malattia per identificare i geni o le proteine associate alla patologia;
- database di farmaci per identificare i target proteici;
- database PPI per ricostruire la rete di interazioni tra i nodi di interesse.
Il workflow consiste nel raccogliere disease genes e drug targets, proiettarli nella stessa PPI network, filtrare le interazioni più affidabili e distinguere i nodi tra elementi del modulo di malattia, elementi del modulo di farmaco e nodi di collegamento.

La misura più immediata è la **network proximity** tra due moduli $A$ e $B$, definita come distanza media dei cammini minimi tra tutte le coppie di nodi dei due insiemi: $$d(A,B)=\frac{1}{|A||B|}\sum_{a\in A}\sum_{b\in B}d(a,b)$$ dove $d(a,b)$ è la lunghezza del cammino minimo tra $a$ e $b$. Valori piccoli indicano vicinanza topologica, mentre valori elevati indicano separazione tra il modulo patologico e quello farmacologico.

Accanto alla proximity si usa la **separation**, che confronta la distanza inter-modulo con la coesione interna dei moduli stessi. Questa misura consente di distinguere meglio tra sovrapposizione, adiacenza topologica e separazione effettiva nell'interactoma.

L'analisi può essere svolta con strumenti visuali o programmabili:
- software di visualizzazione per importare il network, annotare i nodi ed esplorare componenti, cluster e shortest paths;
- librerie per grafi per calcolare centralità, cammini minimi, proximity e separation.
Le stesse reti possono essere usate anche per identificare hub, nodi ponte e proteine che connettono il disease module ai target farmacologici.

La medicine network è utile per prioritizzare candidati terapeutici, valutare il riposizionamento di farmaci e interpretare relazioni sistemiche tra geni di malattia e bersagli molecolari. La sua affidabilità dipende però dalla qualità della PPI network di partenza, dalla correttezza delle annotazioni su malattia e farmaco e dalla scelta di interazioni sufficientemente specifiche e ad alta confidenza.

![[IMG - Medicine network - module and disease module.png]]


![[IMG - Medicine network - predizione di associzione gene-malattia.png]]