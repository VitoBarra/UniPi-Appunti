---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Elementi di crittografica quantistica
---
la _crittografia_ ha avuto un _evoluzione_ con l avvento del [[Quantum computing|calcolo quantistico]]  una tecnologia che si basa su fenomeni di [[Meccanica quantistica|meccanica quantistica]] per funzionare.
Di fatto oggi si parla di _algoritmi crittografici post-quantici_ siccome il calcolo quantistico mette in pericolo la [[Complessita|difficoltà computazionale]] nel risolvere  dei problemi utilizzati in crittografia e considerati difficili.
un esempio lampante di questo è la [[Funzioni One-Way Trapdoor|fattorizzazione in numeri primi]] che è la base della sicurezza del [[Cifrario asimmetrico RSA|RSA]].

### Scambio quantistico di chiavi
la tecnologie di scambio quantistico chiamate _Quantum key distribution_ (QKD) sono algoritmi di scambio di chiavi che si basano su delle proprieta quantistiche. si basa sul utilizzo di  _fotoni_  che sono particelle quantistiche che non hanno massa e hanno una _polarizazione_ definita come piano di oscillazione nel suo campo elettrico. la polorizazione puo essere qualsiasi e in particolare puo essere una polorazazione verticale $\mathcal{V}$ e _orizzontale_$\mathcal{H}$ e _sovrapponendo_ i due puo ottenere la polarizazione $\pm 45°$ queste sono codifichiate in bit come 
- _bit 1_: polarizazione verticale $\mathcal{V}$ ($\uparrow$) e $+45°(\nearrow)$
- _bit 0_: polarizazione orizzontale $\mathcal{H}$($\rightarrow$)  e $-45°$($\searrow$)
gli strumenti per manipolare la polarizazione sono
- _one photon gun_ (_OPG_): permette di sparare un unico fotone
- _cella di pockets_ (_PC_): consente di imporre una polarizazione ad un fotone
- _beam splitter polarizante_ (_PBS_): che dirotta i fotoni in ingresso verso una delle due uscite $A$ e $R$ dove $A$ utilizza un fenomeno di _attraversamento_ e $R$ uno di _riflessione_. Questo strumento ha al suo interno un asso di polarizazione $\mathcal{S}$ sia $\mathcal{F}$ un fotone polarizzato e $\theta$ l angolo compreso tra $\mathcal{S}$ e $\mathcal{F}$ e si ha che il fotone viene inviato
	- al uscita $A$ con [[Probabilità e variabili aleatorie|probabilita]] $\cos^{2}(\theta)$ con polarizazione $\mathcal{S}$
	- al uscita $R$ con [[Probabilità e variabili aleatorie|probabilita]] $\sin^{2}(\theta)$ con polarizazione ortogonale ad $\mathcal{S}$
	e quindi abbiamo che con
	-  $\theta =0°$ abbiamo $\cos(\theta)=1$ sarà sicuramente $A$ ($\mathcal{F}=\mathcal{S}$ )
	- $\theta =90°$ abbiamo $\sin(\theta)=1$ sarà sicuramente $R$ ($\mathcal{F}$_ortogonale_ a $\mathcal{S}$ )
	- $\theta = \pm45°$ abbiamo $\cos(\theta)=\sin(\theta) = \frac{1}{2}$ e quindi è equiprobabile che esca da $A$ o $R$
	in ogni caso questo despisitovo cambia la polarizazione del fotone in uscita
#### protocollo BB84
il BB84 è un protocollo di _scambio di chiavi quantistico_
Indicate le basi per un _PB_ come 
- $+:\mathcal{V}, \mathcal{H}$  ovvero _contemporaneamente_ _orizontale_ e _verticale_
- $\times:\pm45°$ contemporaneamente $45°$ e $-45°$
abbiamo che il circuito che fa funzionare il BB84 è il seguente 
![[IMG_0603.jpeg]]
dove dal parte del mittente (Alice) abbiamo:
	_OPG_ spara un fotone per volta verso il _PC_ che li polarizza secondo una base decisa in modo casuale tramite un [[Generatori di numeri Pseudo Casuali|generatore di numeri casuali]] _RNG1_  
dalla parte del destinatario (Bob):
	Un deviatore di particelle _SW_ e due moduli _PBS_ uno configurato con la base $+$ e l altro con la base $\times$ e bob decide tra uno dei due moduli con un [[Generatori di numeri Pseudo Casuali|generatore casuale]] _RNG2_
I due sono anche connessione da un canale standard _[[Protocolli di Autenticazione|autenticato]]_

la tabella  delle possibili letture risulta quindi come 
![[IMG_0604.jpeg]]
dove due frecce nelle caselle indiano un comportamento _imprevedibile_.

Essendo le due basi scelte per ogni fotone completamente correlate avremmo che ad ogni scambio di fotone la probabilita che il bit inviato e quelli ricevuto siano uguali è $\frac{1}{2}$ e quindi se si invia una sequenza di fotoni saranno recepiti correttamente solo la meta degli elementi.


Dato il circuito il protocollo _segue come_:
1. _alice_ (A) invia la sequenza  $S_{A}$ a _bob_ sul canale quantistio
2. _bob_ (B) interpreta $S_{A}$ con le basi che ha scelto ottenendo una sequenza $S_{B}$ che è uguale a $S_{A}$ per meta degli elementi 
3. Usando il canale standard _bob_ comunica le basi che ha scelto ad _alice_ e _alice_ comunica a _bob_ quali basi sono comuni
4. se non ci sono state interferenze di un _crittoanalista attivo_ _alice_ e _bob_ avranno una sotto sequenza $S_{A}’=S_{B}’$  
	- ![[IMG_0605.jpeg]]
5. _alicea_ e _bob_ sacrificano una parte $S_{A}’’,S_{B}’’$  delle sequenze $S_{A}’,S_{B}’$ in posizioni prestabilite e comunicheranno le due sequenze sul _canale standard_. 
	- _se_ $S_{A}’’\not=S_{B}’’$  i due partner interrompono il protocollo siccome deve esserci stata un alterazione dovuto da una _intercettazione o malfunzionamento_. 
	- _altrimenti_ $S_{A}’-S_{A}’’=S_{B}’-S_{B}’’$  viene usata come chiave



#### Attacchi al protocollo
un possibile _crittoanalista attivo_ (_Eve_) che voglia condurre un attacco [[Tipologia di attacchi ai cifrari|man in the middle]] sul _canale quantistico_ dovrebbe leggere la sequenza di fotoni mandati da _Alice_ e rimandarli a _bob_  ma _eve_ non conosce la base usata da _Alice_ dovrà sceglierne una a coso e _completamente scorrelata_ il che per il fenomeno di _decoerenza_ e del impossibilita di _clonare_ la sequenza prima di leggerla cambierà la polarizzazione dei fotoni della sequenza, per via di ciò  _eve_ non potrà rispedire a  _bob_ la stessa sequenza  ricevuta da _Alice_
![[IMG_0607.jpeg]]
pero a questo punto _eve_ avrà circa $\frac{1}{4}$ delle basi uguali a quelle di _alice_ e _bob_ e quindi riuscita comunque a scoprire un quarto della chiave, motivo per cui si esegue i _quinto punto_ del protocollo dove si comunicano alcuni dei bit sul canale standard. Siccome le basi sono uguali anche i bit dovrebbero essere uguali e se questo non è il caso c è stata un intrusione, questo è il motivo del controllo.    



#### Controllo dei gli errori
in generale anche se non c è un _crittoanalista attivo_ sul canale possono comunque esserci delle incongruenze tra i _bit_ ricevuto anche se le basi sono le stesse.
Questo è dovuto al fatto che durante la trasmissione la polarizzazione del fotone puo variare di poco o il dispositivo preposto a leggere il fotone è fuori asse di poco, in entrambi i casi si puo _generare un errore_.

per risolvere questo problema si introduce un _quantum bit error rate_ (_QBER_)  che è una percentuale di errori che si applica sulla sequenza _sacrificata_ nel protocollo. Se i bit sbagliati sono sopra questa soglia c è stato un malfunzionamento o un intrusione altrimenti si puo procedere ma ci saranno comunque degli errori, e quindi la chiave non risulterà uguale. Per risolvere questo problema si utilizzano dei codici di correzione per generare le stringa $S_{C}$ uguale per entrambi e utilizzabile per chiave.

un attacco a questo sistema dal parte di un _crittoanalista attivo_  e quello di leggere solo una piccola parte della sequenza inviata in modo da non far superare la _QBER_ e ottenere comunque delle informazioni sulla chiave.
Questo pero è risolvibile scomponendo la chiave $S_{C}$  _in blocchi_ e applicando una funzione [[Funzioni Hash One-Way|hash critto graficamente sicure]]    a ciascun blocco. 

si ottiene cosi il protocollo _BB84_ complessivo  segue come:

_Sul canale quantistico_: $S_A[1,n]$ è la sequenza iniziale di bit da cui estrarre la chiave, rappresentata con un codice a correzione di errore. 
	_for_ $i =1$ _to_ $n$ 
		_Alice_: sceglie una base a caso, codifica $S_A[i]$, invia il relativo fotone a _Bob_; 
		_Eve (se presente)_: intercetta il fotone con una sua base, lo invia a Bob, calcola $S_E[i]$; (alternativamente può intercettare solo alcuni fotoni spediti da Alice);
		_Bob_: sceglie una base a caso, interpreta il fotone ricevuto, costruisce $S_B[i]$.


_Sul canale standard_: _QBER_  è il valore fissato come percentuale massima di bit errati dovuti a rumore; $h$ è una funzione [[Funzioni Hash One-Way|hash]] concordata e crittograficamente forte. 
	_Bob_: comunica ad Alice la sequenza di basi scelte; Alice: comunica a Bob le basi comuni; 
	_Alice e Bob_: singolarmente e comunicando tra loro:
 - estraggono le sotto sequenze $S’_A$ e $S’_B$ corrispondenti alle basi comuni, e due sotto sequenza di esse $S’’_A$ e $S’’_B$ in posizioni concordate; 
	 - si scambiano $S’’_A$ e $S’’ _B$; 
	 - _se_ la percentuale di bit in cui queste sequenze differiscono è maggiore di _QBER_ lo scambio è interrotto 
 - calcolano le sequenze $S’_A − S’’_A$ e $S’_B −S’’_B$, e le decodificano con il codice a correzione di errore ottenendo la sequenza comune $S_C$ 
 - calcolano $k = h(S_C)$; assumono $k$ come chiave.