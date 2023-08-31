---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Protocolli Zero Knowledge
---
I _protocolli Zero-Knowledge_ si bassano sulle _dimostrazioni Zero-Knowledge_, queste sono dimostrazioni matematiche dove dato un _provider_ $P$ e  un _verificatore_ $V$ il provider $P$ riesce a dimostrare a $V$ di avere una data _conoscenza o facoltà_ senza dare nessun informazioni a $V$ su metodo utilizzato per avere le informazioni necessarie per dimostrarlo.

la _dinamica_ della dimostrazione sarà del tipo
$V$ chiederà a $P$ di dimostrare una certa facoltà per $k$ volte _se_ per $k$ vote $P$ è riuscito a fornire la dimostrazione _allora_ $V$ sarà sicuro che $P$ abbia effettivamente quella facoltà con una [[Probabilità e variabili aleatorie|probabilità]] prossima ad 1. Ovvero farà un test se la probabilità di indovinare a caso è $\cfrac{1}{2}$ avremmo che la probabilità che $P$ abbia effettivamente quella facoltà sarà $1-\cfrac{1}{2^{k}}$  

Un esempio di questo è il seguente:
$P$ afferma di sapere se il numero di granelli di sabbia in una spiaggia è pari o dispari indicato con $b_{i}$ e $V$ potrà controllare che questo sia vero con _probabilità arbitrariamente_ vicino ad $1$.

per verificare ciò $V$ chiederà a $P$ una sequenza di $k+1$ domande, la prima sarà quella di calcolare $b_{0}$  mentre le iterazioni successive saranno
1. $V$ chiede a $P$ di voltarsi
2. $V$ sceglie un bit _random_ $e$ 
3. $if(e=0)$ $V$ muove un granello di sabia _else_ non fa nulla 
4. $if(e=0 \ AND\  b_{i}\not = b_{i-1}) \ OR \ (e=1 \ AND\  b_{i}= b_{i-1})$ allora $V$ parra alla prossima interazioni _altrimenti_ $P$ è un impostore

siccome la _probabilità_ che $P$ indovini a caso ad ogni iterazione è $1/2$  ed essendo gli eventi indipendenti abbiamo che con questa procedura $V$ può essere sicuro che $P$ abbia quella facoltà con _[[Probabilità e variabili aleatorie|probabilita]]_ $1-\cfrac{1}{2^{k}}$ 
 

## Principi generale
nottano che sia $P$ che $V$ possono essere 
_onesti_: se seguono il protocollo
_disonesti_: se uno dei due mente o non rispetta una delle proprieta sotto elencate  
in gnetale per definire dei protocolli _Zero-Knowledge_ dovendo essere veri i _seguenti principi_ 
_Completezza_:
	se l’affermazione di $P$ è vera, $V$ ne accetta sempre la dimostrazione. 
_Correttezza_: 
	se l’affermazione di $P$ è falsa ($P$ è disonesto), $V$ può essere convinto della veridicità di tale affermazione solo con “bassa probabilità”, cioè una probabilità $\leq 1/2^{k}$ per un valore arbitrario $k$ scelto da $V$.
	Alternativamente la correttezza può essere riformulata dicendo che se $P$ è _onesto_ sarà in grado di convincerne $V$ con probabilità $\geq 1 − 1/2^{k}$. 
_Conoscenza-Zero_: 
	Se l’affermazione di $P$ è vera nessun verificatore $V$ , anche se disonesto (nell’uso del protocollo), può acquisire _alcuna informazione_ su questo fatto salvo la sua veridicità.


In generale i [[Protocolli di Identificazione|protocolli di identificazioni]] che rispettano queste proprietà riescono ad essere molto sicuri siccome non danno nessun informazioni oltre l identità ne al sistema in cui si stanno autenticando sia ai possibili intrusi.
