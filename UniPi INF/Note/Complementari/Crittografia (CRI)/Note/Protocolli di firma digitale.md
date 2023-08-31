---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Protocolli di firma digitale
---
la _firma Digita_ vuole mimare le importanti proprietà della _firma manuale_ che sono
1. La firma è _autentica e non è falsificabile_, dunque costituisce prova che chi l’ha prodotta è veramente colui che ha sottoscritto il documento. 
2.  La firma _non è riutilizzabile_, e quindi risulta _legata strettamente al documento_ su cui è stata apposta. 
3.  Il documento _firmato non è alterabile_, e quindi chi ha prodotto la firma è sicuro che questa si riferirà solo al documento sottoscritto nella sua forma originale. 
4.  La firma _non può essere ripudiata_ da chi l’ha apposta, e costituisce dunque prova legale di un accordo o di una dichiarazione contenuta nel documento.


## Protocolli di firma digitale
in generale i protocolli di firma digitale possono essere realizzati sia con [[Cifrari a chiave Simmetrica|cifrari simmetrici]] che [[Cifrari a chiave Asimmetrica|assimetrici]]
ma quelli simmetrici sono tendenzialmente piu complicati e computazionalmente costosi quindi non adatti a gestire al numero di messaggi che si scambiano oggi su internet.

### Firma digitale Diffie-Hellman
un protocollo che si basa si [[Cifrari a chiave Asimmetrica|cifrari assimetrici]]  dove la chiave privata è usata per _produrre la firma_ e quella pubblica _per verificala_.

#### Protocollo 1
_Sia_ 
- $m$ il messaggio
-  $U$ un generico utente 
-  $k_{U}[pub]$ e $k_{U}[prv]$ l chiavi publiche e private di $U$
-  $\mathcal{C}$ e $\mathcal{D}$ le funzioni di [[Cifratura e Decifratura|cifratura e decifratura]]  e del _cifrario usato_ il protocollo segue:
	_Firma_: L utente $U$ genera la firma $$f=\mathcal{D}(m,k_{U}[prv])$$ e il messaggio _firmato_ puo essere spedito ad un qualsiasi altro utente $V$ come $\langle U,m,f\rangle$
	_Verifica_: L utente $V$ riceve la tripla $\langle U,m,f\rangle$ e la _verifica_ calcolando $$m'=\mathcal{C}(f,K_{U}[pub])$$ e controlla che $m'=m$ se è questo il caso la firma è _verificata_.
In questo caso le funzioni di _cifratura e decifratura_ vengono usate in modo in verso ma questo non è un problema se il cifrario scelto è un cifrario _commutativo_ e vale 
$$\mathcal{C}(\mathcal{D}(m))=\mathcal{D}(\mathcal{C}(m)) =m$$

questo protocollo ha le seguenti proprietà:
-  La _firma_ $f$ è  autentica e non falsificabile (requisito 1), poiché la chiave $k_U [prv]$ utilizzata per produrla è nota solo a $U$ e la funzione $\mathcal{D}$ è [[Funzioni One-Way Trapdoor|one-way trapodoor]]. 
- Il documento firmato $\langle U, m, f\rangle$ _non pùo essere alterato_, altrimenti si perderebbe la consistenza tra $m$ e $f$; quindi $U$ può tranquillamente rilasciarlo ad altri (requisito 3). Ma poiché solo $U$ può aver prodotto $f$, egli non può a sua volta _ripudiare_ tale firma (requisito 4). 
-  La firma $f$ non è riutilizzabile su un altro documento $m' \not = m$ (requisito 2) poiché $f$ è immagine di $m$, cambiando $m$ cambia $f$


Questo protocollo non specifica mai un particolare destinatario $V$ e quindi la verifica puo essere fatta da chiunque anche da un terzo.
##### Svantaggi
Questo protocollo pero non ha applicazione pratica siccome per inviare un solo messaggio ora bisogna mandare anche $f$ che è di lunghezza paragonabile al messaggio stesso, Molto costoso poco pratico.
in più il messaggio _non è nascosto_ si può ottenere direttamente da $f$.


#### Protocollo 2
in questo protocollo la _firma_  si incapsula direttamente nel messaggio $m$ evitando di dover mandare il doppio dei dati e in piu il messaggio stavolta è _cifrato_
_siano_ $U$ e $V$ due utenti e $m$ il messaggio che $U$ vuole mandare a $V$ il _protocollo_ segue come:
	_Firma e cifratura_: 
		il mittente $U$ genera la firma $f= \mathcal{D}(m,k_{U}[prv])$ ,calcola il _crittogramma_ $c=\mathcal{C}(f,k_{V}[pub])$ e spedisce a $V$ la coppia $\langle U,c\rangle$
	_Decifrazione e verifica_:
		il destinatario $V$ riceve la coppi $\langle U,c\rangle$ e calcola $f=\mathcal{D}(c,k_{V}[prv])=\mathcal{D}(m,k_{U}[prv])$ e calcola il messaggio $m=\mathcal{C}(f,k_{U}[pub])$ se $m$ è un messaggio _significativo_ allora la _firma è verificata e il messaggio decifrato_, che succeda con un utente che non sia $U$ è altamente improbabile.

Proprietà:
- Rispetta le stesse proprietà del protocollo 1

#### Protocollo 2 con RSA
un implementazione pratica dello schema del  _protocollo 2_  è quella realizzata con il [[Cifrario asimmetrico RSA|cifrario RSA]]. 
_siano_ 
- $k_{U}[pub]=\langle e_{U},n_{U}\rangle$ e $k_{U}[prv]=\langle d_{U}\rangle$ le chiavi di $U$ 
-  $k_{V}[pub]=\langle e_{V},n_{V}\rangle$ e $k_{V}[prv]=\langle d_{V}\rangle$ le chiavi di $V$ 
_allora_
	_firma e cifratura_:
		$U$ genera _la firma_ del messaggio $m$ come $\mathcal{D}(m,k_{U}[prv])=f=m^{d_{U}} \mod  n_{U}$ ed esegue la _cifratura_ $\mathcal{C}(f,k_{V}[pub])=c=f^{e_{V}} \mod  n_{V}$ e _spedisce_ la coppia $\langle U,c \rangle$ a $V$
	_Decifratura e verifica_:
		$V$ riceve la coppia $\langle U,c \rangle$ e calcola $\mathcal{D}(c,k_{V}[prv])=f=c^{d_{V}} \mod  n_{V}$ e $\mathcal{C}(f,k_{U}[pub])=m = f^{e_{U}} \mod  n_{U}$ se il messaggio $m$ è significativo allora è _autentico_.

per le proprietà algebriche del [[Cifrario asimmetrico RSA|cifrario RSA]] abbiamo che per far si che questo protocollo per funzioni correttamente deve essere vero che $$n_{U} \leq n_{V}$$per fare in modo che $f < n_{V}$  e possa essere cifrata correttamente da $U$. Avere questa limite pero impedirebbe a $V$ di inviare messaggi _firmati e cifrati_ a $U$, in pratica funziona solo in una direzione.
per ovviare a questo problema si utilizzano _due coppie_ di chiavi _pubbliche e private_ una per _cifrare_ il messaggio e una per _firmarlo_

Per realizzare ciò è stato scelto _pubblicamente_ un numero $H= 2^{1024}$ e _ogni utente_ genera 2 coppie di chiavi diverse
	_cifratura_ : $k_{U}[pub]=\langle e_{U},n_{U}\rangle$ e $k_{U}[prv]=\langle d_{U}\rangle$ _con_ $n_{U}>H$ 
	_firma_:      $k_{U}[pub]=\langle e_{U}',n_{U}'\rangle$ e $k_{U}[prv]=\langle d_{U}'\rangle$ _con_ $n_{U}<H$
$H$ è abbastanza grande per garantire che le chiavi siano abbastanza grandi, in piu avere due chiavi diverse aumenta la sicurezza del sistema.

##### Attacchi al protocollo 2 con RSA
Supponiamo che l utente $U$ invii una _risposta automatica_ ad ogni messaggio $m$ ricevuto _cifrato e firmato_, risposta firmata da $U$
queste condizioni permettono ad  un crittoanalista $X$ di leggere i messaggi inviati dagli altri utente a $U$ seguento la procedura: 
1.  $X$ intercettala coppia $\langle c,V \rangle$ ovvero il _crittogramma firmato_ $c= \mathcal{C}(f,k_{U}[pub])$ che è stato inviato a $U$ da un utente $V$ notiamo che $f=\mathcal{D}(m,k_{V}[priv])$
	1. lo rimuove dal canale e spedisce a $U$ la coppia $\langle c,X \rangle$ facendogli credere che sia stato $X$ ad inviare quel messaggio. 
2. $U$ _decifra_ $c$ ottenendo $f=\mathcal{D}(c,k_{U}[prv])$ ovvero la _firma corretta_ di $V$ su $m$, ma supponendo che il messaggio venga da $X$ calcolerà $$m'  = \mathcal{C}(f,k_{X}[pub])\not = m$$dove $m'$ sara  un messaggio _privo di senso_. A questo punto $U$ manderà un messaggio automatico di _ack_ a $X$ inviando $c'=\mathcal{C}(f',k_{x}[pub])$ dove $f'=\mathcal{D}(m',k_{U}[prv])$
3. Ora $X$ può risalire al messaggio originale $m$ usando $c'$ attraverso la seguente catena di calcoli $$\begin{array}{}
\mathcal{D}(c',k_{X}[prv]) & = & f' \\
\mathcal{C}(f',k_{U}[pub]) & = & m' \\
\mathcal{D}(m',k_{X}[prv]) & = & f \\
\mathcal{C}(f,k_{V}[pub]) & = & m
\end{array}$$
#### Protocollo 3 
questo protocollo risolve il problema del _protocollo 2_ applicando la firma non direttamente al messaggio $m$ ma a $h(m)$ dove $h$ è una [[Funzioni Hash One-Way|funzione hash one-way]]. Infatti abbiamo che il protocollo segue come:
	_Firma e cifratura_: 
		il mittente $U$ calcola $h(m)$ e genera la firma $f=\mathcal{D}(h(m),k_{U}[prv])$ e calcola il crittogramma $c =\mathcal{C}(m,k_{V}[pub])$ e spedisce a $V$ la tripla $\langle U,c,f \rangle$
	_Decifrazione e verifica_: 
		il destinatario $V$ riceve la tripla $\langle U,c,f \rangle$; decifra $c$ come $m=\mathcal{D}(c,k_{V}[prv])$; calcola $p =h(m)$ e $p’=\mathcal{C}(f,k_{U}[pub])$ se $p’=p$ allora il messaggio è _verificato_.

questo è il protocollo piu usata oggi per fare _firme sicure_ e la firma $f$ non prende tanto spazio essendo passato per una funzione di _hash_
>[!note] invertire l ordine delle operazioni
>invertire l ordine del operazioni di cifratura e decifratura equinvale a crare una busta con una firma sopra piuttosto che firmare il documento, un utente malintenzionato puo usare la firma sostituendo il messaggio.



#### protocollo 4  (Protocollo con certificato)
unendo il _messaggi cifrato_,  [[Protocolli di firma digitale|firmato]] con [[Funzioni Hash One-Way|funzioni hash]] e il _Certificato_ rilasciato da una [[Certification Authority|CA]] abbiamo un protocollo  di comunicazione tra due utenti $U$ e $V$ che segue come:
_firma, cifratura e certificazione_:
	il mittente $U$ si _procura il certificato_ $cert_{V}$ da cui estrarre la chiave publica $k_{V}[pub]$ 
	calcola $h(m)$ e genera la firma $f=\mathcal{D}(h(m),k_{U}[prv])$, calcola il crittogramma $c=\mathcal{C}(m,k_{V}[pub])$ e spedisce a $V$ la tripla $\langle cert_{U},c,f \rangle$ 
		$cert_{U}$ contiene sia la _chiave pubblica_ di $U$ che la specifica [[Funzioni Hash One-Way|funzione hash]] $h$ usata.
 _Verifica del certificato_:
	 il destinatario $V$ riceve la tripla $\langle cert_{U},c,f \rangle$ e verifica l _autenticità_ di $cert_{U}$  utilizzando la _chiave pubblica_ $k_{CA}[pub]$ della _CA_
_Decifrazione e verifica della firma_:
	$V$ decifra il crittogramma $c$ mediante la sua chiave privata ottenendo $m= \mathcal{D}(c,k_{V}[prv])$; 
	verifica l autenticità della firma apposta da $U$ su $m$ controllando che risulti $\mathcal{C}(f,k_{U}[pub])= h(m)$



