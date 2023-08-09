---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrari ibridi
---
i _Cifrari ibridi_ sona tipologia di _cifrario_ che utilizzano un [[Cifrari a chiave Simmetrica|cifrario asimmetrico]] e uno [[Cifrari a chiave Asimmetrica|asimmetrico]]

questo si fa perché solitamente i cifrari _asimmetrici_ sono molto meno efficienti dal punto di vista del tempo di crittazione e decriptazione ma non richiedono lo scambio di una chiave, mentre quelli _simmetrici_ sono molto veloci ma ha bisogno dello scambio.

per prendere il meglio dei due mondi si utilizza un cifrario _asimmetrico_ solo per lo scambio delle chiavi del cifrario _Simmetrico_  detta _chiave di sessione_ $k[sesion]$, ad ogni scambio di messaggi si varia la chiave per aumentare la sicurezza di questo tipi di cifrario, si potrebbe non fare ma se ne perde in sicurezza 

e abbiamo che lo schema dello scambio di messaggi è 
$$
\begin{array} {}
  \langle \mathcal{C}_{asim}(k[session],k[pub]) & \mathcal{C}_{sim}(m,k[session]) \rangle \\
  \langle \mathcal{D}_{asim}(k[session],k[priv]) & \mathcal{D}_{sim}(c,k[session]) \rangle
\end{array}
$$



### Protocollo DH
è un protocollo per unche implementa un  _cifrario ibrido_. 
Utilizza la funzione [[Funzioni One-Way Trapdoor|one-way trapdor]] del _logaritmo discreto_ 
i due utenti della scambio di messaggi generano la chiave $k[session]$ in modo incrementale e la scambiano tra di loro  inviando in chiaro alcune parti della chiave. Questa parte è sufficiente a ricostruire la chiave intera solo con le informazioni _private_ e diverse che hanno a disposizione i due utenti. 

Si eseguono i seguenti passi.
- I _Alice e Bob_ si accordano pubblicamente su un [[Numeri primi|numero primo]]  _molto grande_ $p$  solitametne di un migliacciò di cifre binarie, questo si puo ottenere con la [[Generazione di numeri Primi|Generazione di numeri Primi]] e su un [[Generatori di insieme di coprimi|generatore]] $g$ di $\mathcal{Z}_{p}^{*}$ che esiste sicuramente essendo $p$ primo. in caso non si riesca a generare questa coppia si può perdere una coppia publica nel sistema senza compromettere il cifrario
- _Alice_ estrae un numero casuale $x<p$  e calcola $X = g^{x} \mod p$ e lo spedisce in chiaro al secondo 
- _Bob_ estrae un numero casuale $y < p$ e calcola $Y= g^{y}$ e lo invia al primo utente
-  _Alice_ riceve $Y$  e calcola $k[session] = Y^{x} \mod p = g^{xy} \mod  p$
- _Bob_ riceve $X$ e calcola $k[session] = X^{y} \mod p = g^{xy} \mod p$

#### Attacchi al cifrario
un __crittoanalista *passivo*__ per rompere questo cifrari dovrebbe risolvere l equazione usando i logaritmo discrete, quindi deve risolvere un problema difficile.


un __crittoanalista *attivo*__ se ha la possibilità di modificare i messaggi inviati puo attuare un tipo di attacco [[Tipologia di attacchi per scoprire il messaggio criptato|man in-the-midle]] 

![[IMG_0598.jpeg]]
_Eve_ (eavesdropper) è l intente malevolo che vuole infiltrarsi nella comunicazione e lo scegliendo un intero $z$ qualsiasi e calcolando $Z =g^{z} \mod  p$ e si trapone tra il canale di comunicazione di _alice_ e _Bob_ obbligandoli a comunicare con se stessa.
al momento dello scambio di $X$ e $Y$ _Eve_ invia ad entrambi $Z$. questa viene ridivenuta da _Alice_ e _Bob_ come proveniente dal partner e generano cosi due chiavi $k[session]$ diverse $K_{A} = Z^{x} \mod  p = g^{xz} \mod p$ e $K_{B} = Z^{y} \mod  p = g^{yz} \mod p$ e le comunicazioni successive verrano fatte tramite _Eve_ che inoltrerà i messaggi dal uno al altro per restare nel segreto.

questo tipo di problema è risolte con il _Certification Authority_
