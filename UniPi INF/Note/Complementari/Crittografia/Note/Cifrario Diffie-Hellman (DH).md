---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifrario Diffie-Hellman (DH)
---
il _cifrario Diffie-Hellamn_ è un  _[[Cifrari ibridi|cifrario ibrido]]_, la sicurezza di questo cifrario si base sulla risoluzione del _logaritmo discreto_ che è problema [[Funzioni One-Way Trapdoor|one-way trapdor]] 

I due utenti della scambio di messaggi generano la chiave $k[session]$ in modo incrementale e la scambiano tra di loro  inviando in chiaro alcune parti della chiave. Questa parte è sufficiente a ricostruire la chiave intera solo con le informazioni _private_ e diverse che hanno a disposizione i due utenti. 

Si eseguono i seguenti passi.
- I _Alice e Bob_ si accordano pubblicamente su un [[Numeri primi|numero primo]]  _molto grande_ $p$  solitamente di un migliaio di cifre binarie, questo si può ottenere con la [[Generazione di numeri Primi|Generazione di numeri Primi]] e su un [[Generatori di insieme di coprimi|generatore]] $g$ di $\mathcal{Z}_{p}^{*}$ che esiste sicuramente essendo $p$ primo. in caso non si riesca a generare questa coppia si può perdere una coppia pubblica nel sistema senza compromettere il cifrario
- _Alice_ estrae un numero casuale $x<p$  e calcola $X = g^{x} \mod p$ e lo spedisce in chiaro al secondo 
- _Bob_ estrae un numero casuale $y < p$ e calcola $Y= g^{y}$ e lo invia al primo utente
-  _Alice_ riceve $Y$  e calcola $k[session] = Y^{x} \mod p = g^{xy} \mod  p$
- _Bob_ riceve $X$ e calcola $k[session] = X^{y} \mod p = g^{xy} \mod p$

#### Attacchi al cifrario
un __crittoanalista *passivo*__ per rompere questo cifrari dovrebbe risolvere l equazione usando i [[Funzioni One-Way Trapdoor|logaritmo discreto]], quindi deve risolvere un problema difficile.


un __crittoanalista *attivo*__ se ha la possibilità di modificare i messaggi inviati può attuare un tipo di attacco [[Tipologia di attacchi ai cifrari|man in-the-midle]] 

![[IMG_0598.jpeg]]
_Eve_ (eavesdropper) è l intente malevolo che vuole infiltrarsi nella comunicazione e lo scegliendo un intero $z$ qualsiasi e calcolando $Z =g^{z} \mod  p$ e si trapone tra il canale di comunicazione di _alice_ e _Bob_ obbligandoli a comunicare con se stessa.
al momento dello scambio di $X$ e $Y$ _Eve_ invia ad entrambi $Z$. questa viene ridivenuta da _Alice_ e _Bob_ come proveniente dal partner e generano cosi due chiavi $k[session]$ diverse $K_{A} = Z^{x} \mod  p = g^{xz} \mod p$ e $K_{B} = Z^{y} \mod  p = g^{yz} \mod p$ e le comunicazioni successive verranno fatte tramite _Eve_ che inoltrerà i messaggi dal uno al altro per restare nel segreto.

questo tipo di problema è risolte con il _[[Certification Authority|Certification Authority]]_
