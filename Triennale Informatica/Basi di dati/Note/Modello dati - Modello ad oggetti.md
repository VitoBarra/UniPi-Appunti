---
Course: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# Progettazione DB - Modello ad oggetti
---
La _modellazione ad oggetti_ è [[Modelli di dati|modello dati]] per la _[[Modellazione della conoscenza|Modellazione della conoscenza]]_

### Rappresentazione della struttura della conoscenza concreta
#### Oggetto (Definizione)
Un _oggetto_ e un’entità _software_ con stato, comportamento e identità, che modella un’[[Modellazione della conoscenza|entità]] dell’_universo del discorso_. 
Lo stato è costituito da un _insieme di campi_  di qualsiasi complessità che modellano le _proprietà dell’entità_.
Il _comportamento_ è costituito da un insieme di _metodi_, eventualmente _dotate di parametri_, questi modellano le operazioni di base che riguardano l’oggetto e le proprieta derivabili da altre dello stato
Le _operazioni_ applicabili ad un oggetto sono dette _messaggi_ a cui l’oggetto risponde, utilizzando i _propri metodi e manipolando il proprio stato_.


##### Interfaccia del oggetto (Definizione)
l _interfaccia di un oggetto_ specifica l’insieme dei messaggi a cui esso puo _rispondere_, con il tipo dei _parametri e del risultato_, e l’insieme dei campi dell’oggetto che sono accessibili dall’esterno dell’oggetto stesso, con il loro tipo.

##### Identificatore del oggetto (Definizione)
L’_identità di un oggetto_ (_Object Identifier, OID_) e una caratteristica che è associata all’oggetto al momento della creazione, questo _non può essere modificata_ in nessun modo 
_L’identita_ di due oggetti diversi è sempre diversa. 
_L’identità_ modella quelle caratteristiche di un’entità del mondo reale che fanno si che tale entità sia sempre percepita come la stessa anche quando cambiano i valori di alcune delle sue proprietà.

##### Tipo del oggetto (Definizione) 
Un _tipo_ definisce un _insieme di possibili valori_ e le _operazioni ad essi applicabili_. 

Nella costruzione di un modello informatico i _tipi_ scaturiscono dal processo di _astrazione_ con il quale prima si raggruppano entità diverse, perchè ritenute _omogenee_ ai fini dell’_applicazione_ in esame, e poi si prescinde dalle differenze tra le singole entità per evidenziare invece cio che le accomuna e le rende _omogenee_, cioè la loro struttura.

##### Interfaccia tipo oggetto (Definizione)
L’_interfaccia di un tipo oggetto_ specifica i componenti dello stato che sono accessibili _dall’esterno e il loro tipo_.

Nomi dei componenti accessibili dello stato sono detti anche _attributi_ degli oggetti. 
Come accade per le _proprietà delle entità_, un attributo di un oggetto può avere valori di tipo _atomico o strutturato, univoco o multivalore_. 


##### Rappresentazione grafica
la rappresentazione grafica è simile a quella degli oggetti del [[UML - Diagramma degli oggetti|digramma oggetti del UML]] 

è composto da 3 parti dove 
- la prima indica il _nome del oggetto_ (al singolare)
- la seconda indica lo stato del oggetto con i relativi _tipi_
- la terza (opzionale) indica i _vincoli_   

la differenza con _UML_ sta nel fatto che  i tipi dei campi non possono essere di tipo _oggetto_ ma solo di tipi primitivi, ovvero int, real, bool ,date, string

Applicando delle operazioni sui tipi primitivi, o non si possono ottenere dei tipi _non primitivi_
- l’operatore tipo _record_ costruisce un tipo i cui valori sono record, ovvero insiemi di coppie (_etichetta_, _valore associato_). 
	- La sintassi: $[ A_1:T_1; \dots ; A_n:T_n ]$
- l’operatore tipo _enumerazione_, insieme di _etichette_ separate da un punto e virgola tra parentesi tonde. 
	- La sintassi: $(E_1;E_2;\dots;E_n)$
	- Per esempio, il tipo dell’attributo Sesso $(M; F)$.
- l’operatore tipo _sequenza_  costruisce un tipo i cui valori sono _sequenze di valori_ con tipo $T$, la sequenza  è un [[Struttura dati - MultiInsieme|MultiInsieme]] finito e ordinato 
	- La sintassi: $seq \ \ T$

un esempio è
![[IMG_1032.jpeg]]



#### Classi
Le _classi_ modellano le _collezioni_
>[!warning]
>NON sono le _classi_ dei _[[Linguaggi ad oggetti|linguaggi ad oggetti]]_
##### Classe (Definizione)
Una _classe_ e un insieme di oggetti dello stesso tipo, modificabile con operatori `
per includere o estrarre elementi dall’insieme, al quale sono associabili alcuni _vincoli di integrità_


##### Rappresentazione grafica
Solitamente non si rappresentano e si assume che ogni 
- si rappresentano solo elementi di _classi_
- il nome del _tipo_ e la stessa della _classe_
	- Motivo per cui è convenzione dare nomi al _PLURARE_



#### Rappresentazione delle associazioni
##### Associazioni Binarie
Un’associazione fra due _collezioni_ $C_1$ e $C_2$ e una _relazione binaria_ fra $C_1$ e $C_2$, e si rappresenta nella notazione grafica _con una linea_ che collega le classi che rappresentano le due collezioni. 
La _linea_ è _etichettata_ con il nome dell’associazione che di solito viene scelto utilizzando un predicato che dia un significato alla frase con la struttura “_soggetto predicato complemento_” ottenuta leggendo il diagramma da sinistra a destra (o dall’alto al basso), dove 
- il _soggetto_ e il generico elemento della prima collezione 
- il _complemento_ il generico elemento della seconda collezione
Quando non si riesce a trovare un verbo specifico per l’associazione, oppure quando piu associazioni in uno schema finirebbero per avere lo stesso nome, si puo utilizzare come nome `
dell’associazione la _concatenazione dei nomi delle classi_ coinvolte.

L’_univocita_ di un associazione, rispetto ad una classe $C_1$, si rappresenta con una _freccia singola_ sulla _linea che esce_ dalla classe $C_1$ ed _entra_ nella classe $C_2$ e si legge come “ad ogni elemento della classe $C_1$ corrisponde un unico elemento nella classe $C_2$”,

l’assenza di vincolo di _univocita_ è indicata da una _freccia doppia_. 


la _parzialità_ è rappresentata con un taglio sulla linea vicino alla freccia,
il _vincolo di totalità_ e rappresentato dall’assenza del taglio.
![[IMG_1033.jpeg]]

Le associazioni stesse possono avere delle _proprietà_ che descrivono l _associazione_ e sono rappresentata con un rettangolo collegato alla linea dell _associazione_
![[IMG_1034.jpeg]]
Alternativamente puo essere modellata interpretando l _associazione_ come un _[[Modellazione della conoscenza|entita]]_ è ottenendo quindi qualcosa del tipo
![[IMG_1035.jpeg]]


Le _associazioni_ possono essere anche ricorsive ovvero avere come partenza e fine la stessa _collezione_.
Per la corretta interpretazione bisogna etichettare le punte della _associazione_ con il _ruolo_ che hanno i due componenti in un _instanza di associazione_ 
![[IMG_1036.jpeg]]

##### Associazioni n-arie
esistono _associazioni_ $n$-arie ma sono complicate e di scarso utilizzo

#### Classi gerarchiche
##### Gerarchia di tipi (Definizione)
una _gerarchia di tipi_ è un [[Ordinamenti|ordinamento parziale]] sull’insieme dei tipi _tale che_ un valore che _appartiene al sottotipo_ può essere utilizzato _in tutti i contesti_ in cui e previsto un valore del _super tipo_.

##### Definizione per ereditarieta
la definizione di un _interfaccia di tipo oggetto_  $T$ è data da _per eridarieta_ quando _partendo_ da un tipo $\mathcal{J}$ si _specificando_ quali attributi _aggiungere_ a $\mathcal{J}$ e come, eventualmente, _modificare_ i tipi ereditati da $\mathcal{J}$ (__ovveride__)
Dove sul __ovveride__ esiste il vincolo di _eredità stretta_ ovvero, nuovo tipo del _proprieta_ modificato deve essere un _sottotipo_ del _tipo origiale_, per assicurare compatibilità con i contesti dove si utilizzava il tipo $\mathcal{J}$

un tipo $T$ può essere definito per eredita 
con 
- _eredita singola_(gerarchia ad [[Struttura dati - Alberi|albero]]): partendo da un singolo _supertipo_
- _eredita multipla_(gerarchia a [[Struttura dati - Grafi|grafo]]): ereditando contemporaneamente da più antenati
	- Questo puo portare problemi quando si eredita la stessa _proprietà_ da antenati diversi ([[diamond Problem|diamond Problem]])

Cio che rende questo meccanismo interessante e, in particolare, la combinazione di sovraccarico dei messaggi (overloading) e risoluzione dei nomi dei messaggi a tempo di esecuzione (late
binding).


##### Gerarchia di inclusione
La _gerarchia di inclusione_ è una _relazione_ di [[Ordinamenti|ordinamento parziale]] sull’insieme delle classi _tale che_ 
_se_ $C_1$ e una _sottoclasse_ di $C_2$ (è inclusa in $C_2$), 
_allora_ gli elementi di $C_1$ sono un sottoinsieme degli elementi di $C_2$ 
- $C_1$ eredita le _associazioni_ definite su $C_2$ (_vincolo estensionale_)


Come conseguenza, quando nel modello si _aggiunge un elemento_ ad una _sottoclasse_, esso viene automaticamente a far parte anche delle _superclassi_. 

Si impone il _vincolo strutturale_: se $C_1$ e una sottoclasse di $C_2$, allora il _tipo degli elementi_ di $C_1$ e un _sottotipo del tipo_ degli elementi di $C_2$.
Questo si fa per evitare problemi di _tipo_

si possono definiscono più _sottoclassi_ di una _stessa classe_, e sul insieme di _sottoclassi_ si definiscono i _vincoli_:
- _vincolo di disgiunzione_(sottoclassi disgiunte): se ogni _coppia di sottoclassi_ nel insieme è _disgiunta_, ovvero e priva di elementi comuni 
- _vincolo di copertura_ (sottoclassi copertura): se l’[[Insiemi Matematici|unione]] degli elementi delle sottoclassi _coincide_ con l’insieme degli elementi della _superclasse_

I _due vincoli_ sono _indipendenti_ fra loro;
se sono entrambi soddisfatti, l’ _insieme di sottoclassi_ costituisce una _[[Partizione di un insieme|partizione]]_ della _superclasse_.

Una _sottoclasse_ puo essere definita anche a partire da un’altra sottoclasse, modellando cosi _gerarchie a più livelli_. 

##### Rappresentazione grafica
![[IMG_1037.jpeg]]
![[IMG_1038.jpeg]]




### Conoscenza Astratta
della  [[Modellazione della conoscenza|conoscenza astratta]] nel modellare una situazione reale, vanno rappresentati i _vincoli d’integrita_ che impongono restrizioni sui possibili valori della _conoscenza concreta_.
I vincoli possono essere descritti in due modi 
- _Dichiarativo_: con formule del [[Logica proposizionale|calcolo dei predicati]]
- _Operativo_: mediante controlli da eseguire nelle operazioni (di base o degli utenti).
si preferisce l’approccio _dichiarativo_ siccome più facile stabilire la _coerenza dei vincoli_ con la _definizione dei [[Analisi dei requisiti|requisiti]]_ ed apportare modifiche per _adeguarli a nuove esigenze_
- sono utili per gli _strumenti di progettazione_ per trovare eventuali _inconsistenze o ridondanze_, cioè vincoli logicamente implicati da altri
- si _evita di ripetere i controlli_ in più operazioni.

##### Rappresentazione grafica
Nella definizione di una _classe di entità_  si gli attributi _marcati con la stringa_ $\ll K\gg$
sono una [[Modello Relazionale - Chiavi|chiave]].
Se vi sono altre n chiavi si usano le stringhe $\ll K_1\gg \dots \ll Kn\gg$.

Vincoli _generali andrebbero_ espressi usando un opportuno formalismo, come l’OCL (Object Constraint Language) proposto per l’UML

![[IMG_1039.jpeg]]
> [!tip]
> In uno _stadio iniziale_ del progetto può essere sufficiente descrivere i vincoli usando il _linguaggio naturale_

#### Rappresentazione del conoscenza procedurale
Mentre la conoscenza delle operazioni di base viene modellata con il meccanismo dei metodi degli oggetti, le operazioni degli utenti vengono modellate con il meccanismo delle transazioni, programmi sequenziali che consentono di modellare l'evoluzione dell'universo del discorso astrae da malfunzionamenti e da interferenze indesiderate con altre transazioni che accedono concorrentemente ai dati. Un'operazione (di base o degli utenti) si specifica, a questo livello di astrazione, dando le seguenti informazioni:
- Il nome, un identificatore non già utilizzato per altri elementi dello schema;
- Lo scopo dell'operazione, descritto con un testo in linguaggio naturale;
- Gli argomenti dell'operazione, un elenco di coppie "identificatore: tipo";
- Il tipo del risultato;
- Il testo di eventuali messaggi di errore;
- Le classi e le associazioni che usa ma non modifica;
- Le classi e le associazioni che modifica, per aggiunta di elementi o modifica di attributi degli elementi;
- Due condizioni, la precondizione e la postcondizione, che devono essere vere nello stato di partenza e nello stato di arrivo della base di dati. In una condizione si possono usare i nomi dei parametri o le classi che l'operazione usa o modifica. Queste informazioni si danno nel formato (descrittore operazioni) mostrato in Figura 2.14.

![[IMG_1040.jpeg]]

#### Rappresentazione della comunicazione 
Nel modellare la comunicazione con il sistema informativo, e in particolare con il sistema informatico, si suppone che questa comunicazione avvenga come un dialogo, nel quale il sistema presenta all'utente una forma caratterizzata da un certo aspetto, dalla presenza di alcuni campi modificabili e dalla presenza di alcuni elementi attivi (bottoni, menu, barre di scorrimento, ecc.). L'utente modifica (o riempie) i campi modificabili oppure agisce sugli elementi attivi, e il sistema reagisce a queste azioni dell'utente modificando la forma, o ritirandola, o presentando una nuova forma, fino a che l'interazione non termina. Questo modello può essere esteso, supponendo, ad esempio, che il sistema sia disponibile a presentare all'utente più forme nello stesso momento e a permettere all'utente di agire su queste forme in qualunque ordine.

Un'ulteriore estensione riguarda la possibilità per l'utente di sottomettere al sistema non solo forme riempite ma anche interrogazioni scritte in un linguaggio formale opportuno, che il sistema esegue. Un'ultima estensione riguarda la possibilità per l'utente di effettuare interazioni meno strutturate, sottoponendo al sistema richieste in forma testuale o con dialoghi vocali in linguaggio naturale. Queste forme di comunicazione non strutturata sono ovviamente essenziali in un sistema informativo in cui siano presenti anche componenti umane.

Il modello ad oggetti è particolarmente adatto a modellare la comunicazione non solo per la possibilità di catturare la natura "attiva" dei componenti delle interfacce grafiche, ma anche perché esso permette di trarre vantaggio dal fatto che tra i tipi degli oggetti che costituiscono un'interfaccia grafica (detti widget) sono naturalmente definite ricche gerarchie di sottotipo e di eredità.