---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Moneta elettronica Bit Coin
---
le _monete elettroniche_ o _criptovalute_ sono della valute Completamente decentralizzate ovvero non hanno bisogno di intermediari come banche centrali enti finanziari. Infatti sono nati proprio sul principio di evitare questi tipi di controlli o n'esita di terzi.

Le monete si basano su sistemi [[Peer-to-Peer|Peer-to-Peer]] e su [[Block chain|block chain]], ogni transazione tra utente viene controllata e eventualmente ricontrollata da solo gli utenti della reta.


le transazioni operata vengono conservate in _blocchi_ e concatenati poi nella [[Block chain|Block chain]] questa farà da _libro contabile_ per tutte le transizioni avvenute.



lo _schema generale_ per eseguire una transazione si eseguono i seguenti passi.
1. le nuove transazioni sono trasmesse sulla rete via _broadcast_
2. ogni nodo del sistema raccoglie le nuove transizioni in un _blocco_
3. Ogni nodo cerca di individuare una dimostrazione di correttezza per il suo blocco. Questo volutamente implica la soluzione di un “_[[Complessita|problema difficile]]_”. 
4. Quando un nodo trova una dimostrazione di correttezza la diffonde per broadcast a tutti i nodi per inserire il blocco nel [[Block chain|block-chain]]. Un premio in bitcoin viene accreditato al nodo autore della dimostrazione. 
5. I nodi accettano il blocco solo se le transazioni in esso contente sono valide e non sono apparse in blocchi precedenti. 
6. I nodi esprimono la loro accettazione del blocco iniziando a creare un nuovo blocco da inserire nel block-chain

#### Identificati sulla rete
l utente sulla rete sarà identificato solo da un _wallet_ (portafoglio) questo attesta la proprietà in _bit coin_ di un utente.
Ogni _wallet_ ha associato una coppia di chiave pubblica e privata di un [[Cifrari a chiave Asimmetrica|cifrario asimmetrico]] su [[Curve Ellittiche|curve Ellittiche]]  e un _indirizzo_, questo indirizzo sarà il vero identificatore del _wallet_ questo non conterrà _nessun informazione personale del utente_ per garantire un alto livello di privacy

> [!note]- curva scelta
> le chiavi sono generate su una curva specifica curva  chiamata _secp256k1_

l _indirizzo_ è calcolato a partire dalla _chiave pubblica_ su cui viene fatto l [[Funzioni Hash One-Way|SHA256]] Piu volete e poi compresso via [[Algoritmo di compressione RIPEMD-160|RIPEMD-160]] in una stringa a 160 bit. Alla stringa appena generata si aggiunge in testa una _speciale sequenza_ che indica che effettivamente la stringa complessiva è un indirizzo _bitcoin_


#### Transizioni
Una _transizione_ nel sistema _bit coin_ è espressa come "$A$ vuole inviare $X$ _bit coin_ a $B$ "  dove $A$ e $B$ sono identificati con l indirizzo del _wallet_ $adr_{A}$ e $adr_{B}$, ogni transazione segue il _seguente protocollo_:
_messaggio_: 
	L utente $A$ genera un messaggio $m=adr_{A}-X-adr_{B}$
_firma_: 
	L utente $A$ calcola l [[Funzioni Hash One-Way|hash]] $h = SHA256(m)$ e genera la [[Protocolli di firma digitale|firma digitale]] $f=\mathcal{D}(h,k_{A}[prv])$ 
_Broadcast_:
	la coppia $\langle m,f \rangle$ vene diffuso sulla rete.

una volta eseguita una _transazione_ questa non è istantaneamente verificata, di conseguenza un utente disonesto potrebbe provare a spendere Piu bit coin di quanti ne possiede inviando _Spese_ multiple in tempi brevi e spendendo piu volte gli stessi bit coin. (Problema chiamato dal inventore di bitcoin _double Spending_).
Questo può si presenta non essendoci un ente preposto a fare la verifica delle transazioni. L utente $B$ prima di accettare la transazione dovrà aspettare che questa venga _[[#Verifica della transazione|verificata  dalla rete]]_, questa è studiata per riuscire a fare una verifica ogni 10 minuti il che rende difficile l utilizzo di bit coin in luoghi fisici.


>[!warning] chiave privata
>Per via di questo protocollo la _chiave privata_  è l unico _documento valido_ che possa attentare la proprietà di _BitCoin_. Se questa dovesse essere persa non si potrebbero Piu spendere i _bit coin_ posseduti e se questa dovesse essere invece rubata e usata per spendere i bit coin, non ci sarebbe modo per cancellare quelle transazioni. questo siccome la [[Protocolli di firma digitale|firma digitale]] non è _ripudiabile_.



#### Verifica della transazione
La _verifica delle transazioni_ da parte della rete viene dalla _proof of work_ ovvero per verificare un blocco di transazioni c è bisogno di completare un _[[Complessita| compito  computazionalmente difficile]]_ ma verificabile in modo _[[Complessita|computazionalmente facile]]_.

ogni blocco di transazioni verificate viene aggiunta alla [[Block chain|Block chain]] che fa da _libro contabile_ ed è usata per verificare tutte le transazioni.

il contenuto di ogni blocco $B_i$ è il seguente 
- numero che rende vera certe proprietà chiamato _nonce_
- l _hash_ del blocco precedente
- Le _transizioni da verificare_
 

il Processo di validazione è detto _mining_ e consiste nel eseguire la funzione [[Funzioni Hash One-Way|Sha256]] sulle transizioni sul _nonce_ $n_{i}$ e sul _Hash del blocco precedente_ $h_{i-1}$ e bisogna trovare un _nonce_ $n_{i}$ tale che il codice _hash_ $h_{i}$ generato inizi con $t$ zeri.
Dove $t$ è un parametro del sistema _bit coin_ e questo cambia in basa alla potenza di calcolo presente sul sistema in modo da fare in modo che venga validato un blocco ogni 10 minuti.
siccome la potenza di calcolo tende ad aumentare sempre di Piu anche cosi fa $t$

Essendo [[Funzioni Hash One-Way|Sha256]] una _funzione crittograficamente_ forte non c è modo di predire velocemente quale numero $n_{i}$ genererà un codice con le proprietà volute e quindi l unico modo per calcolare questo valore è il metodo enumerativo, si devono quindi provare tutte le combinazioni. Mediamente per trovare il _nonce_ giusto ci vogliono $2^{t}$ operazioni

![[Pasted image 20230819182515.png]]

Durante la validazione di un blocco tutta la catena di blocchi precedenti è _validata e immutabile_

Una volta _validato_ un blocco questo viene mandato in broadcast a tutti gli utenti sulla rate che verificheranno _con un operazione facile_ che l Hash generato sia corretto e verrà aggiunto alla copia locale della blockchain.

in caso di _validazione_ contemporanea di piu blocchi si sceglie quelle con piu transazioni, o che ha la catena piu lunga


L operazioni di verifica di un blocco può essere fatta da qualsiasi utente ma nella pratia sono i nodi con più capacita computazionale che effettivamente faranno la verifica mentre gli altri si limiteranno ad accertarsi che questa sia corretta.
	oggi per risolvere il problema della verifica si usano gli ASIC (_application specific integrated circuits_) questo permette di risolvere il problema in modo più efficiente e veloce


L incentivo per ogni utente di validare un blocco è nel guadagnare bitcoin ad ogni blocco _validato_, questo aggiunge bit coin al sistema con una formula che dimezza il gain di bit coin ogni 4 anni fino a raggiungere lo zero nel 2140



#### Sicurezza
la sicurezza del _BitCoin_ è data dal _consenso di nakamoto_ (l inventore di bitcoin)
Questo si basa su una certa probabilita di selezionare un nodo $N$ onesto che abbia fatto la verifica, la probabilità di selezionare un nodo è proporzionale alla sua capacita di calcolo perche ha Piu probabilita di trovare prima degli altri un _nonce_ $n_{i}$ che soddisfa le proprietà per la verifica.
Se la maggior parte della capacita di calcolo appartiene a nodi onesti allora la _Block-chain_ conterrà solo transazioni oneste.

Poniamo che un un utente disonesto voglia cambiare un blocco precedete, per fare ciò dovrebbe avere la capacita di calcolo anche tutti i blocchi successive siccome questi dipendono da i precedenti. lavoro troppo grande.

#### Problematiche del bit coin
fare la proof of work è un lavoro inteso e consuma molta energia.
bisogna accertarsi del _identificati_ del utente a cui si vogliono mandare dei bit coin. non essendoci enti come la [[Certification Authority|Certification Authority]] per tutelare la privacy degli utenti bisogna fare attenzione su come ci si scambiano gli identificativi. Essenzialmente ci sono i problemi che si presentano con le _chiavi pubbliche_ senza certificati


