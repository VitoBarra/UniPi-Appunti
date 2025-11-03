---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Teoria dei giochi - Giochi Non-Cooperativi
---
La **[[Teoria dei giochi (Game theory)|teoria dei giochi]] in giochi non cooperativi** descrive formalmente le interazioni strategiche tra [[agenti razionali|agenti razionali]] che agiscono in ambienti in cui le decisioni di ciascuno influenzano gli esiti degli altri. 
Un **gioco in forma normale** dove le azioni vengono simultaneamente è definito da: 
- l’**insieme dei giocatori**: il numbero di player che va da $n>2$ 
- l'**azioni disponibili** che possono o non possono essere uguiali per tuttu i giocatori
- l'**funzione di utilità** che assegna a ciascun giocatore un payoff per ogni combinazione possibile di azioni. Nei giochi a due giocatori, la funzione di utilità può essere rappresentata da una matrice dei payoff, in cui le righe corrispondono alle azioni di un giocatore e le colonne a quelle dell’altro. Ogni cella indica la coppia di utilità associate alle scelte simultanee.
una **strategia** rappresenta la politica decisionale di un giocatore
- Una **strategia pura** corrisponde alla scelta deterministica di una singola azione, 
- una **strategia mista** rappresenta una [[Distribuzione di probabilita|distribuzione di probabilità]] sulle azioni, indicata come $[p:a;(1-p):b]$ nel caso in cui ci siano solo **2** azioni disponibili
Un **profilo strategico** è l’insieme delle strategie adottate da **tutti i giocatori**, e determina l’esito del gioco che è un valore in caso di **strategie pure** o un valore atteso se ci sono **strategie miste**.

La razionalità degli agenti implica che ciascuno debba considerare il comportamento degli altri, generando una catena di ragionamenti del tipo “io so che tu sai che io so”. Le soluzioni formali, dette concetti di soluzione, servono a definire i punti di equilibrio di tali interazioni. 

nella strategie disponibili possono esserci **strategie dominaniti**:
- **dominanza forte:** una strategia $s$ **domina fortemente** un’altra strategia $s'$ se fornisce sempre un payoff maggiore indipendentemente dalle scelte degli altri giocatori; 
- **dominanza debole** una strategia $s$ **domina debbolmente** le altra strategia $s'$ non è mai peggiore e risulta migliore almeno in un caso per ogni scelta degli altri palyer.
un agente razionale se dispone di una **strategia dominante** la scegliera sempre e non sceglie mai una strategia che è dominata.
Se tutti i palyer scelgono **strategia dominanti** l outcome del gioco è detto **dominant strategy equilibrium** ed è detto equilibrio perche nessun giocatore ha incentivi a cambiare strategia.

nella maggior parte dei giochi reali non esistono **strategie dominanti**, Si adotta quindi un criterio più generale: l’equilibrio di Nash. Un **profilo strategico** è un **equilibrio di Nash** se, fissate le strategie degli altri, nessun giocatore può migliorare il proprio payoff modificando unilateralmente la propria strategia. **Formalmente**, per ogni giocatore $i$ e per ogni strategia alternativa $s_i'$ vale $u_i(s_i,s_{-i}) \ge u_i(s_i',s_{-i})$, dove $u_i$ rappresenta la funzione di utilità e $s_{-i}$ il profilo delle strategie altrui. 
Ogni **equilibrio di strategie dominanti** è anche un **equilibrio di Nash**, ma non viceversa.

Un gioco può ammettere più **equilibri di Nash** e ognuno di questi rappresenta uno stato **stabile del gioco**, poiché nessun partecipante ha motivi razionali per cambiare comportamento. l'esistenza di piu equilibri di Nash fa emergere la necessita dei giocatori di convergere su uno dei possibili equilibri, questo è un  **problema di coordinamento** dove gli attori non posso comunicare perche il gioco è non cooperativo.

Non tutti i **giochi ammettono un equilibrio di Nash in strategie pure**. Esistono situazioni in cui ogni scelta deterministica induce uno dei giocatori a preferire una deviazione.
esiste sempre almeno un equilibrio di Nash quando i giocatori usano **strategie miste**




### Calcolare gli equilibiri di Nash
La ricerca degli **equilibri di Nash** in strategie pure può essere condotta mediante esplorazione esaustiva dei **profili strategici**. 
Dato un insieme di $n$ giocatori ciascuno con $m$ azioni, esistono $m^n$ profili possibili rendendo la ricerca esaustiva inpraticabile.

un [[Algoritmi|algoritmo]] per calcolare un **equilibrio di Nash** è la **myopic best response** (o **iterated best response**).  
Il procedimento segue le regole:
1. Si seleziona un profilo di strategie iniziale in modo casuale.  
2. Se un giocatore non sta adottando la strategia ottimale rispetto alle scelte degli altri, egli modifica la propria strategia scegliendo la risposta migliore (**best response**).  
3. Il processo viene ripetuto finché si raggiunge una configurazione in cui ogni giocatore adotta la propria risposta ottimale, data la strategia degli altri.
Quando questo avviene, il sistema si trova in un **equilibrio di Nash**, poiché nessun giocatore ha incentivo a deviare unilateralmente. Questo algoritmo non ha garanzia di convergenza in generale ma risulta efficace per alcune classi di giochi strutturati.


### Calcolo degli equilibri in strategie miste

Per calcolare l’**[[Equilibrio di Nash|equilibrio di Nash]]** nel caso di strategie miste e *[[Giochi a somma zero|giochi a somma zero]]*, si utilizza il **metodo del [[Ricerca MiniMax|maximin]]**, introdotto da Von Neumann, secondo il quale ciascun giocatore tende a **massimizzare il proprio guadagno minimo garantito**.

Siano $E$ e $O$ due giocatori, e sia $u_E(e,o)$ il valore di utilità per $E$ in funzione delle strategie $e$ e $o$.  
Si considerino due scenari fondamentali:
- **Caso 1: $E$ sceglie per prima:**  
  $E$ annuncia la propria strategia e $O$, conoscendola, sceglie la risposta ottimale.  
  Il valore atteso del gioco in questo caso è $U_{E,O}$, che **favorisce $O$**.  
  Pertanto, il valore vero del gioco $U$ deve soddisfare $U \ge U_{E,O}$.
- **Caso 2: $O$ sceglie per primo:**  
  $O$ annuncia la propria strategia e successivamente $E$ sceglie la risposta ottimale.  
  Il valore del gioco è $U_{O,E}$, che **favorisce $E$**.  
  Di conseguenza, $U \le U_{O,E}$.
Combinando i due casi, si ottiene la disuguaglianza fondamentale:
$$
U_{E,O} \le U \le U_{O,E}
$$
dove $U_{E,O}$ e $U_{O,E}$ rappresentano rispettivamente i valori del gioco quando a muovere per primo è $E$ o $O$.  
L’**equilibrio** si trova nel punto in cui entrambe le strategie **ottimizzano simultaneamente** i propri [[Variabili aleatoria - Momenti|rendimenti attesi]], garantendo a ciascun giocatore il **massimo del proprio minimo guadagno** possibile e questo è detto **equilibrio di maximin** che coincide con un  **[[Equilibrio di Nash|equilibrio di Nash]]**  
Un giocatore che adotta la strategia maximin ottiene due garanzie fondamentali:  
1.  nessun’altra strategia può fornire un risultato migliore contro un avversario razionale;  
 2. la strategia resta ottimale anche se viene rivelata all’avversario.



La determinazione di un equilibrio di maximin può essere formalizzata come un problema di **[[programmazione lineare|programmazione lineare]]**, in cui si massimizza una funzione obiettivo soggetta a vincoli lineari.  
Geometricamente, ciascuna strategia mista rappresenta un punto in uno spazio $n$-dimensionale, e le funzioni di utilità corrispondono a iperpiani.  
L’equilibrio si ottiene nel punto di intersezione più alto (o più basso) tra gli iperpiani residui, dopo aver eliminato le strategie dominate.

Nei giochi con più di due giocatori o a somma non nulla, il procedimento generale si articola in due fasi:  
(1) l’enumerazione di tutti i sottoinsiemi di strategie miste per ciascun giocatore;  
(2) la verifica delle condizioni di equilibrio mediante sistemi di equazioni e disequazioni.  

Per due giocatori, queste equazioni restano lineari e possono essere risolte con tecniche di programmazione lineare; tuttavia, per tre o più giocatori diventano non lineari, rendendo il problema computazionalmente più complesso.  
Il **teorema di von Neumann** garantisce che ogni gioco a due giocatori a somma zero ammette un equilibrio di maximin in strategie miste e che ogni equilibrio di Nash in tali giochi coincide con un maximin.


