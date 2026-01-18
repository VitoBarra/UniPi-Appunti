---
Course: "[[Human Language Technology (HLT)]]"
Course 2: 
tags:
  - HLT
Area: 
topic: 
SubTopic:
---
# Espressioni regolari
---
Le **espressioni regolari** sono **un formalismo matematico** e computazionale utilizzato per descrivere **insiemi di stringhe** attraverso un linguaggio simbolico compatto. Esse consentono di specificare pattern astratti che possono essere ricercati, confrontati o validati all’interno di sequenze testuali, costituendo uno strumento fondamentale in numerosi ambiti dell’informatica teorica e applicata.

Un’espressione regolare è costruita a partire da un **[[Alfabeto|alfabeto]]** di simboli e da un insieme di **operatori sintattici** che ne definiscono la combinazione, la ripetizione e l’alternativa. L’alfabeto rappresenta l’insieme dei caratteri che possono comparire nelle stringhe di interesse, mentre gli operatori consentono di costruire espressioni più complesse a partire da simboli elementari. Dal punto di vista formale, le espressioni regolari definiscono **linguaggi regolari**, riconoscibili da automi finiti.

La scrittura di un’espressione regolare si basa su alcune operazioni fondamentali. La **concatenazione** rappresenta la giustapposizione di simboli o sotto-espressioni e descrive la successione ordinata dei caratteri all’interno di una stringa. L’**alternativa** consente di specificare scelte tra più pattern possibili, definendo insiemi di stringhe che soddisfano almeno una delle alternative ammesse.

Un ruolo centrale è svolto dai **quantificatori**, che permettono di controllare il numero di occorrenze di un simbolo o di una sotto-espressione. Essi consentono di esprimere ripetizioni opzionali, multiple o vincolate entro un certo intervallo, introducendo una notevole capacità di astrazione. L’uso dei quantificatori permette di descrivere famiglie di stringhe potenzialmente molto ampie tramite espressioni compatte.

Le **classi di caratteri** permettono di indicare insiemi di simboli alternativi che possono comparire in una determinata posizione della stringa. Le classi possono essere definite in modo esplicito o come intervalli e rappresentano un meccanismo essenziale per generalizzare la descrizione dei pattern. L’operatore di negazione applicato alle classi consente di escludere specifici simboli, ampliando ulteriormente la capacità descrittiva del linguaggio.

Le espressioni regolari supportano inoltre il **raggruppamento**, che consente di trattare sequenze di simboli come unità logiche. Il raggruppamento introduce una struttura gerarchica all’interno dell’espressione, permettendo di applicare operatori e quantificatori a sotto-espressioni complesse. L’interazione tra raggruppamento, quantificatori e alternativa costituisce il meccanismo principale attraverso cui vengono costruiti pattern articolati.

Dal punto di vista sintattico, i costrutti fondamentali utilizzati nella scrittura di un’espressione regolare possono essere riassunti come segue:
- `.`  qualsiasi carattere
- `*`, che indica **zero o più occorrenze** dell’elemento precedente;
- `+`, che indica **una o più occorrenze**;
- `?` zero o una occorrenza  
- `{n}` esattamente n occorrenze  
- `{m,n}` da m a n occorrenze  
- `[]` classe di caratteri  
- `[^ ]` classe di caratteri negata  
- `()` raggruppamento  
- `|` alternativa  
- `^` inizio della stringa  
- `$` fine della stringa


Dal punto di vista computazionale, il matching di un’espressione regolare contro una stringa può essere interpretato come un problema di riconoscimento di linguaggi formali. A seconda dell’implementazione, questo processo può essere ricondotto alla simulazione di automi finiti o all’uso di strategie di backtracking. L’efficienza del matching dipende dalla struttura dell’espressione e dalla lunghezza della stringa, rendendo rilevante l’analisi della complessità nei contesti applicativi.

Nel quadro generale dell’analisi computazionale delle stringhe, le espressioni regolari rappresentano un compromesso tra **potenza espressiva** e **semplicità computazionale**, risultando sufficientemente flessibili per modellare un’ampia classe di pattern senza introdurre la complessità di formalismi più espressivi.
