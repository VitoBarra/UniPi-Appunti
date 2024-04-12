---
Subject: Interazione Uomo Macchina
topic: nota
tags: IUM
---

Prev: [[Interazione Uomo Macchina (IUM)]]

# Information Architecture
---
l _architettura del informazione_ è lo studio di come strutturare, organizzare e etichettare il contenuto di una _GUI_ in una maniera efficace e sostenibile. L'obiettivo è quello di aiutare l utente a _trovare informazioni_ e completare compiti.

i componenti del _Information Architectre_ (IA) sono
- _Schemi organizativi e strutture_: categorizzazione e  struttura del informazione
- _Sistemi di etichettatura_: nomi dato al informazione
- _Sistemi di navigazione_: come l utente si muove tra l informazioni
- _Sistemi di ricerca_: come l utente cerca le informazioni


le Strutture più comuni sono
_Strutture gerarchiche_: Strutture gerarchiche o ad albero sono solitamente strutture del informazioni organizzate in moda _Top-Down_, si passa da un concetto più generale (partent) ad uno più specchio (children) 
![[Pasted image 20230610190443.png]]
_Strutture sequenziali_: sono strutture dove al utente è richiesta di andare step-by-step seguendo un percorso di contenuto specifico
![[Pasted image 20230610190505.png]]
_struttura a matrice_: una struttura dove il contenuto è collato in modi diversi e permette al utente di muoversi tra le informazioni con il percorso che preferisce
![[Pasted image 20230610190521.png]]
_Database Model_: questa struttura prende un approccio _Bottom-up_ e si basa fortemente sui metadati. questo permette al utente di avere un esperienza dinamica  ricevendo risultati di ricerche correlate e con la possibilità di fare ricerche più strutturate con filtri.
![[Pasted image 20230610191316.png]]

Le _Strututre_ devono essere pianificate in modo che possono cresce (aggiungendo nuovi contenuti) e devono essere Sostenibili ovvero non devono essere troppo vuote o troppo profondo
![[Pasted image 20230610191809.png]]
siccome questa cosa puo portare confusione.
trovare il giusto bilanciamento puo essere difficile.


per la costruzione di una una buona _Information Architecture_ bisogna caprie l  interdipendenza tra
- _User_: tipo di utenti, compiti, bisogni, esperienza nella ricerca di informazioni, Governance e priorita
- _Contesto_: obbiettivi di bussines, fondi, politica, cultura , tecnologia, risorse, vincoli
- _Contenuto_: obiettivi di contenuto, tipo di documento e di dati, volumi , struttura esistenti
![[Pasted image 20230610122751.png]]


### Schemi organizzativi e strutture
sono di due tipo _schemi esatti_ e schemi _soggettivi_
#### Schemi organizzativi esatti
sono tutti gli schemi che per organizzare l informazione si basano su una _metrica oggettiva_ e divido l informazione in sezioni mutualmente esclusive.

questo tipo di schema è facilmente progettabile è organizzabile per i progettisti ma più difficile da usare e capire per l utente, infatti spesso non sono cosi utile al utente. 

alcuni esempi sono
_Schema alfabetico_ si usa l alfabeto per organizzare i dati un esempio è la rubrica telefonica.
![[Pasted image 20230610124416.png]]
in questo caso la ricerca alfabetica è usato come metodo di ricerca secondaria infatti dal punto di vista del utente puo essere tedioso cercare scrollando, primariamente si utilizza la ricerca del contatto.

_Ordine cronologico_: si organizzano le informazioni per data. molto funziona in servizio come google foto
![[Pasted image 20230610124703.png]]
in questo caso è molto intuitivo per l utente e utile 

_Schema geografico_: si organizzano le informazioni basandosi sul luogo geografico. 
un buon esempio sono i servizi di noleggio monopattino
![[Pasted image 20230610124838.png]]
qui c è un [[Principi di progettazione del interazione|mapping]] luogo icone. infatti è un modo molto efficace in questo caso

#### Schemi organizzativi Soggettivi 
sono schemi che categorizzano l informazione in un modo che puo essere _specifico_ per l organizzazione o il campo di lavoro

Questa organizzazione è _più difficile_ per i designer ma molto _più utile_ per l utente rispetto ai _schemi esatti_. Infatti per realizzare questo tipo di schemi c è bisogno di fare molto studio sugli utenti.

questo tipo di organizzazione puo essere molto utile al utente in quanto lo aiuta a imparare come funziona il sistema facendogli fare connessioni tra _contenuto_ e _pezzo di interfaccia_.


alcuni esempi sono
_Schema per topic_: si organizzano le informazioni basandosi sul tipo ad esempio i generi di netflix
![[Pasted image 20230610145536.png]]

_Schema per task_: si organizzano le informazioni basandosi sulle attività, necessita, processi o domanda del utente
es  il creare un nuovo file su google drive o i menu di VLC studio
![[Pasted image 20230610150055.png]]
_Schema per Audience_: si dividono le informazioni per tipo di publico che deve accedere a quelle informazioni.
es. I profili netflix
![[Pasted image 20230610150230.png]]
questo tipo di organizzazione puo presentare delle problematiche se i contenuti non si dividono bene tra i tipi di pubblico e in generale vanno in contenuto va identificato e associato.
sono di due tipi _Open_ e _closed_ che indicano se l utente puo o no navigare tra un tipo di utente al l altro. 
I profili netflix sono un esempio di tipo _open_


_Schema per metafore_: aiuta l utente mettendo in relazioni i dati con concetti familiari. é spesso usato nel design di interfacce 
es explorer di windows
vì![[Pasted image 20230610150750.png]]

#### Ibridi
si possono mischiare più tipi di schemi il che puo essere utile quando non c è un modo chiaro di scegliere come organizzare i dati. Bisogna pero cercare di tenere gli schemi il più semplice possibile perché una complessità troppo altra puo dare _confusione_ al utente.

### Etichettature
Dipende unicamente dal campo  e si stratta di studiare il campo specifico per dare i nomi giusti alle informazioni

### Navigazione
lo studio delle  _navigazione_ in IA riguarda come l utente si orienta nel interfaccia, e il suo obiettivi principale è permettere al utente di trovare le informazioni.

i principi per garantire una buona navigazione sono _findability_ e _discoverability_
dove
per _findability_ si intende la capacita delle feature di essere trovate li dove l utente si aspetta di trovarle. Quanto l interfaccia permette al utente di trovare le informazioni che sta cercando.
- piazzare gli elementi in modo coesistente e rispettando gli standard del campo specifico riesce a garantire una buona _Findability_  
per _Discoverability_ si intende la capacita del interfaccia di far scoprire nuove informazioni o nuove feature che l utente non stava intenzionalmente cercando.
- questa è più difficile da sviluppare e solitamente si mettono le nuove fauture vicino a quelle più usate o si usano strumenti come i Wizzard (tutorial guidati) ![[Pasted image 20230610174822.png]]

### Pattern comportamentali degli utenti
quansi si parla di ricerca di informazioni sui motori di ricerca o su una barra di ricerca in generale ci sono delle classi di pater di comportamento comuni e sono
_Quitting_: l utente non trova  l informazione di suo interesse esce
![[Pasted image 20230610181002.png]]
_Narrow_: l utente fa una ricerca e successivamente diminuisce i risultati aggiungendo filtri o tool di riordinamento 
![[Pasted image 20230610181040.png]]
_expand_: l utente fu una ricerca e espande i risultati es altre pagine di google
![[Pasted image 20230610181136.png]]
_Perl Growing_: l utente fa una ricerca e apre link presenti sul risultato (chiamato anche mining Topics). un esempio tipico è wikipedia
![[Pasted image 20230610181220.png]]
_pogosicking_: l utente fa una ricerca e apre un risultato e torna sulla ricerca e ne apre altri
![[Pasted image 20230610181514.png]]

_Trashing_: l utente guardai i risultati e cambia la query per fare un altra ricerca andando per tentativi
![[Pasted image 20230610181522.png]]
_berry picking_ l utente fa una ricerca e con le informazioni trovate fa una nuova ricerca
![[Pasted image 20230610181814.png]]


alcuni di questi pattern sono _AntiPattern_  ovvero dei pattern che dobbiamo cercare di evitare, ad esempio _Pogosticking_, _Thrashing_ and _Berry picking_, possono succedere ma se succedono troppo spesso o troppo a lungo possono dare frustrazione. Se succede spesso a molti utenti allora probabilmente sono sintomi di una cattiva _information Architecture_.


### Design Pattern
un pattern di design sono delle delle risposte comuni che funzionano  in risposta agli _antipattern_
1. _autocompletamento_: auto completamento nella barra di ricerca in moda da aiutare l utente a formulare la ricerca
	- ![[Pasted image 20230610184619.png]]
2. _autosuggest_: simile al auto completamento aiuta a cercare cosa relative ma anche distanti a quello che sta scrivendo
3. _Risultati istantanei_: dare la ricerca live ovvero si danno i risultati mentre si sta cercando 
4. _Did you mean_: si cerca di interpretare la query con una simile "piu sensata" solitamente corregge gli errori di scrittura
5. _AutoCorrect_: invece di suggerire la correzione della query ricerca direttamente la query corretta.
6. _best Frist_: si mostrano i risultati della ricerca migliori, gli algoritmi per decidere il _migliore_ sono vari ma si basano su importanza, popolarita, data, formato e cosi via
	- ![[Pasted image 20230610184638.png]]
7. _Metch parziali_: mostra i risultati piu simili alla query per evitare situazioni di 0 risultati.
8. _ricerche correlate_: mostrare oltre cio che si è cercato risultati a ricerche correlate
9. _ricerca federata_: si fa ricerca contemporaneamente in piu database e poi il risultati sono un mix dei risultati
	- ![[Pasted image 20230610184832.png]]
10. _Navigazione faccettata_: si da al utente la possibilità di fare ricerche più raffinate includendo dei metadati
	- ![[Pasted image 20230610184954.png]]
11. _Ricerca avanzata_ permettere al utente di usare fare una ricerca avanzata aggiungendo opzioni  prima di fare la ricerca. Un esempio sono gli operatori logici
	- ![[Pasted image 20230610185009.png]]
12. _Scoped Search_: se i contenuti sono organizzati in categorie si possono usare dropdown menu per mostarde solo i risultati di quella categoria 
13. _Personalizazione_: i risultati dipendono  anche dal utente es. google map che mostra la posizione in cui sei
	- ![[Pasted image 20230610185710.png]]
14. _paginazione_ la divisione in risultati in pagine
	- ![[Pasted image 20230610185731.png]]
15. _Risultati strutturati_: ogni risultato è mostrato nel modo piu coerente possibile con il tipo di risultato. es. se sto Cercando una mappa mi si presenterà un widget della mappa 
	- ![[Pasted image 20230610185745.png]]
16. _Risultati azionabili_ a seconda del tipi di risultato si puo interagire con questi, es. in video che puo essere avviato gia nella ricerca
	- ![[Pasted image 20230610185323.png]]
17. _Comparazione di Risultati_: permette al utente di comparare i diversi risultati velocemente
18. _Unified Discovery_: modalità di ricerca e di raffinazione sono unite insieme. si possono trovare più applicazioni dei precedenti pattern in un unica pagina 
	- ![[Pasted image 20230610185913.png]]
