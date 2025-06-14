---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Allineamento di sequenze multiple (MSA)
---
L’**allineamento di sequenze multiple** o ***Multiple Sequence Alignment*** (***MSA***) è una generalizzazione dell’[[Allineamento di sequenze pairwise|allineamento pairwise]] in cui il confronto viene effettuato simultaneamente su **più di due sequenze**. L’obiettivo è costruire una disposizione comune che preservi l’ordine dei simboli in ciascuna [[Stringhe|sequenza]] e renda esplicite le corrispondenze tra posizioni considerate omologhe lungo l’intero insieme. Nel contesto biologico questo è particolarmente utile, poiché si hanno spesso sequenze simili provenienti da organismi diversi.

Il problema dell’**MSA** è formulato come [[Problemi di ottimizzazione|problema di ottimizzazione]] e una funzione obiettivo comunemente utilizzata è la **[[Funzioni obiettivo - sum of pairs (SP)|sum-of-pairs (SP)]]**. In questa formulazione, il punteggio complessivo di un **MSA fissato** è definito come la somma dei punteggi di tutti gli **[[Allineamento di sequenze pairwise|allineamenti pairwise]]** indotti dalle colonne dell’allineamento multiplo.

La ricerca dell’**MSA** ottimale rispetto alla funzione **SP** mediante un’estensione diretta degli algoritmi di [[Programmazione Dinamica]] utilizzati per l’[[Allineamento di sequenze pairwise|allineamento pairwise]] richiede la definizione di una tabella di memorizzazione multidimensionale, in cui ogni stato rappresenta simultaneamente una posizione in ciascuna delle sequenze. Il numero di stati cresce come il prodotto delle lunghezze delle sequenze considerate, e il numero di transizioni possibili per stato cresce esponenzialmente con il numero di sequenze $n$. Di conseguenza, la complessità computazionale cresce esponenzialmente in funzione di $n$, rendendo impraticabile la ricerca esatta dell’allineamento ottimale già per un numero moderato di sequenze. Per questo motivo, il problema dell’**MSA** è **[[Classi di complessita - NP-Hard|NP-hard]]**.


Per risolvere il problema del **MSA** vengono usati **approcci euristici**, che rinunciano alla garanzia di **ottimalità globale** per ottenere soluzioni di **buona qualità** in tempi computazionalmente accettabili. Questi approcci esplorano solo una porzione dello spazio delle soluzioni, guidati da ipotesi strutturali sulle relazioni tra le sequenze. Gli approcci principali sono 3: 
- **metodi progressivi**: In questo schema, si stima inizialmente la similarità tra tutte le coppie di sequenze mediante allineamenti pairwise e si utilizza tale informazione per costruire una struttura guida che ne organizza le relazioni. L’allineamento viene quindi costruito in modo incrementale, allineando prima le sequenze più simili e incorporando progressivamente le altre. A partire da un certo punto, le unità da allineare non sono più singole sequenze ma **profili**, ossia rappresentazioni sintetiche di allineamenti parziali già costruiti. Le scelte effettuate nelle fasi iniziali influenzano fortemente il risultato finale e non vengono generalmente riconsiderate.
- **metodi iterativi**, che partono da un allineamento iniziale e lo raffinano attraverso una serie di riallineamenti successivi. In questi metodi, sottoinsiemi di sequenze o profili vengono temporaneamente rimossi e riallineati al resto, accettando le modifiche solo se migliorano la funzione obiettivo. Questo consente di correggere errori introdotti nelle fasi iniziali, al prezzo di un maggiore costo computazionale. 
- **metodi ibridi**:  in cui ogni colonna dell’allineamento viene descritta tramite distribuzioni di frequenza dei simboli o modelli probabilistici. Tali rappresentazioni consentono di integrare informazioni provenienti da più sequenze in modo compatto e di valutare nuove sequenze rispetto a un allineamento già esistente. In questo contesto, l’allineamento di sequenze multiple può essere visto come un processo di ottimizzazione che opera su oggetti più complessi delle singole stringhe.

Le regioni che risultano conservate su molte sequenze tendono a riflettere vincoli funzionali o strutturali, mentre le regioni variabili possono indicare adattamenti specifici o divergenza evolutiva. L’MSA fornisce inoltre una base strutturata per analisi successive, come la costruzione di modelli evolutivi, la definizione di profili di famiglia e l’identificazione di motivi ricorrenti.