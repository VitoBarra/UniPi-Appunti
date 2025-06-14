---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---
# Motif discoverey
---
La **Motif discoverey** è un insieme di tecniche dell’[[analisi di sequenze|analisi di sequenze]] che mira a identificare pattern ricorrenti all’interno di sequenze biologiche, come [[DNA Struttura e funzionalità|DNA]], [[RNA|RNA]] o [[proteine|proteine]], che risultano conservati perché associati a funzioni specifiche. Un motif rappresenta quindi una firma caratteristica, spesso breve, che compare in più sequenze e che può indicare siti di legame, regioni regolative o elementi strutturali importanti.

L’obiettivo della **motif discovery** è individuare tali configurazioni senza conoscerne a priori la posizione esatta, attraverso l’analisi statistica delle frequenze e delle ricorrenze. I motifs possono essere rappresentati in forme diverse, che vanno da pattern rigidi e altamente conservati fino a modelli più flessibili capaci di descrivere una variabilità funzionalmente compatibile. Questa differenza riflette il fatto che alcuni motifs sono definiti in modo netto, mentre altri possono tollerare sostituzioni e variazioni mantenendo comunque la funzionalità. Quindi si hanno due classi quali:
- i **motifs deterministici**, in cui un pattern è definito in modo preciso e risulta presente oppure assente nella sequenza, come avviene per molti motifs proteici annotati in banche dati come Prosite  
- i **motifs probabilistici**, in cui il motif è descritto attraverso una distribuzione di possibilità, incorporando maggiore variabilità e modellando la presenza dei simboli in termini di probabilità  

Un motif può quindi essere descritto come una sequenza consenso, oppure come una matrice di probabilità posizione-specifica, in cui per ogni posizione viene stimata la distribuzione dei simboli:

$$P=\{p_{i}(a)\}$$

dove $p_{i}(a)$ indica la probabilità di osservare il simbolo $a$ alla posizione $i$. Questa formulazione consente di catturare la variabilità naturale e di confrontare motifs con diversi gradi di conservazione.


La scoperta di motifs è strettamente legata a problemi di [[Allineamento di sequenze|allineamento di sequenze]] locale, poiché implica la ricerca di sottosequenze simili distribuite in regioni diverse. 
Il processo può essere visto come una combinazione tra individuazione di pattern comuni e discriminazione rispetto al rumore di fondo generato da occorrenze casuali.

