---
type: nota
course: Interazione Uomo Macchina
topic: 
tags: IUM
---

Prev: [[Interazione Uomo Macchina (IUM)]]

# Principi di progettazione del interazione
---
si affrontano i problemi di progettazioni del interazioni 

in generale per l utente esiste solo un _buon_ design e un _cattivo_ design e una volta vita un etichetta e difficile cambiarla.

### Principi
I concetti di base della progettazione sono 

#### Discoverability 
la _Discoverability_ è la capacità di un sistema di veicolare e comunicare i propri possibili usi all'utente.
- Un sistema che a prima vista fa capire all'utente a cosa serve e che cosa ci si può fare ha una buona Discoverability 
- Per avere una buona discoverability si usa tipicamente la _visibilità_ 
- Non è detto però che una volta capito cosa si può fare si riesca a farlo.
#### Understanding
l _Understanding_ di un sistema è la capacità del prodotto di farsi usare correttamente dall'utente. 
- Se la _discoverability_ è la misura di quanto bene si capisce cosa si può fare con il prodotto, la _understanding_ invece è la proprietà associata a quanto bene un prodotto dice come si usano le funzioni disponibili.
- Per capire come si usa un prodotto non basta infatti aver identificato quali sono i controlli, è necessario dare con facilità risposta alle seguenti domande: 
	-  Come si usa il prodotto? 
	-  Che funzione ha ciascun controllo? 
	-  Come si combinano i controlli?



### Principi
è importante lavorare sul miglioramento della _discoverability_ e lo si fa basandosi sui 6 principi fondamentali del Design
#### 1. Affordances
le _affordances_ sono relazioni tra le proprietà di un prodotto o oggetto e la persona e queste determinano come l oggetto puo eventualmente essere usato
![[Pasted image 20230606001801.png]]
> [!warning]
> non sono proprieta

##### Anti-Affordance
servono a prevenire e a limitare certe azioni

#### 2. Signifiers
i _signifier_ o significanti sono degli elementi che rendono pale un _affordance_.  ovvero che segnalano che si puo fare qualcosa li. risponde spesso alla domande _dove_ fare quale azione ma non necessariamente l afforcante e dove è il significante. in generale comunica qualcosa

i significanti possono essere
_intenzionali_ e _deliberati_ 
- es. un cartello
 _accidentali_ e _non intenzionali_
- es. il numero di persone su un binario

in generale comunicano qualcosa

i significanti si basano sulle esperienza pregresse del utente. si basano su quindi su convenzioni ormai gia stabilite

#### 3. Mappings
il principio di _mapping_ e quando cerco di associare due insiemi di cose con un associazione uno ad uno
- un esempio è tra i fornelli e le manopole
- ![[Pasted image 20230606161853.png]]
un mapping di questo tipo lavora con l intuizione del utente che deve interagire con il sistema e lo aiuta a capire velocemente cosa deve fare.

il mapping si basa sulle convezioni culturali ad esempio
- ![[Pasted image 20230606162422.png]]
- in culture asiatiche troviamo il full a sinistra mentre in quelle occidentali a sinistra. Mapping diverso della stessa cosa su base culturale!
#### 4. Feedback
I _feedback_ servono al utente del interazione per capire che l azione che vuole compiere è stata affettivamente compiuta.
devono avere due proprietà
- _immediatezza_: se passano più di 100ms tra l azione e il feedback si potrebbe mal interpretare associando quel feedback ad altro
- _informativa_: il feedback deve dare un informazione altrimenti l utente potrebbe essere traviato e reagire in modo sbagliato al feedback.
se mancano una delle due proprietà il feedback più fare più danni di quanto sia effettivamente utile.

in più è importante non abusare dei feedback ne servono pochi e utili. _Less is more_

#### 5. Conceptual model of the system
il _modello concettuale_ è una _spiegazione_ estremamente semplificata di come qualcosa funziona. non deve essere completa o accurata basta che sia _utile_. 
questo è creato dal progettista e utilizzato per sviluppare l interazione

> [!example]
> un esempio è il [[File System|file system]] è un modello concettuale del sistema che c è sotto questi permette un utilizzo facile dal utente.

l utente si creare il suo _modello mentale_ che è una spiegazione di come il sistema personale e non necessariamente uguale al _modello concettuale_ su cui si basa il sistema. Più il _modello mentale_ è distante dal _modello concettuale_ più l utente più fare errori siccome non ha la giusta idea di come il sistema funziona 

in generale più è semplice un modello più è probabile che l utente del interazione riesca ad assimilarlo e a crearsi un _modello mentale_ più vicino al _modello concettuale_ questo viene al costo di dover fare un astrazione più altra e potenzialmente alla rinuncia di certe funzionalità/feature.

creare un buon _Conceptual model_ è anche trovare un buon compromesso tra semplicità e feature offerte.


il _modello mentale_ si costruisce sulla base degli altri principi del design. (Affordances, signifiers, mapping e feedback) 

il _modello concettuale_ e _modello mentale_ e il sono anche detti _design model_ e _user model_
![[Pasted image 20230606171104.png]]
non c è relazione tra i due. l unico modo che l utente ha per creare il suo _user model_ è _interagendo_ con l oggetto e con le _risorse e informazioni_ disponibili. le informazioni possono essere di qualsiasi tipo es. manuale, video su youtube, qualcuno che spiega. 

il prodotto e tutte le informazioni sono dette _System Image_
![[Pasted image 20230606171439.png]]

se la _system image_ è incoerente con il prodotto allora questo diventa difficile da utilizzare per l utente.


in più la consistenza è importante in quanto un sistema consistente riduce la confusione e da meno da imparare al utente. _la consistenza è virtuosa_
#### 6. Constraints
i vincolo sono le _costrizioni_ che ci aiutano a capire il prodotto abbattendone la curva di apprendimento. e una curva di apprendimento bassa fa sentire l utente meno stressato e meno incline al errore

questi possono essere di vari tipi e in ordine di importanza sono
1. _fisici_: ti fisicamente impediscono di fare qualcosa facendoti imparare che quella cosa non la devi/puoi fare. sono legate al _affordance_ ti dicono cosa puoi e non puoi fare
2. _culturali_: sono vincoli che dipendono solamente dalla cultura e comunemente sono convenzioni. nulla ci vieta di fare il contrario di quello che ci indica in vincolo ma _culturalmente_ non si fa
	1. ES. il senso di marcia con l auto
3. _semantici_: il significato che l utente da a certi _significanti_
4. _logici_: i limiti di buon senso

_Forcing Functions_
sono funzionalità che bloccano certe azioni. nei prodotti spesso questi sono _vincoli_ fisici mentre nel software è un qualcosa che evita il cambio di stato del applicazione.
- es. prima di poter usare le funzionalità bisogna verificare la email
_Forcing function: Interlock_
le _interlock_ permettono di guidare l esperienza utente e a seconda di come viene usato garantire che ciò che doveva essere fatto sia stato fatto. 
essenzialmente chiedo al utente di fare qualcosa prima di accedere al prossimo stato
- es. sa l email non dovesse esistere non posso garantire il servizio, verificare l email evita questo scenario.
_Forcing Functions: Lock-Ins_
i _lock-in_ mantengono un operazione attiva chiedendo al utente di fare un altra azione prima di interrompere quel attività
es.  le finestre modali ![[Pasted image 20230606232629.png]]
_Forcing Functions: Lockout_
nel _Lockout_ si richiede al utente di fare un ulteriore azione di conferma per poter iniziare un attività 
- es. ![[Pasted image 20230606233028.png]]

_Activity-Centered Controls_ 
in generale invece di pensare alle funzionalità si pensa al _attività_ utile al utente.
- es. la modalità gaming del monitor.
vengono generalmente realizzati con dei _preset_ delle configurazione che dovrebbero permettere al utente di svolgere l attività che gli interessa svolgete.
Quando questi vengono progettati male possono fare più male che bene soprattutto se questi poi diventano uno standard. al utente puo restare in mente che quel _preset_ sia inutile e non lo userà neanche dove è ben realizzato.
