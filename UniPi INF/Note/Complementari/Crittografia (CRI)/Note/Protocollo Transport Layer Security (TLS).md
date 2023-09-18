---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Protocollo Transport Layer Security (TLS)
---
è un protocollo che ha sostituito il [[Protocollo Secure socket layer (SSL)|SSL]] e serve allo stesso scopo, mettere in comunicazione due utenti sulla [[Tipi di rete|rete]] in _modo sicuro_

consiste di due parti come per  [[Protocollo Secure socket layer (SSL)|SSL]]
1. _Protocollo di Handshake_ 
	  Protocollo di scambio chiavi per stabilire e cavi simmetriche condivise
2. _protocollo Record-Layer_
	  Utilizza le chiavi condivise per cifrare e autenticare la comunicazione


_TLS_ permette al _client_ e al _server_ di [[Protocolli di Autenticazione|autenticarsi]] reciprocamente. ma tipicamente è usato solo per autenticar il _server_ e poi l utente si identificherà con un _login_

### Protocollo hand shake
Il _client_ $C$ ha una serie di chiavi publiche di [[Certification Authority|certification authority]] $$k_{ca_{1}}[pub]\dots k_{ca_{n}}[pub]$$
il _server_ $S$ posside una coppia chiave _publica/privata_ per la [[Protocolli di firma digitale|firma digitale]] $$k_{S}[pub]\ \ \ k_{S}[prv]$$
e un _[[Certification Authority|certificato digitale]]_ $cert_{S}$ per $k[pub]_{S}$  rilasciato da una _CA_ di cui il _client_ ha la chiave publica


_Client_:
$C$ invia a $S$ il messaggio iniziale del protocollo [[Cifrario Diffie-Hellman (DH)|DH su primi]] o [[Cifrario Diffie-Hellman su curve ellittiche|DH su curve ellittiche]]  per lo scambio di chiavi, che include
-  la specifica del [[Gruppi|gruppo]] $G$ usato dal _client_
	- il gruppo $G$ può essere l’ [[Insieme dei coprimi|insieme dei coprimi]]. $\mathcal{Z}^{*}_{p}$ ($p$ _[[Numeri primi|primo]]_), oppure una [[Curve Ellittiche|curva ellittica]] 
- il _[[Generatori di insieme di coprimi|generatore]]_ $g$, oppure il punto $B$ della curva e il suo ordine
- il valore $g^{x}$, oppure il punto $xB$, calcolato usando un intero segreto $x$ _[[Generatori di numeri Pseudo Casuali|scelto casualmente]]_ da $C$
-  un _nonce_ (sequenza casuale di bit) $N_C$
- informazioni sulle _ciphersuite_ che è in grado di supportare

_server_:
$S$ completa il protocollo [[Cifrario Diffie-Hellman (DH)|DH su primi]] o [[Cifrario Diffie-Hellman su curve ellittiche|DH su curve ellittiche]] inviando un messaggio al client che contiene $g^{y}$, oppure il punto $yB$, calcolato usando un intero segreto $y$ scelto casualmente da $S$
-  $S$ invia un suo _nonce_ $N_S$
-  $S$ calcola $K = g^{xy}$ (oppure $K = yxB$) e applica una _KEY DERIVATION FUNCTION_ per estrarre da $K$ le chiavi
$$K’_{S}, K’_{C}, K_{S}, K_{C}$$
per una _cifratura autenticata_
- $S$ invia la propria _chiave pubblica_ $k_{S}[pub]$, il certificato $cert_{S}$, la firma $\sigma$ calcolata usando la $k_{S}[prv]$ su tutti i _messaggi di handshake_ inviati
 - Tutti i dati inviati sono cifrati con $K_{S}’$

_client_:
- $C$ calcola $K = g^{xy}$ (oppure $K = x y B$) e applica anche lui la _KEY DERIVATION FUNCTION_ ottenendo $$K’_{S}, K’_{C}, K_{S}, K_{C}$$
- Usa $K’_{S}$ per recuperare $k_{S}[pub]$, il certificato $cert_S$, la firma $\sigma$ (che sono stati cifrati con $K_{S}’$) 

-  _Se_ possiede la _chiave pubblica_ della [[Certification Authority|CA]] che ha rilasciato $cert_{S}$, verifica il certificato

- Verifica la firma $\sigma$ sui _messaggi di handshake_ usando $k_{S}[pub]$
- Calcola il _MAC_ dei messaggi di _handshake scambiati_ usando $K’_{C}$ e lo invia a $S$


### Protocollo record layer
se tutti i _passaggi di handshake_ vanno a buon fine allora 
- $C$ usa $K_{C}$ per _cifrare i messaggi_ che invia a $S$
- $S$ usa $K_{S}$  per _cifrare i messaggi_ che invia a $C$


### Osservazioni
- Alla fine del protocollo di Handshake, $C$ e $S$ _condividono le chiavi di sessione_
	-  $K_C$ e $K_S$ che possono usare per cifrare e autenticare la comunicazione ($K’_C$ e $K’_S$ sono usate solo per la fase di _Handshake_)
-  Dato che $C$ verifica il certificato, sa che $k_{S}[pub]$ è la chiave _pubblica corretta_ di $S$
 - Se la firma $\sigma$ è valida, $C$ conclude che sta comunicando con $S$ 
	- $S$ è l’unico che conosce la _chiave privata_ $k_{S}[prv]$ associata a $k_{S}[pub]$) 
- $S$ firma tutti i messaggi scambiati per l’esecuzione del protocollo _DH_
	- $C$ sa che nessun valore è stato modificato 
-  Il _protocollo DH_ assicura che nessun crittoanalista passivo possa ottenere informazioni su $K$ e sulle chiavi derivate da $K$
-  Alla fine della _fase di Handshake_, $C$ sa che condivide le chiavi $K_{C}$ e $K_{S}$ con il legittimo $S$




### Confronto TSL 1.3 vs  TSL 1.2 e SSL 
Nelle versioni precedenti ([[Protocollo Secure socket layer (SSL)|SSL]], _TLS 1.2_) _client_ e _server_ potevano stabilire la chiave $K$ usando un [[Cifrari a chiave Asimmetrica|cifrario a chiave pubblica]] al posto del protocollo [[Cifrario Diffie-Hellman (DH)|DH]]
- il _client_ sceglieva la chiave $K$ e la cifrava con la _chiave pubblica_ $k_{S}[pub]$ del _server_
 In TLS 1.3 non è più possibile
- per garantire la _FORWARD SECRECY_, cioè la segretezza delle chiavi di sessione precedenti nel caso di un server compromesso

La _forward secrecy_ è una proprietà dei protocolli 
di negoziazione delle chiavi che assicura che _se una chiave di cifratura a lungo termine viene compromessa, le chiavi di sessione generate a partire da essa rimangono riservate_.


_DH_ garantisce _FORWARD SECRECY_ dato che il valore $y$ del 
_server_ usato nel protocollo di _Handshake_ può essere cancellato alla fine del protocollo 

- senza $y$, il crittoanalista non può ricostruire la chiave di sessione $K$

- Usando un _cifrario a chiave pubblica_, non si ha _FORWARD SECRECY_ dato che la chiave privata del server non può _essere cancellata_
- Se un avversario la ottiene, può _decifrare i crittogrammi_ scambiati nelle esecuzioni passate del protocollo di _Handshake_ e recuperare le chiavi di sessione usate dalla parti coinvolte



Combinazione tra cifratura e autenticazione del messaggio, al fine di fornire simultaneamente
- confidenzialita
- autenticita
-  interita del dato trasmesso


_Encrypt-then-MAC_:
	prima si cifra, poi si genera il MAC a partire dal cifrario
	$$m’=\mathcal{C}(m,k)|| MAC(\mathcal{C}(m,k))$$
		_due chiavi_: una per cifrare , una per il _MAC_
_encrypt-and-MAC_:
	$$m’=\mathcal{C}(m,k)||MAC(m)$$
	una sola chiave per cifrare il MAC

_MAC-then-Encrypt_: (usato in TLS)
	$$m’=\mathcal{C}(m||MAC(m),k)$$
	una sola chiave per cifrare e per il mac
