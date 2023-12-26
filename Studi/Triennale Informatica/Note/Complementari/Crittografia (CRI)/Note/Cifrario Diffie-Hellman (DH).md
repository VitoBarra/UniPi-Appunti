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
1.  _Alice e Bob_ si accordano pubblicamente su 
	- un [[Numeri primi|numero primo]]  $p$ _molto grande_, solitamente di un migliaio di _bit_, questo si può ottenere con l [[Generazione di numeri Primi|algoritmo di generazione di numeri Primi]] 
	- su un [[Generatori di insieme di coprimi|generatore]] $g$ di $\mathcal{Z}_{p}^{*}$ che _esiste sicuramente_ essendo $p$ primo. 
	- in caso non si riesca a generare questa coppia si può perdere una coppia pubblica nel sistema senza compromettere il cifrario
2. _Alice_ estrae un numero casuale $x<p$  e calcola $X = g^{x} \mod p$ e lo spedisce in chiaro a _Bob_ 
3. _Bob_ estrae un numero casuale $y < p$ e calcola $Y= g^{y} \mod  p$ e lo invia ad _alice_ in chiaro
4.  _Alice_ riceve $Y$  e calcola $k[session] = Y^{x} \mod p = g^{xy} \mod  p$
5. _Bob_ riceve $X$ e calcola $k[session] = X^{y} \mod p = g^{xy} \mod p$

#### Attacchi al cifrario
un __crittoanalista *passivo*__ per rompere questo cifrari dovrebbe estrarre uno dei numeri casuali da $X$ o $Y$.
velenerò farlo con $X$ dovrebbe risolvere $$\begin{array}{}
X=g^{x} & \mod  p \\
\log_{g}(X)=x  & \mod   p
\end{array}
$$ovvero risolvere l equazione usando i [[Funzioni One-Way Trapdoor#Calcolo del logaritmo discreto|logaritmo discreto]] che è un problema difficile.
una volta ottenuto $x$ potrà calcolare $k[session]=Y^{x}\mod p$ 


un __crittoanalista *attivo*__ se ha la possibilità di modificare i messaggi inviati può attuare un tipo di attacco [[Tipologia di attacchi ai cifrari|man in-the-midle]] 

![[IMG_0598.jpeg]]
_Eve_ (eavesdropper) è l intente malevolo che vuole infiltrarsi nella comunicazione e lo scegliendo un intero $z$ qualsiasi e calcolando $Z =g^{z} \mod  p$ e si trapone tra il canale di comunicazione di _alice_ e _Bob_ obbligandoli a comunicare con se stessa.
al momento dello scambio di $X$ e $Y$ _Eve_ invia ad entrambi $Z$. questa viene ricevuta da _Alice_ e _Bob_ come proveniente dal partner e generano cosi due chiavi $k[session]$ diverse $$
\begin{array}{}
K_{A} = Z^{x} \mod  p = g^{xz}  & \mod p \\
K_{B} = Z^{y} \mod  p = g^{yz}  & \mod p
\end{array}
$$e le comunicazioni successive verranno fatte tramite _Eve_ che inoltrerà i messaggi dal uno al altro per restare nel segreto.

questo tipo di problema è risolto con il _[[Certification Authority|Certification Authority]]_
