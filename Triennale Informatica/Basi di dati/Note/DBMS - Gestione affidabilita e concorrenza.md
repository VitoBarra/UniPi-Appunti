---
Course: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# DBMS - Gestione affidabilita e concorrenza
---


la componenti di affidabilità e concorrenza sono due componenti del [[Architettura di un DBMS|architettura dei DBMS]]


##### Transizioni
una __transizione__ e' un unita logica di elaborazione che corrisponde a una serie di operazioni fisiche elementari (lettura/scrittura) sul [[Introduzione ai Data Base|DB]]


Una __transazione__ è una sequenza di azioni di __lettura e scrittura__ in memoria permanente e di elaborazioni di dati in memoria temporanea.

le transazioni devono garantendo le proprietà __ACID__: 
- __Atomicity__ (Atomicità):  
	- Le _transazioni_ che terminano prematuramente (aborted transactions) sono trattate dal sistema come se non fossero mai iniziate; pertanto eventuali loro effetti sulla base di dati sono annullati.
- __Consistency__ (consistenza): 
	- La transazione deve lasciare il [[Introduzione ai Data Base|DB]] in uno stato consistente, eventuali [[Modellazione della conoscenza|vincoli di integrità]] non devono essere violati.
- __Isolation__(isolamento): 
	- L’esecuzione di una transazione deve essere indipendente dalle altre.
- __Durability__ (Persistenza): 
	- Le modifiche sul [[Introduzione ai Data Base|database]] di una transazione _terminata_ normalmente sono permanenti, cioè non sono alterabili da eventuali malfunzionamenti.




Una _transazione_ può eseguire molte operazioni sui dati recuperati da un database, ma al [[Database Managment System (DBMS)|DBMS]] interessano solo quelle di lettura o scrittura  dal database 

Un dato letto o scritto può essere
- un record
- un campo di un record 
- una pagina

considerando la pagina per semplicità abbiamo che 
- Un’operazione di __lettura__ comporta la lettura di una pagina nel [[DBMS - Macchina Fisica#Gestore buffer|buffer]], se non già presente.
- Un’operazione di __scrittura__ comporta l’eventuale lettura nel [[DBMS - Macchina Fisica#Gestore buffer|buffer]] di una pagina e la sua modifica nel buffer, ma non necessariamente la sua scrittura in memoria permanente. 
	- Per questa ragione, in caso di malfunzionamento, si potrebbe perdere l’effetto dell’operazione.




##### Tipi di malfunzionamento 
Fallimenti di __transazioni__: 
	non comportano la perdita di dati in memoria temporanea né persistente (es.: [[Modellazione della conoscenza|violazione di vincoli]], violazione di protezione, [[MultiThreading - DeadLock|deadlock]]) 
Fallimenti di __sistema__:
	comportano la perdita di dati in memoria temporanea ma non di dati in memoria persistente (es.: comportamento anomalo del sistema, caduta di corrente, guasti hardware sulla memoria centrale) 
__Disastri__:
	comportano la perdita di dati in memoria persistente (es.: danneggiamento di periferica


#### Gestore del affidabilità
il __gestore dell’affidabilità__ e di eseguire le operazioni delle transazioni e la loro terminazione garantendo che la base di dati contenga solo gli effetti delle transazioni _terminate normalmente_ e sia protetta da 
- _fallimenti di transazione_
- _fallimenti di sistema_
- _disastri_

in particolare il _gestore del affidabilità_ garantisce le proprietà di Atomicità e persistenza delle transazioni

ed e' responsabile di 
- Implementare i comandi di: _begin_ _transaction_, _commit_, _rollback_ 
- Responsabile di ripristinare il sistema dopo __malfunzionamenti software__ (ripresa a caldo) 
- Responsabile di ripristinare il sistema dopo __malfunzionamenti hardware__ (ripresa a freddo)

##### Notazione
Convenzioni notazionali: • data una transazione T, indicheremo con B(T), C(T) e A(T) i record di begin, commit e abort relativi a T, rispettivamente, e con U(T, O, BS, AS), I(T, O, AS) e D(T, O, BS) i record di update, insert e delete, rispettivamente su un oggetto O, dove BS è before state and AS è after state. • I record del log associati ad una transazione, consentono di disfare e rifare le corrispondenti azioni sulla base di dati: • primitive di undo: per disfare un’azione su un oggetto O, è sufficiente ricopiare in O il valore BS (l’insert viene disfatto cancellando l’oggetto O) • primitiva di redo: per rifare un’azione su un oggetto O, è sufficiente ricopiare in O il valore AS (il delete viene rifatto cancellando l’oggetto O)



##### Operazione Di Dump
L’operazione di dump produce una copia completa della base di dati, effettuata in mutua esclusione con tutte le altre transazioni quando il sistema non è operativo. • La copia viene memorizzata in memoria stabile (backup). • Al termine del dump, viene scritto nel log un record di dump, che segnala l’avvenuta esecuzione dell’operazione in un dato istante. Il sistema riprende, quindi, il suo funzionamento normale

##### File di log
Il _file di log_\_giornale_ e' la struttura usata per la gestione del affidabilità e che serve ad implementare tutti gli algoritmi necessari.

e' un file sequenziale suddiviso in __record__
![[Pasted image 20240111233139.png]]
divisi in 
- Record di transazione (Blu):
	- Tengono traccia delle operazioni svolte da ciascuna transizione sul DBMS. 
- Record di sistema (grigi):
	- tengono traccia delle operazioni di sistema (__dump/checkpoint__).


Contenuto dei record di transazione nel giornale giornale/log sono del tipo: 
- $(T, begin)$: __solo uno__ per ogni transazione distinta
- Per ogni operazione di insert (I), delete (D) e update (U): 
	- la transazione responsabile
	- il tipo di ogni operazione eseguita
	- vecchia versione del dato modificato
	- nuova versione del dato modificato
-  $(T, commit)$ o $(T, abort)$: __solo uno__ per ogni transazione distinta

Questo e un archivio gestito in maniera sicura (cioè mantenuto in due copie su dispositivi con fallimento indipendente)

il __log__ viene aggiornato durante l’uso della BD registrando la storia delle azioni effettuate su DB dal momento in cui ne è stata fatta l’ultimo __Dump__ (dal ultimo backup)

Un malfunzionamento può capitare tra il momento in cui un’operazione viene eseguita ed il momento in cui tale operazione viene registrata nel __file di log__, perciò bisogna registrare le operazioni nel __file di log__ prima che esse vengano eseguite effettivamente, si seguono le regole:
   1. __Write ahead log__: la parte __BS__ (before state) di ogni record di __log__ deve essere scritta prima che la corrispondente operazione venga effettuata nella [[Introduzione ai Data Base|base di dati]] in modo che il vecchio valore si recuperabile in caso di malfunzionamento. (Regola per disfare)
   2.  __Commit Rule__: la parte __AS__ (after state) di ogni record di log deve essere scritta nel log prima di effettuare il commit della transazione in modo da poter rieseguire la transazione in caso di fallimento di sistema o di disastro (Regola per rifare)
	   - questo perché non subito i dati vengono salvati in modo permanente, ma restano per un po' ne buffer

> [!example]-
> Esempi corretti:
>![[Pasted image 20240112000920.png]]
>![[Pasted image 20240112001156.png]]
>Esemi sbagliati
>![[Pasted image 20240112001317.png]]

##### Algoritmi per la gestione del affidabilita
per gli [[Algoritmi|algoritmi]] per la gestione del affidabilità si assume che le scritture sulla memoria permanente del __Log__ vengano fatte subito

questi algoritmi si differenziano a seconda del modo in cui si trattano le __scritture sulla BD__ e la __terminazione delle transazioni__ e sono di 4 categorie
- Disfare - Rifare
- Disfare - NonRifare
- NonDisfare - Rifare
- NonDisfare - NonRifare

###### __Disfare-Rifare__ 
Allora si ha che:
- __modifica Libera__ : un dato puo essere scritto sul DB in memoria permanente prima che la transazione termini, in caso di abort della transizione si riscrivono i vecchi valori leggendoli dal __log__
	- Necessita della regola "__Write Ahead Log__" (regola per disfare) 
- __commit libero__: Una transazione $T$ e' considerata terminata normalmente, e viene scritto nel __file Di log__  il record $(T, commit)$, senza che le sue modifiche vengano riportate nella base di dati. Nel caso di fallimento di sistema occorre rifare  le modifiche fatte dalle transazioni terminate normalmente prendendo i nuovi dati dal __log__ perché non si e' certi che i loro effetti siano stati riportati sulla [[Introduzione ai Data Base|base di dati]] questo siccome e' il [[DBMS - Macchina Fisica#Gestore buffer|gestore del buffer]] a gestire quando verranno scritte le modifiche sul DB in memoria premente e al momento del malfunzionamento potrebbero esserci delle modifiche ancora non salvate
	- Necessita della regola "__Commit Rule__" (regola per rifare) 

 
per recuperare i dati va scandito tutto il file di __log__ ma sono solo le ultime operazioni che  probabilmente sono state perdute e quindi per evitare di scansionare parti inutili del log si utilizza l operazione di __CheckPoint__ che scrive la marca CKP sul giornale/log per indicare che tutte le operazioni che la precedono sono state effettivamente riportate sulla BD in memoria permanete. in questo modo si puo ripartire dalla marca CKP invece che scansionare tutto il __log__

l operazione di __CheckPoint__ e' fatta come segue:
1. Si scrive sul giornale una marca di __inizio checkpoint__ che riporta l’elenco delle transazioni attive $(BeginCkp, \{T_1,\dots,T_n\})$ 
2. In parallelo alle normali operazioni delle transazioni, il [[DBMS - Macchina Fisica#Gestore buffer|gestore del buffer]] riporta sul disco tutte le pagine modificate 
3. Si scrive sul giornale una marca di EndCkp 
La marca di __EndCkp__ certifica che tutte le scritture avvenute prima del __BeginCkp__ ora sono sul disco mentre non ce' certezza dello stato delle scritture avvenute tra __BeginCkp__ e __EndCkp__ 





Avendo a disposizione il __file di log__, ed una vecchia copia del [[Introduzione ai Data Base|database]] (Dump), la procedura di ripristino in caso di malfunzionamento é la seguente:
- __Fallimento di transazione__: si _disfano_ gli effetti di tutte le operazioni della transazione, utilizzando le informazioni sul giornale, ed infine si memorizza un _record di transizione_ $(T,abort)$ sul __log__
- __Fallimento di sistema__ (ripresa a caldo): si esegue il comando __restart__ che ripartendo da un __checkpoint__ (detto anche punto di allineamento)
	- le transazioni attive al momento del fallimento vanno __disfatte__ 
	- le transazioni terminate normalmente al momento del fallimento vanno __rifatte__
- __Disastro__ (ripresa a freddo): si ricarica un backup (dump) del database e si rifanno tutte le operazioni delle transizioni terminate normalmente registrate sul __log__
	- Se il backup e' stato fatto in un momento di attività del sistema,  e' anche necessario disfare gli effetti di tutte le transazioni che erano in corso al momento della copia e che non avevano ancora effettuato il commit al momento del malfunzionamento. 

la __ripresa a caldo__ dopo un __fallimento di sistema__ viene eseguiti con i seguenti passi:
1.  Trova l'ultimo checkpoint (ripercorrendo il log a ritroso) 
2.  Costruire gli insiemi
	1.  UNDO (transazioni da disfare) 
	2.  REDO (transazioni da rifare) 
3. Ripercorrere il log all'indietro, fino alla __più vecchia__ azione delle transazioni in UNDO, disfacendo tutte le azioni incontrate delle transazione in UNDO
4.  Ripercorrere il log in avanti, rifacendo tutte le azioni delle transazioni in REDO

la __ripresa a freddo__ dopo un __Disastro__ viene eseguiti con i seguenti passi:
1. Si ripristinano i dati a partire dal backup 
2. Si eseguono le operazioni registrate sul giornale fino all'istante del guasto 
3. Si esegue una ripresa a caldo



le operazioni di “disfacimento” e “rifacimento” devono essere “idempotenti”, ovvero si deve ottenere l’effetto voluto sia che
- si stia disfacendo un’operazione realmente effettuata
- sia che si stia disfacendo un’operazione gia disfatta.
questo e' importante per due motivi
- per via della regola "__Write Ahead log__"  (disfare) abbiamo che il vecchio valore di un record modificato non vada mai perduto ma se un malfunzionamento avviene poco dopo la scrittura del record nel __log__, non e' possibile sapere se l’operazione fosse stata effettuata anche sui dati permanenti. 
- un malfunzionamento può avere luogo anche durante il ripristino


###### __Disafre-NonRifare__
Operazioni direttamente in memoria permanente 
- si cancella solo le parti della transizione fallite


###### __NonDisfare-Rifare__
Operazioni in memoria temporanea fino al commit
- se ci sono disastri non c ‘ e nulla da Disfare perchè non viene salvato in memoria


###### NonDisfare-NonRifare
Swapping di ShadowPages (Da approfondire)

#### Gestore della concorrenza 
Il __gestore della concorrenza__ garantisce la proprietà di __isolamento__ delle transizione
La proprietà di isolamento di una transazione garantisce che essa sia eseguita come se non ci fosse concorrenza 
Questa proprietà è assicurata facendo in modo che ciascun insieme di transazioni concorrenti sottoposte al sistema sia “__serializzabile__”




• Definizione 
Un’esecuzione di un insieme di transazioni $\{T1 , \dots, Tn \}$ si dice __seriale__ se, per ogni coppia di transazioni $T_i$ e $T_j$ , tutte le operazioni di $T_i$ vengono eseguite prima di qualsiasi operazione $T_j$ o viceversa. 

• Definizione 
Un’esecuzione di un insieme di transazioni si dice __serializzabile__ se produce lo stesso effetto sulla base di dati di quello ottenibile eseguendo serialmente, in un qualche ordine, le sole transazioni terminate normalmente.

Uno schedule S si dice seriale se le azioni di ciascuna transazione appaiono in sequenza, senza essere inframezzate da azioni di altre transazioni.$$ S=\{T_1, T_2, \dots ,T_n\}$$ 
Schedule seriale ottenibile se: 
1.  Le transazioni sono eseguite uno alla volta (scenario non realistico) 
2. Le transazioni sono completamente indipendenti l’una dall’altra (improbabile)

i [[Database Managment System (DBMS)|DBMS]] implementano tecniche di controllo di concorrenza che garantiscono direttamente la __serializzabilità__ delle transazioni concorrenti. 
Tali tecniche si dividono in due classi principali:
- __Protocolli pessimistici/conservativi__: tendono a «ritardare» l’esecuzione di transazioni che potrebbero generare conflitti, e quindi anomalie, rispetto alla transazione corrente. Cercano quindi di prevenire. 
- __Protocolli ottimistici__, che permettono l’esecuzione sovrapposta e non sincronizzata di transazioni ed effettuano un controllo sui possibili conflitti generati solo a valle del commit.



##### Protocolli Ottimistiche
nelle __tecniche Ottimistiche__ le transazioni effettuate le proprie operazioni sugli oggetti della base di dati secondo l’ordine temporale con cui le operazioni stesse sono generate, Al commit, viene effettuato un controllo per stabilire se sono stati riscontrarti eventuali conflitti, e nel caso, viene effettuato il rollback delle azioni delle transazioni e la relativa riesecuzione. 
In generale, un protocollo di controllo di concorrenza ottimistico è basato su 3 fasi: 
1. __Lettura__: ogni transazione legge i valori degli oggetti della BD su cui deve operare e li memorizza in variabili (copie) locali dove sono effettuati eventuali aggiornamenti 
2.  __Validazione__: vengono effettuati dei controlli sulla serializzabilità nel caso che gli aggiornamenti locali delle transazioni dovessero essere propagati sulla base di dati 
3. __Scrittura__: gli aggiornamenti delle transazioni che hanno superato la fase di validazione sono propagati definitivamente sugli oggetti della BD.

##### Protocolli pessimistiche
nei __Protocolli pessimistici__ si dividono in due categorie
- Basati su [[Sincronizzazione MultiThreading - Lock|lock]]
- Basati su Timestamp



###### le metodologie basate su lock
Il [[Sincronizzazione MultiThreading - Lock|lock]] è un meccanismo che blocca l'accesso ai dati ai quali una transazione accede ad altre transazioni 
il lock e' multi granulare ovvero funziona a 
- livello di riga
- livello di tabella
- livelo di pagina   
il lock viene fatto in modalita multimodale a seconda del operazione 
- scrittura in __mutua esclusione__ 
- lettura __accesso condiviso__
quando una risorsa è bloccata, le transazioni che ne richiedono l'accesso vengono in genere messe in coda, devono aspettare che il lock sia rimosso

 Questo è un meccanismo efficace, ma influisce sulle prestazioni


Il gestore della concorrenza (serializzatore) dei DBMS ha il compito di stabilire l’ordine secondo il quale vanno eseguite le singole operazioni per rendere serializzabile l’esecuzione di un insieme di transazioni. 


Il protocollo del __[[Prevenzione Deadlock - Consecutive Two phase locking|lock a due fasi]] stretto__ (Strict Two Phase Locking, S2PL) è definito dalle seguenti regole: 
1. Ogni transazione, prima di effettuare un’operazione acquisisce il blocco corrispondente (chiede il lock) 
2.  Transazioni diverse non ottengono blocchi in conflitto, ovvero non si prende un lock gia preso 
3. I blocchi/lock si rilasciano dopo la terminazione della transazione (cioè al commit)

 posso capitare situazioni di attesa “circolare”, ovvero di [[MultiThreading - DeadLock|deadlock]]. Per sbloccare questo tipo di situazioni si usano le tecniche di [[Prevenzione DeadLock - individuare e recuperare da un DeadLock|individuazione e recupero]]
1. _Rilevazione per time-out_: ogni volta che un’attesa si prolunga oltre un certo limite, la transazione in attesa viene abortita, presupponendo l’esistenza di uno stallo. 
2. _Rilevazione tramite [[Struttura dati - Grafi|grafo]] delle attese_: si costruisce un grafo avente come nodi le transazioni, aggiungendo un arco da T1 a T2 ogni volta che T1 va in attesa del rilascio di un [[Sincronizzazione MultiThreading - Lock|lock]] da parte di T2. Ogni volta che si crea un ciclo nel grafo, una delle transazioni coinvolta viene fatta abortire (tipicamente la piu giovane, quella che ha meno risorse o quella il cui aborto ha il minor costo).
o con tecniche di [[Prevenzione Deadlock|Deadlock avoidance]] 
1. si prendono tutti i lock al inizio e li si rilascia tutti alla fine (consecutive 2 phase loking, C2FL)
 
Ia tecnica del [[Prevenzione Deadlock - Consecutive Two phase locking|lock a due fasi]] garantisce la serializzabilità, ma _limita_ la concorrenza possibile tra diverse _transazioni_. 
 Ad esempio, un’applicazione lunga che legge una grande quantità di dati potrebbe non riuscire mai ad acquisire tutti i lock necessari, oppure, quando li avesse acquisiti tutti, potrebbe impedire ad ogni altra transazione che voglia effettuare modifiche di partire. Per questo motivo, molti sistemi permettono al programmatore di limitare la quantità di lock richiesti dalle applicazioni, anche se questo comporta la perdita della serializzabilità

###### Metodologie basate su Timespamp
Un metodo alternativo al 2PL per la gestione della concorrenza in un DBMS prevede l’utilizzo dei time-stamp delle transazioni (metodo TS). 
- Ad ogni transazione si associa un timestamp che rappresenta il momento di inizio della transazione. 
- Ogni transazione non può leggere o scrivere un dato scritto da una transazione con timestamp maggiore. 
- Ogni transazione non può scrivere su un dato già letto da una transazione con timestamp maggiore.