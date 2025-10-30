---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Planning - Other
---
Nel panorama della [[Planning|pianificazione]] automatica si sono sviluppati numerosi approcci alternativi ai metodi classici. Tra questi, uno dei più rilevanti è **Graphplan**, che utilizza una particolare struttura dati, il *planning [[Grafi|graph]]*, per rappresentare le relazioni tra azioni, precondizioni ed effetti, nonché per specificare le esclusioni mutue. Questa rappresentazione consente di catturare in modo compatto le dipendenze logiche e temporali, riducendo la complessità della ricerca e permettendo una valutazione più efficiente delle possibilità di pianificazione.  

Un altro approccio teoricamente significativo è il **situation calculus**, un formalismo basato sulla logica del primo ordine. Esso impiega assiomi di stato successivo analoghi a quelli di SATPLAN, ma la logica del primo ordine consente una maggiore espressività e compattezza nella formulazione dei problemi. Tuttavia, nonostante la sua eleganza formale, l’applicazione pratica è stata limitata, poiché i dimostratori per la logica del primo ordine non hanno raggiunto l’efficienza dei risolutori proposizionali. Questo approccio ha comunque fornito un contributo fondamentale alla comprensione teorica dei processi di pianificazione.  

Un’evoluzione concettualmente affine è la formulazione del problema di pianificazione come **[[Problemi di soddisfacibilita vincolata (CSP)|problema di soddisfacimento di vincoli (CSP)]]**. In questo caso, un problema di pianificazione limitato a $k$ passi viene tradotto in un insieme di vincoli, con una variabile $Action_t$ per ciascun istante temporale, il cui dominio è l’insieme delle azioni possibili. Ciò consente di evitare la moltiplicazione delle variabili per ogni azione e la necessità di esplicitare assiomi di esclusione, semplificando notevolmente la struttura proposizionale pur mantenendo la coerenza logica.  

Un diverso paradigma è rappresentato dalla **pianificazione a ordine parziale**, nella quale il piano non è concepito come una sequenza lineare di azioni, ma come un grafo che rappresenta le relazioni di precedenza tra azioni. Ogni azione è un nodo e i collegamenti indicano la dipendenza di una precondizione da un’altra azione o dallo stato iniziale. Questo consente di specificare solo le relazioni necessarie tra azioni, lasciando indeterminato l’ordine tra quelle indipendenti. Il processo di ricerca avviene nello spazio dei piani, inserendo progressivamente azioni per soddisfare le condizioni richieste.  

Negli anni Ottanta e Novanta, la pianificazione a ordine parziale si affermò come la strategia più efficace per gestire problemi composti da sottoproblemi indipendenti. Tuttavia, lo sviluppo di euristiche avanzate nei pianificatori basati sulla ricerca in avanti e i progressi tecnologici che hanno reso più efficienti i risolutori proposizionali hanno ridotto la competitività di questo approccio nei contesti di pianificazione classica completamente automatica.  

Nonostante ciò, la pianificazione a ordine parziale mantiene una notevole importanza in applicazioni specifiche. In ambiti come la programmazione operativa o la pianificazione di missioni spaziali, essa risulta preferibile per la sua capacità di generare piani interpretabili da operatori umani. Il processo di raffinamento progressivo dei piani favorisce infatti la comprensione e la verifica delle soluzioni prima della loro esecuzione, garantendo affidabilità e trasparenza nelle operazioni critiche.
