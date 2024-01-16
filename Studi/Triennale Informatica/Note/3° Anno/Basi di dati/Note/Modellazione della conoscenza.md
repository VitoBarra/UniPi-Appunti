---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Modellazione della conoscenza
---

### Modellazione della conoscenza
Si vuole creare un _modello astratto_ del _universo del discorso_ questo rappresentare la parte della realtà che ci interessa, fare ciò ci permette di analizzare e lavorare più facilmente sui dati che ci interessano  


#### Modello Astratto (Definizione)
Un _modello astratto_ è la rappresentazione _formale_ di idee e conoscenze relative ad un fenomeno.

Questa definizione mette in evidenza
1. Il modello è una _rappresentazione_ di alcuni fatti di un fenomeno
2. La rappresentazione è data con un _linguaggio formale_
3. Il Modello è il risultato di un processo di _interpretazione_ di un fenomeno, guidato dalle _idee_ e _conoscenze_ già possedute dal soggetto che interpreta

### Creazione di un modello
Per creare un modello ciò bisogna chiedersi _cosa_ e _come_ si vuole modellare, queste domande vengono risposte dai vari aspetti del modello

#### Aspetto ontologico (cosa si modella?)
l _aspetto ontologico_ (Descrizione di ciò che esiste) riguarda il _cosa_ si vuole modellare, quali _fatti_ ci interessano, ovvero quali parti della realtà ci interessa considerare come _universo del discorso_. Questo ci permette di _eliminare dettagli inutili_ agli scopi per cui si sta realizzando il modello stesso.

 si divide in 3 categorie
##### Conoscenza concreta
la _Conoscenza concreta_ riguarda ciò che esiste in un _dato momento_ e rappresenta lo _stato_ del _universo del discorso_ in quel momento.
Lo stato è una cosa mutabile che dipende dal 
- _Tempo_: di natura continua   
- Eventi: di natura _discreta_   
entrambi possono cambiare lo _stato del universo_

Le parti della conoscenza concreta sono	
###### Entità (Definizione)
un _entità_ è un qualcosa di _astratto o concreto_ di cui si vuole rappresentare alcuni _fatti_  

###### Proprietà (Definizione)
una _proprietà_ è un fatto che descrive, una qualità di un _entità_

Ogni Proprietà ha associato un _dominio_ ovvero i valori che puo assumere e ha le seguenti caratteristiche:
- _atomica/struttura_ : _atomica_ non può essere ulteriormente scomposta, una _strutturata_ si
- _univoca/multivalore_: _univoca_ se la proprieta ha un solo valore altrimenti _multivalore_
- _Totale/parziale_: _Totale_ se la proprietà è _obbligatoria_ altrimenti è detta parziale

Tutte queste proprietà sono indipendenti e i valori di una proprietà _strutturata_ hanno a loro volta queste _caratteristiche_

###### Tipo (Definizione)
un _tipo_ è una descrizione astratta di ciò che accumuna un insieme di _entità omogeneo_ (della stessa natura)  _esistei o possibili_

>[!info]
>Questa è una collezione infinita di tutte le entità di quel tipo _esistenti_ e _posibili_

###### Collezione (Definizione)
una _collezione_ è un insieme finito di entità variabile nel tempo di _entità omogenee_ interessanti del universo del discorso 

gli elementi di una collezione in un dato momento è detta __estensione della collezione__


###### Generalizzazione (Definizione)
_sia_ $C_{sub}$  una _specializzazione_ della collezione  $C_{sup}$
_allora_ $C_{sub}$ e un _sottoinsieme_ di  $C_{sup}$ e gli
elementi di $C_{sub}$ ereditano le caratteristiche degli elementi $C_{sup}$, oltre ad averne altre _proprie_.


###### Istanza di associazione (Definizione)
un _istanza di associazione_ è un fatto che correla due o più entità stabilendo un legame logico

###### Associazione (Definizione)
Un _associazione_ tra le collezioni $C_1, \dots , C_n$ è un insieme di _istanze di associazione_ tra elementi di $C_1, \dots , C_n$, che varia in generale nel tempo.

Il [[Prodotto Cartesiano|prodotto cartesiano]] delle estensioni di $C_1, \dots , C_n$ e detto il _dominio dell’associazione_

###### Molteplicità (Definizione)
La _molteplicità_ di un’_associazione_ fra $X$ ed $Y$ riguarda il numero massimo di elementi di $Y$ che possono trovarsi in relazione con un elemento di $X$ e viceversa.
Si dice che l’associazione è 
- _Univoca_: da $X$ ad $Y$ se ogni elemento di $X$ puo essere in relazione con _al più_ un elemento di $Y$
- _Multivalore_:  se ogni elemento di $X$ si possono associare $n$ valori in  $Y$
e valgono le stessi definizione per le associazioni da $Y$ a $X$ e i vincoli sulle dure direzioni sono _indipendenti l uno dal altro_

###### Cardinalità (Definizione)
la _cardinalità_ di una _associazione_ fra $X$ e $Y$ descrive contemporaneamente la molteplicità del associazione e la sua inversa.
le cardinalità sono definite come:
- $(1,1)$ un ad uno
- $(N,1)$ molti ad uno
- $(1,M)$ uno a molti
- $(N,M)$ molti a molti


###### Totalità di un associazione (Definizione)
La _totalità di un’associazione_ fra due _collezioni_ $X$ ed $Y$ riguarda il numero minimo di elementi di $Y$ che sono associati ad ogni elemento di $X$.
Se almeno un _entità_ di $Y$ deve essere associata ad _ogni entità_ di $X$, si dice che l’associazione è _totale_ su $X$, _altrimenti_ l’associazione è _parziale_.

>[!tip] 
>Si può _generalizzare_ sostituendo $X=X_{1}$ e $Y=X_{1},\dots X_{n}$


###### Struttura della conoscenza concreta (Definizione)
La _struttura della conoscenza concreta_ riguarda la conoscenza dei seguenti _fatti_:
1. _esistenza_ di alcune _collezioni_, nome delle collezioni, _tipo_ degli elementi delle collezioni (e quindi, nome e caratteristiche delle _proprietà_ di tali elementi); `
2. _esistenza_ di alcune _associazioni_, nome delle associazioni, _collezioni_ correlate da ogni associazione, proprietà strutturali delle associazioni. `

###### Conoscenza concreta (Definizione)
La _conoscenza concreta_ presuppone che sia nota la _struttura di tale conoscenza_, e riguarda la conoscenza dei seguenti fatti:
1. Quali _entità_ esistono, che tipo ha ciascuna di queste entità, e quali sono i valori delle sue _proprietà_ (dominio); `
2. Per ogni _collezione_ esistente, quali _entità_ appartengono a tale collezione (_estensione_ della collezione);
3. Per ogni _associazione_, quali _istanze di associazione_ appartengono a tale associazione (_estensione_ dell’associazione).

##### Conoscenza Astratta
La conoscenza astratta riguarda i fatti generali che descrivono 
- La _struttura_ della _conoscenza concreta_ 
- Le restrizioni sui valori possibili della conoscenza concreta e sui modi in cui essi possono evolvere nel tempo (_vincoli d’integrita_),
- Regole per derivare nuovi fatti da altri noti.
  
i _vincoli di integrità_ sono classificati in 

__vincoli statici__: definiscono _condizioni sui valori_ della conoscenza concreta che devono essere soddisfatte _indipendentemente_ da come evolve l’_universo del discorso_. 
Le condizioni possono riguardare:
1. I _valori_ di una proprietà, alcuni esempi sono 
	- un numero maggiore o minore di $h$, 
	- il _tipo_(int, char,string) di dato di una proprietà
	- Un qualsiasi vincolo sui valori
2. I _valori_ di _proprietà diverse_ di una stessa _entità_ 
	- qualsiasi tipo di _vincolo  sui valore_ di una proprietà che dipende da un _altro valore_ sulla stessa _riga_
	- per ogni impiegato le trattenute sulla paga devono essere inferiori ad un quinto dello stipendio; 
	- se X e sposato con  Y allora il suo stato civile e coniugato.
3. I _valori_ di _proprietà_ di _entità diverse_ di uno stesso insieme.
	- Sono _vincoli_ su un insieme di _colonne_
	- le matricole degli studenti sono tutte diverse; 
	- se due persone hanno _la stessa data dinascita_, allora hanno anche la _stessa eta_; 
	- se una persona $X$ e sposata con $Y$, allora $Y$ e sposata con $X$. 
	- Un insieme di proprietà e' [[Modello Relazionale - Chiavi|chiave]], rispetto ad una collezione di  elementi 
4. I _valori di proprietà_ di _entità_ di _insiemi diversi_
	- il presidente della commissione degli esami deve essere il titolare del corrispondente corso.
5. _Caratteristiche_ di _insiemi_ di _entità_. 
	- Il numero degli studenti e inferiore ad un limite massimo prestabilito 
	- Un laureato in Informatica deve aver accumulato almeno 180 CFU.

__Vincoli dinamici__: definiscono delle _condizioni_ sul modo in cui la _conoscenza concreta può evolvere_ nel tempo. 
- Uno studente di un anno di corso non può iscriversi ad un anno precedente dello stesso corso di studio
- Una data di nascita non può essere modificata.

_un vincolo statico_ riguarda ogni singolo stato dell’universo del discorso,
_un vincolo dinamico_ riguarda le transizioni da uno stato ad un altro 

##### Conoscenza procedurale
L’_universo del discorso_ e una realtà in _evoluzione_ che _interagisce_ con un _ambiente_
Questa riguarda le operazioni a cui può essere soggetta la _conoscenza concreta_, l’effetto di tali operazioni ed il modo in cui esse si svolgono.
la conoscenza procedurale è classificata come 
- _Conoscenza delle operazioni degli utenti_: le _operazioni_ con le quali avvengono le _interazioni_ con l’ambiente esterno per fornire i servizi previsti
- _Conoscenza delle operazioni di base_: le _operazioni_ elementari che interessano le _entità_ dell’universo del discorso per produrre determinati effetti, creazione, modifica, cancellazione che devono soddisfare le  condizioni espresse dai _vincoli d’integrità_


##### Comunicazione
La _comunicazione_ riguarda le modalità offerte agli utenti del sistema informativo per `
scambiare _informazioni_ con il sistema e per accedere alle risorse informative rispettando le regole e le possibilità loro concesse.
Modellare _la comunicazione significa_ anche rappresentare le _interfacce del sistema_ informativo
Si osservi che la conoscenza concreta, astratta e delle operazioni di base puo essere modellata facendo riferimento essenzialmente all’universo del discorso, sia pure visto in funzione delle necessita del sistema informativo di un’organizzazione. 
Passando invece alla conoscenza delle operazioni degli utenti, e ancor piu alla comunicazione, l’interesse si sposta gradatamente dall’universo del discorso al sistema informativo stesso. 
Poiche la modellazione è in generale finalizzata alla progettazione di un sistema informativo che modifichi quello preesistente, gli strumenti per modellare procedure e comunicazione possono essere usati per rappresentare tanto il sistem informativo esistente quanto quello in via di progettazione.L’interesse verso questo aspetto della progettazione e della modellazione, in particolare verso la modellazione dei dialoghi fra gli utenti e il sistema informatico, e molto `
cresciuto negli ultimi anni poiche, con lo sviluppo degli strumenti hardware e software che supportano la realizzazione di applicazioni con interfaccia grafica, la realizzazione di modalità di interazione gradevoli e personalizzate ai diversi tipi di utenti coinvolti ha assunto un’importanza sempre maggiore, sia come requisito, sia per cio che riguarda la quantita di lavoro che i programmatori dedicano alla realizzazione `
dell’interfaccia stessa.

#### Aspetto linguistico astratto (come si modella?)
L’_aspetto linguistico astratto_ riguarda gli _strumenti concettuali_, o _meccanismi di astrazione_ adottati per modellare l’universo del discorso.

Un _meccanismo di astrazione_ è lo strumento fondamentale per cogliere un aspetto `
della situazione da descrivere, _tralasciando dettagli_ ritenuti in quel momento poco
significativi (l’astrazione come forza semplificatrice).

#### Aspetto linguistico concreto (con quale linguaggio formale si definisci il modello?)
L’_aspetto linguistico concreto_ riguarda le caratteristiche, e la definizione, del _linguaggio formale_ usato per costruire il modello. 
Una volta _fissati i meccanismi di astrazione_ da usare per modellare, si possono usare linguaggi formali con caratteristiche molto diverse che _supportano i meccanismi di astrazione_ prescelti, a seconda degli obiettivi che ci si prefigge con la costruzione del modello. Si possono usare linguaggi di specifica non eseguibili, linguaggi logici o linguaggi di programmazione

#### Aspetto Programmatico (come si procede nella costruzione del modello?)
L’_aspetto pragmatico_ riguarda la _metodologia_ da seguire nel processo di modellazione.
Una _metodologia_ è un insieme di regole finalizzate alla _costruzione del modello  informatico_. 
La natura delle metodologie dipende dal tipo di modello da costruire e quindi dal _livello di dettaglio_ al quale vanno trattati i vari aspetti del modello.