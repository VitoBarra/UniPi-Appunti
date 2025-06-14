---
Course: "[[Elementi di Complessità e Calcolabilità (ECC)]]"
topic: nota
tags:
  - ECC
---
# Complessita
---
La complessità computazionale studia la difficoltà intrinseca dei problemi da un punto di vista delle risorse necessarie per risolverli. Queste risorse possono essere di varia natura: il tempo di calcolo richiesto, la quantità di memoria necessaria, il numero di comunicazioni in un sistema distribuito, o altre risorse computazionali misurabili. In questa disciplina, l'obiettivo principale non è valutare la bontà o l'efficienza di un singolo algoritmo, ma piuttosto analizzare la difficoltà del problema stesso in relazione ai limiti sulle risorse disponibili.

Alcuni problemi risultano intrattabili se posti sotto vincoli stringenti di risorse. Ad esempio, esistono problemi che non possono essere risolti in tempo polinomiale se la memoria è estremamente limitata, oppure problemi che non ammettono soluzioni esatte se si limita il numero di comunicazioni possibili tra i nodi di un sistema distribuito. Tuttavia, molti di questi problemi possono essere affrontati aumentando le risorse disponibili o adottando approcci alternativi, come il calcolo approssimato.

La complessità forma quindi una gerarchia di classi di problemi in funzione delle risorse. Un problema può appartenere a una classe più ampia se si dispone di più tempo, più memoria o più comunicazioni. Queste gerarchie sono oggetto di studio sistematico, e permettono di comprendere meglio i limiti della computazione stessa. Alcune classi fondamentali sono, ad esempio, $P$, $NP$, $PSPACE$, $EXPTIME$ e così via, ciascuna definita dal tipo e dalla quantità di risorsa considerata.

Inoltre, esistono problemi speciali detti "completi" per una data classe di complessità. Un problema completo rappresenta l'intera difficoltà della classe, poiché ogni altro problema della classe può essere ridotto a esso tramite trasformazioni efficienti. Ad esempio, i problemi $NP$-completi sono rappresentativi della classe $NP$ in quanto, se uno di essi fosse risolvibile in tempo polinomiale, allora lo sarebbero tutti i problemi in $NP$.

Un altro aspetto centrale della teoria della complessità riguarda la misurazione delle risorse. La risorsa "tempo" viene spesso misurata come funzione del numero di passi elementari eseguiti da una macchina astratta (ad esempio una macchina di Turing), in funzione della dimensione dell'input $n$. Analogamente, la "memoria" viene misurata come il numero massimo di celle di memoria utilizzate durante l'esecuzione. Si hanno quindi funzioni di complessità temporale $T(n)$ e di complessità spaziale $S(n)$ che esprimono tali misurazioni.

In alcuni casi, i problemi non ammettono soluzioni esatte in tempi ragionevoli, ma possono essere risolti in modo approssimato, accettando soluzioni che si avvicinano al risultato ottimale entro un certo margine di errore. Questa prospettiva apre lo studio della complessità approssimativa, che analizza quanto sia difficile trovare buone approssimazioni in termini di risorse richieste.

Infine, è importante notare che, pur partendo da modelli di calcolo diversi, come la macchina di Turing deterministica, quella non deterministica, o modelli a circuiti, spesso si ottengono modelli equivalenti in termini di ciò che è calcolabile. Tale equivalenza permette di astrarre dalla specifica macchina e studiare la complessità come proprietà dei problemi stessi.

