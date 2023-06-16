---
type: nota
course: Interazione Uomo Macchina
topic: 
tags: IUM
---

Prev: [[Interazione Uomo Macchina (IUM)]]

# Errori Umani
---
in generale non ha senso cercare la colpevolezza di una persona per risolvere un problema creatosi. Gli errori umani solitamente avvengono per _colpa_ non per _dolo_ ovvero avvengono come incidenti non per volontà del individui. quindi se c è un problema questo non è causato dalla persona ma dal _processo_, e il _processo_ si puo cambiare da un _designer_ e quindi sarà li che si puo lavorare.

## Root Cause Analysis
 il _Root Cause Analysis_ è un metodo per arrivare a capire quale è la causa del problema. Con questo metodo riusciamo ad ignorare i _sintomi_ e risolvere il _vero problema_, nonostante questo possono esserci delle concause.
#### I 5 why (perché)
la tecnica più utilizzata per fare questo è la regola dei _5 perché_. Essenzialmente ci si continua a chiedere il perché del problema che si è presentato finche non arriviamo a qualcosa di _significativo_ su cui _si puo agire_, facendo cosi si individua la parte del processo che porta a generare il _problema_
un esempio è
![[Pasted image 20230608185749.png]]
in generale i "5 perché" è una linea guida i perché possono essere un numero qualsiasi basta che sia utile a trovare la causa dei problemi.
##### perché usare questo metodo
![[Pasted image 20230608185922.png]]


## Definizione di errore umano
l errore umano è definito come qualsiasi devianza dal comportamento "_appropriato_". dove per appropriano dipende dal contesto e non é detto sia conosciuto.

questi sono categorizati in due modi
- _Slip_(_lapsus_): questo tipo di è errore si verifica quando l azione intera era una ma l azione poi svolta diventa un altra ottenendo ovviamente risultati diversi dagli attesi. questi sono di due tipi
	- _Action-Base_: faccio l azione sbagliata
	- _memory lapses_: mi dimentico di fare qualcosa
- _Mistakes_(_errori cognitivi_): questo tipo di è errore si quando il _piano o il goal_ sono sbagliati, l azione che si preforma è corretta ma il risultato è diverso dal voluto perché era sbagliato in principio il piano o l obiettivo stesso. si dividono in 
	- _Rule-Based_: la persona ha bene in mente il sistema con cui sta lavorando (ha un buon [[Principi di progettazione del interazione|modello mentale]]) ma compie un errore applicando una _sequenza di azione_ sbagliata.
	- _Knowledge-based_: la persona compie l errore siccome non conosce bene il sistema o le informazioni sono incomplete
	- _Momory-lapse_: la persona compie un errore dimenticandosi uno o più passaggi della procedura che vuole eseguire
![[Pasted image 20230608190652.png]]

questi diversi tipi di errori vengono fatti nelle diverse fasi delle [[Le azioni degli utenti|azioni del utente]]
![[Pasted image 20230608192654.png]]
> [!warning] 
> i _memory lapses_ non sono di due tipi ma diventano slips o mistakes a seconda di dove li compio nelle fasi

in generale abbiamo che 
- i novizi tendono a fare più errori cognitivi (_Mistake_) rispetto Ai _labsus_(_slips_)
- gli esperti fanno più _labsus_(_slips_) che errori cognitivi (_Mistake_) 

### Cosa produce gli errori
gli __errori cognitivi__ sono solitamente generati da informazioni _non chiare o ambigue_ date al utente riguardo lo stato del sistema o nella comunicazione del [[Principi di progettazione del interazione|modello concettuale]]. 
un esempio di informazioni erronee puo essere dato da _feedback_ di bassa qualità 

_feedback_ eccessivi possono dare fastidio al utente che probabilmente arriverà a disattivarli se ne ha la possibilità. Con questi disattivi l utente non noterà neanche i _feadback_ che invece sarebbero stati utili commettendo cosi degli errori 


un altra fonte di __errori__ sono le _Interruzione_. queste ci fanno fare _context switch_ il che è molto costoso dal punto di vista energetico siccome finita la gestione del interruzione il costo di ripresa di quel azione è molto alto. Ci si deve ricordare dello stato del sistema, del obiettivo e dove eravamo nel ciclo di azione il che è costoso



## Error prevention
gli errori in generale non si possono evitare del tutto ma si puo provare a ridurli in numero e gestire i casi in cui succede.
- _capendo_ la causa del errore si puo agire lato design per fare in modo che sia meno facile che l errore avvenga
- _facendo sensibility check_ ovvero controllando che le azioni rispettino il _buon senso_ in modo da mostrare messaggi di errore o conferma solo quando necessario
- _dare la possibilità di annullare un azione_ cosi se c è un errore e l utente se ne accorge puo facilmente risolvere il problema da solo creandogli meno frustrazione rispetto al dover fare tutto da zero
- fare in modo che l utente _si accorga_ del errore, con segnalazioni o evidenziazioni
	- es box rosso se la password non rispetta le regole e regole scritte affianco.
- _non trattare le azioni come errori_ alcuni "errori" a seconda di come sono gestiti possono diventare occasioni aiutandoli a compere comunque l azione che volevano compiere.
	- es carrello di amazon senza aver fatto il login, o lista degli acquista dopo
- _aggiungere vincoli_ che aiutano l utente a non sbagliare


messaggi di conferma e messaggi di errori sono estremamente _NON_ efficaci nel evitare gli errori infatti questi dovrebbero essere evitati. 
ha senso metterli solo in casi particolari piazzati in modo intelligente ad esempio se l utente sta facendo un azione che di norma non fa in modo che compaia poche volte e sia utile.
- es. la media di bonifici fatti dal utente è 50 e sta inviando 5000 euro di bonifico


per mitigare gli errori di tipi _slips_ cerca di fare in modo che sia difficile sbagliare per l utente mettendo a procedure per azioni diverse interface diverse in modo che si possa rendere conto di star facendo l azione sbagliata