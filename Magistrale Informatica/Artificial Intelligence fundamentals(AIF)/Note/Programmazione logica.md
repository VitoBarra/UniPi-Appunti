---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Programmazione logica
---
La programmazione logica rappresenta un paradigma che si avvicina all'ideale dichiarativo: i sistemi vengono costruiti esprimendo conoscenza in un linguaggio formale, e i problemi sono risolti attraverso processi di inferenza su tale conoscenza [[Agenti Knowledge Based|La programmazione logica è una componente chiave degli agenti basati su conoscenza]]. Tale approccio è sintetizzato dall'equazione di Robert Kowalski:$$
\text{Algoritmo} = \text{Logica} + \text{Controllo}
$$[[Logica|Si riferisce al formalismo logico usato per rappresentare conoscenze]] + [[Sistemi di inferenza logica|I meccanismi di controllo eseguono inferenze sui fatti e regole definite]].

Prolog è il linguaggio di programmazione logica più diffuso, utilizzato soprattutto per prototipazione rapida e per manipolazioni simboliche, come la scrittura di compilatori o l'analisi del linguaggio naturale. I programmi Prolog consistono in clausole definite con una notazione differente dalla logica del primo ordine: le variabili sono rappresentate con lettere maiuscole, i costanti con lettere minuscole [[Logica del primo ordine (FOL)|Prolog implementa molte caratteristiche della logica del primo ordine]]. Le clausole vengono scritte in forma inversa rispetto alla logica tradizionale, ad esempio:$$
C \; :- \; A, B
$$indica che $C$ è vero se $A$ e $B$ sono veri. Le liste in Prolog sono espresse con la notazione $[E|L]$, dove $E$ è il primo elemento e $L$ il resto della lista. La potenza di Prolog risiede nel descrivere relazioni tra più argomenti, piuttosto che funzioni con parametri fissi. Le interrogazioni possono produrre tutte le combinazioni di variabili che soddisfano la relazione, grazie al meccanismo di unificazione [[FOL - Algoritmo di unificazione|La unificazione è il meccanismo chiave per associare variabili a termini]].

L’esecuzione dei programmi Prolog avviene tramite un controllo retrogrado a profondità prima (depth-first backward chaining) [[Algoritmo Forward and Backward chaining per Dimostrazione di teoremi|Prolog utilizza backward chaining per provare obiettivi]], tentando le clausole nell’ordine in cui sono scritte. Alcuni aspetti si discostano dall’inferenza logica pura:

- utilizzo della semantica di database [[FOL - Semantica Database|Prolog adotta la semantica di database, con mondo chiuso e nomi unici]], con trattamento particolare di uguaglianza e negazione,  
- funzioni built-in per calcoli aritmetici che vengono eseguite invece di inferite,  
- predicati con effetti collaterali, come input/output o modifiche alla base di conoscenza,  
- omissione del controllo di occorrenza durante l’unificazione,  
- possibilità di ricorsione infinita senza meccanismi di controllo.

Problemi sorgono in presenza di stati ripetuti o percorsi infiniti, poiché il backtracking a profondità prima può non terminare, rendendo Prolog incompleto come dimostratore di teoremi per clausole definite [[Inferenza logica - Backard chaining con FOL|Limitazioni di backward chaining in Prolog per alcuni percorsi infiniti]]. In alternativa, l’inferenza in avanti (forward chaining) costruisce incrementi di soluzione evitando duplicazioni, come avviene nella programmazione dinamica, e può essere emulata in sistemi di programmazione logica tabellare, che combinano l’efficienza dell’approccio bottom-up con l’orientamento agli obiettivi del backward chaining [[Inferenza logica - Forward chaining con FOL|Forward chaining evita ripetizioni e loop infiniti]].

Prolog adotta la semantica di database basata sull'assunzione di nomi unici e sul mondo chiuso: ogni costante e termine ground rappresenta un oggetto distinto e le uniche affermazioni vere sono quelle entailed dalla base di conoscenza. La chiusura del mondo limita l’espressività rispetto alla logica del primo ordine, ma migliora l’efficienza e la concisione del ragionamento [[FOL - Semantica Database|Il concetto di closed-world assumption e unique names assumption è centrale per l’efficienza di Prolog]].

La programmazione logica con vincoli estende Prolog consentendo di lavorare con variabili vincolate invece che semplicemente legate [[Programmazione logica|CLP è un'estensione della programmazione logica classica]]. Le soluzioni consistono in vincoli specifici derivati dalla base di conoscenza, utilizzando algoritmi di risoluzione dei vincoli appropriati. Sistemi CLP (Constraint Logic Programming) combinano algoritmi di soddisfacimento dei vincoli, logica deduttiva e database, offrendo maggiore flessibilità nell’ordine di ricerca, impiegando tecniche come ordinamento euristico dei congiunti, backjumping o cutset conditioning [[Sistemi di inferenza logica|CLP amplia le strategie di inferenza per una maggiore efficienza]]. Alcuni linguaggi, come MRS, permettono la definizione di metaregole per scegliere dinamicamente l’ordine delle inferenze secondo criteri specifici [[Metarule|Le metaregole consentono controlli personalizzati sull'ordine delle inferenze]].
