---
type: nota
course: Interazione Uomo Macchina
topic: 
tags: IUM
---

Prev: [[Interazione Uomo Macchina (IUM)]]

# Human Interface Devices
---
una _human interface device_ (HID) è un tipo di periferica per il computer usato da umani.

_HID_ prende _input_ da umani e da input ad _umani_.
in generale per il termine HID si intende sia il dispositivo disico sia la _USB-HID specification_.


### USB-HID specification
con _USB-HID specification_ è uno _standard_ per i device periferici di computer. questo supporta mouse, tastiera e joystick.
è stato introdotto questa standard per permettere uno sviluppo più veloce delle periferiche.
queste prima dovevano conformarsi a dei protocolli standard rigidamente definiti e per fare qualcosa di nuovo bisognava o ridefinire cosa facessero certi input o creare dei driver specializzati. Invece con gli _HID-defined device_ possono inviare pacchetti auto descrittivi che possono contenere ogni tipo di tipi di dati e formati. questo permette un singolo driver HID su un computer di processare dati e abilita l associazione dinamica tra i dati del IO e le applicazioni delle funzioni.

nel _HID "report protocol"_  definite due entità l _host_ e il _device_
dove 
- il _device_ é la periferica input/output
- l _host_ é il computer che riceve e manda dati alla periferica

ogni device definisce i suoi pacchetti e poi presenta un "_HID descriptor_" al host. Quest ultimo é un array di byte che descrive i pacchetti dati del dispositivo includendo:
- Quanti pacchetti supporta il device.
- la dimensione dei pacchetti
- il significa di ogni byte e bit nel pacchetto.

Solitamente il _HID descriptor_ è scritto dentro una [[ROM|rom]] e non è detto che il device stesso sia in grado di processarlo, ma è un operazione deve fare l _Host_, e senza di questa l _host_ non puo comunicare al massimo  con il dispositivo. 

l _HID "boot protocol"_ è un protocollo che è nato siccome ci si è reso conto che l host non è sempre in grado di processare l _HID descriptor_. Si é creato un protocollo con pacchetti standard  atto al supporto funzionalità basilari di sole tastiere e mouse. Questo limita l innovazione infatti è usato solo dove è necessario.



### HID Device
le periferiche HID possono essere organizate in due categorie
- _Input device_: sono basati su _sensori_ e rilevano eventi e cambiamenti nel mondo fisico e li convertono in informazioni analogiche o digitali
- _Output devices_: si basano su _atuatori_ e convertono informazioni analogiche o digitali in perturbazione nel mondo fisico.

#### Input device
la _Tastiera_ è l HID device più utilizzato e solitamente rispetta lo standard di layout ISO/IEC 9995-2 ANSI e solitamente ha 3 differenti layout
1. _Layout fisico_: come i tasti sono disposti sulla tastiera 
2. _Layout visuale_: come è disposta la leggenda sui tasti (etichette, marcature, rilievi)
3. _Layout Funzionale_: come è mappato ogni tasto a quale significato nel software. Questo layout determina la risposta alla pressione di un tasto.
la tastiera alla pressione di un tasto manda un _Scancode_ al computer, questo indica solo la riga e la colonna del tasto premuto e non il significato funzionale di quel tasto, a quel punto sarà il [[Sistemi Operativi|sistema operativo]] a fare la conversione _Scancode-to-character_ utilizzando una tabella di conversione chiamata _Keyboard mapping table_. in questo modo si puo cambiare dinamicamente il layout funzionale cambiando il software che interpreta ogni tasto 



#### Barcode readers
un _barcode reader_ è un scanner ottico che puo leggere _barcode_ stampati.
consiste in una fonte di luce una lente a una sensore di luce.
questi dispositivi sono in grado di scannerizzare il bar code  e decodificarlo, mandando poi il contenuto del bar code sulla porta di output dello scanner.
![[barcode.gif]]
i _barcode_ sono un metodo per rappresentare dati in un modo visuale e machine-readable. questi sono formati standard e cambiano il valore variando la spaziature tra linee parale e l ampiezza di queste linee.
un altro modo è il QR code che non niente altro che un _barcode_ 2D
![[qr-code.png]]

#### RFID
un _RFID Reader_ manda un interrogazione elettromagnetica ai _tag RFID_ e questi risponderanno solitamente con un numero identificati
un _tag RFID_ consiste in un piccolo radio Transponder, quindi é un ricevitore e un trasmettitore .
sono di due tipi:
- _tag passivi_ prendono l energia per funzionare direttamete da RFID reader
- _tag attivo_ prendono energia da una batteria e possono essere usati a distanze maggiori.
i tag non devono essere a vista del reader quindi possono essere messi direttamente dentro l oggetto che si vuole tracciare.


#### Pointing Devices
un _dispositivi di puntamento_ è un interfaccia di input che permette al utente di dare input di tipi spaziale al computer

tipicamente i dispositivi di puntamento sono i mouse  ma non solo. oggi il termine mouse racchiude qualsiasi device che sposta il _cursore_ o _puntatore_  
ogni azione fatta al mouse viene riflessa sul desktop fisico visualizzato con una GUI


##### classificazione
per tipologia di input
- _input diretto_: il puntatore sullo schermo e alla stessa posizione fisica del _dispositivi di puntamento_
- _input indiretto_: il puntatore sullo schermo _NON_ è alla stessa posizione fisica del _dispositivi di puntamento_ ma traduce il movimento al corrispettivo movimento sullo schermo

per tipo di movimento
- _movimento Assoluto_: c é un mapping consistente (che non cambia) tra un punto nel input space e un punto nel output space 
- _movimento relativo_: mappa uno spostamento nel input space in uno nel output space. controlla la posizione relativa del cursore comparandola con la sua posizione iniziale.

per tipologia
- _isotonico_: è un oggetto movibile e misura il suo spostamento 
	- ![[Pasted image 20230615010742.png]]
- _isometrico_: è un oggetto che non si muove ma reagisce alla forza che si applica sul dispositivo
	- ![[Pasted image 20230615010753.png]]
- _elastico_:  è  un dispositivo che aumenta la forza di resistenza al aumentare della distanza dal punto iniziale
	- ![[Pasted image 20230615010800.png]]


per il tipo di controllo
- _controllo di posizione_: cambia direttamente la posizione del pointer 
- _controllo di frequenza_: cambia la direzione e la velocita di spostamento sul pointer


##### confronti
* device a _puntamento diretto_ sono più veloci ma meno preci di quelli a _puntamento indiretto_.
* persone disabili preferisco  i joystick e trackballs
	* se l applicazione di forza è un problema  si usano sistemi sensibili al tocco
* usare approcci multimodali migliora l usabilità e le performance
* usare la [[Legge di Fitts]] per ridurre i tempi  e la frustrazione

#### Eye tracking
il tracciamento degli occhi è un processo per misurare il _punto di sguardo_ (dove una persona sta guardando) o il movimento degli occhi relativo alla testa.

un dispositivo di _eye tracking_ serve a misurare la posizione e il movimento degli occhi.

Solitamente il funzionamento di questi dispositivi si basa su un _emettitore di luce_ (solitamente a infrarossi) e una _camera_ per catturare in video il riflesso generato da uno o entrambi gli occhi. Da questo video si possono estrarre dati come la rotazione del occhio basandosi vettore tra il _centro della pupilla_ e il riflesso sulla cornea.

 i metodi più conosciti sono
 _Bright-pupil_: solitamente più complessa da realizzare dal punto di vista del hardware. ma funziona meglio con tutti i vari pigmenti di occhio
 ![[Pasted image 20230615012942.png]]
 _Dark-pupil_: più facile da realizzare un po' meno accurata
 ![[Pasted image 20230615012949.png]]
La differenza tra le due viene dalla posizione della sorgente di luce.

un altro metodo meno usato è chiamato  _passive light_ e usa la luce visibile per illuminare
![[Pasted image 20230615013304.png]]


##### gaze-tracking
per fare il _traking dello sguardo_ si ha bisogno anche di sapere la posizione della testa, ci sono device per fare esattamente questo.
un altro metodo è limitare il movimento della testa e guardare solo gli occhi.


#### Data Glove
sono dei guanti con dei cavi che fanno da device di input per il pc. una volta indossati reiscono ad inviare dati come di quanto è piegato ogni singolo dito e  posizione e rotazione delle mani nello spazio. questi dati possono poi essere interpretati in informazioni utili a seconda del applicazione

#### Haptic Device
i dispositivi aptici sono dispositivi meccanici che permettono al utente di _toccare_, _sentire e manipoloare_ oggetti 3D in uno spazio virtuale 

i dispositivi aptici sono device di input-output in quanto tracciano le manipolazioni fisiche fatte dal utente (input) e danno una sensazione tattile realistica coordinata con gli eventi sullo schermo
 
#### Smart paper
sono device che vogliono digitalizzare l interazione del utente con la carta. questo avviene tramite penne intelligenti o sensori.


### Speech and auditory input interfaces
In fisica, il suono è una vibrazione che si propaga come un'onda acustica attraverso un mezzo di trasmissione come un gas, un liquido o un solido. In fisiologia e psicologia umana, il suono è la ricezione di tali onde e la loro percezione da parte del cervello.

Le onde acustiche con frequenze comprese tra circa 20 Hz e 20 kHz è detto _range di frequenza udibile_, Queste provocano una _percezione uditiva_ negli esseri umani. Nell'aria a pressione atmosferica, Le onde sonore al di sopra dei 20 kHz sono conosciute come ultrasuoni e non sono udibili dagli esseri umani. Le onde sonore al di sotto dei 20 Hz sono conosciute come infrasuoni. Diverse specie animali hanno differenti gamma di udibilità.

Il suono può essere acquisito utilizzando i _microfoni_.
Un _microfono_ è un dispositivo, un sensore, che _converte il suono in un segnale elettrico_.
I _microfoni_ sono ampiamente utilizzati come dispositivi di input.
Oggi sono utilizzati diversi tipi di microfoni, che utilizzano metodi diversi per convertire le variazioni di pressione dell'aria di un'onda sonora in un segnale elettrico.

#### Array di microfoni
Un _array di microfoni_ è costituito da un _insieme di microfoni_ che operano insieme. 
Sono utilizzati per: 
- Sistemi per estrarre l'input vocale dai rumori ambientali (in particolare telefoni, sistemi di riconoscimento vocale, apparecchi acustici) 
-  Audio surround e tecnologie correlate 
-  Registrazione binaurale 
-  Localizzazione degli oggetti tramite il suono: localizzazione delle fonti acustiche 
-  Registrazioni originali ad alta fedeltà 
-  Monitoraggio del rumore ambientale
![[Pasted image 20230616173646.png]]
Di solito, un array è composto da microfoni _omnidirezionali_, _microfoni direzionali_ o una combinazione di microfoni omnidirezionali e direzionali distribuiti lungo il perimetro di uno spazio.
Gli array possono essere formati anche utilizzando un numero di microfoni molto vicini tra loro. Date le relazioni fisiche fisse nello spazio tra i diversi elementi dell'array di trasduttori dei singoli microfoni, il processamento simultaneo _DSP_ (_digital signal processor_) dei segnali provenienti da ciascuno degli elementi dell'array di microfoni _può creare uno o più microfoni "virtuali"_.


ad esempio alexa con il suo array di microfoni puo triangolare la posizione di chi parla ![[Pasted image 20230616174321.png]]

 i problemi di questi tipi di sistemi solitamente sono: 
 - La larghezza di banda del suono è molto inferiore rispetto ai display visivi. 
 - La natura effimera del linguaggio parlato (intonazione, ecc.). 
 - Difficoltà nell'analisi e ricerca del suono → maggiore carico computazionale.
 
 mentre funzione bene per:
 Specializzazioni lessicali (come medicina o legge) 
 - Dettatura di report, appunti, lettere 
 - Esercitazione delle abilità di comunicazione (paziente virtuale) 
 - Recupero automatico/trascrizione di contenuti audio (come la radio, CC) 
 - Sicurezza/identificazione dell'utente


### [[Acquisizione modelli 3D dal mondo fisico]]



### IMU Inertial Measurement Unit
Un '_unità di misura inerziale (IMU)_ è un dispositivo elettronico che misura e riporta 
- forza specifica (l accelerazione del corpo)
-  la velocità angolare 
- e talvolta l'orientamento di un corpo
 utilizzando una combinazione di _accelerometri_, _giroscopi_ e _talvolta magnetometri_. 
l IMU ha 9 assi totali combinano  un giroscopio a 3 assi, un accelerometro a 3 assi e una bussola a 3 assi (magnetometro) nello stesso chip insieme a un processore di movimento digitale incorporato in grado di elaborare complessi algoritmi di MotionFusion.
![[Pasted image 20230616190303.png]]




### Werable Device
Un _device indossabile_ è un dispositivo informatico che viene indossato sul corpo. L'interfaccia e l'unità di elaborazione sono integrate 
I dispositivi indossabili possono essere per _uso generico_, in tal caso sono un esempio particolarmente piccolo di calcolo mobile.
Altrimenti possono essere destinati a scopi specializzati come i _tracker fitness_. Possono incorporare sensori speciali come _accelerometri_, _termometri_ e _monitor cardiaci_, 

altri _dispositivi indossabili_ sono interfacce utente innovative come Google Glass, un display ottico montato sulla testa controllato tramite gesti. 

Potrebbe essere che i dispositivi indossabili specializzati si evolvano in dispositivi _all-in-one_ generali, come è successo con la convergenza delle PDA (i palmari) e dei _telefoni cellulari_ nei dispositivi smartphone.

I dispositivi indossabili sono tipicamente indossati sul polso (come i fitness tracker), appesi al collo (come una collana), fissati al braccio o alla gamba (come gli smartphone durante l'esercizio fisico) o sulla testa (come occhiali o casco), anche se alcuni possono essere posizionati altrove (come su un dito o in una scarpa). Dispositivi portati in una tasca o in una borsa, come gli smartphone e, prima di essi, le calcolatrici tascabili e le PDA, possono o meno essere considerati "indossati". I computer indossabili presentano varie problematiche tecniche comuni ad altri dispositivi di calcolo mobile, come batterie, dissipazione del calore, architetture software, reti wireless e personal area network e gestione dei dati. 
Molti computer indossabili sono attivi tutto il tempo, ad esempio elaborando o registrando dati in modo continuo.

#### Heart Rate Wearable Monitor
Un _hart rate monitor (HRM)_ è un dispositivo di monitoraggio personale che consente di misurare e visualizzare la _frequenza cardiaca in tempo reale_ o registrare la frequenza cardiaca per uno studio successivo. 

gli _HRM_ per i consumatori sono progettati per un uso quotidiano e non utilizzano fili per la connessione e (tipicamente) non sono adatti per applicazioni mediche. 

I sensori di _fotopletismografia (PPG)_ utilizzano una tecnologia basata sulla luce per misurare il volume di sangue controllato dall'azione di pompaggio del cuore. Alcuni dispositivi che utilizzano questa tecnologia sono in grado di misurare anche la saturazione di ossigeno nel sangue (SpO2).
sono dei device per calcolare il ritmo di dilatazione dei capillari  in questi modo si puo calcolare il ritmo cardiaco 
per fare ciò ci sono due tecniche
- _luce rosa_: penetra di più nella carne e può dare risultati più accurati ma è molto suscettibile ai movimenti
- _luce verde_: un po' meno accurata ma si puo usare anche in contesti con disturbi 

I sensori di _elettrocardiografia (ECG)_ misurano il potenziale bio-generato dai segnali elettrici che controllano l'espansione e la contrazione del cuore

![[Pasted image 20230616192930.png]]

### Eletroncefalografia
_L'elettroencefalografia (EEG)_ è un metodo di monitoraggio per registrare l'attività elettrica del cervello. 
Gli _headset EEG_  posizionano elettrodi non invasivi lungo il cuoio capelluto. La definizione clinica dell'_EEG_ è la registrazione dell'attività cerebrale nel corso del tempo. Gli elettrodi EEG captano e registrano l'attività elettrica nel cervello. I segnali raccolti vengono amplificati, digitalizzati e quindi inviati a un computer o dispositivo mobile per la memorizzazione e l'elaborazione dei dati. Gli headset EEG vengono utilizzati come dispositivi di puntamento per soggetti disabili o con difficoltà motorie.
![[Pasted image 20230616204842.png]]



### NFC
_Near-field-Comunication_ (NFC) é un set di [[Protocollo|protoclli]] di comunicazione bidirezionale tra due dispositivi elettronici

_NFC_ offre una connessione a bassa velocita e solitamente si usa per fare il bootstarp di connessioni con più capacita.

non è un dispositivi di input
