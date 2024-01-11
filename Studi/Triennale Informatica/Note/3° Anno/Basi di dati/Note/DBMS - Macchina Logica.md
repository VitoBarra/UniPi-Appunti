---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# DBMS - Macchina Logica
---
La _Machina Logica_ di un [[Architettura di un DBMS|architettura di un DBMS]] gestisce

## Macchina logica
La _macchina logica offre_ una visione dei dati permanenti come un insieme di tabelle relazionali sulle quali si opera con gli operatori dell’SQL.
Essa prevede i seguenti
moduli:
- Il gestore delle autorizzazioni per controllare che solo gli utenti autorizzati facciano uso dei dati con le modalità consentite. 
- Il gestore del catalogo per trattare i metadati, ovvero le informazioni sulle caratteristiche logiche e fisiche dei dati presenti.
- Il _gestore delle interrogazioni_ per controllare la correttezza delle interrogazioni e stabilire la strategia migliore per eseguirle con un opportuno algoritmo detto _piano di accesso_.


### Gestore delle interrogazioni 
La _gestione delle interrogazioni_, è svolta con le seguenti fasi:
1. _Controllo lessicale, sintattico e semantico_ dell’interrogazione e sua rappresentazione in forma di albero logico.
2. Riscrittura algebrica dell’albero logico.
3. _Ottimizzazione fisica_ e generazione del _piano di accesso_.
4. Esecuzione del _piano di accesso_.
Una volta controllata la correttezza dell’interrogazione, essa viene rappresentata con un albero logico, usando i seguenti operatori dell’algebra relazionale estesa per operare su [[Struttura dati - MultiInsieme|multinsiemi]], come accade in [[Linguaggio per Database - SQL|SQL]].
-  Proiezione senza l’eliminazione dei duplicati: $\pi_X^b(O)$, con $X$ alcuni attributi di $O$.
 - Eliminazione dei duplicati da un multinsieme: $\delta(O)$.
- Ordinamento del risultato: $\tau_X(O)$, con $X$ alcuni attributi di $O$.
 - Operatori insiemistici senza l’eliminazione dei duplicati: $O_1 \cup^b O_2, O_1 \cap^b O_2,O_1 -^b O_2$.

Gli operatori dell’[[Modello relazionale - Algebra Relazionale|algebra relazionale]] su insiemi per la restrizione, prodotto, giunzione e raggruppamento con aggregazioni non cambiano per applicarli a [[Struttura dati - MultiInsieme|multinsiemi]].



#### Riscrittura algebrica
Durante la _riscrittura algebrica_ si applicano tecniche di [[Algebra Relazionale - Trasformazione di espressioni|trasformazione dell’interrogazione]], basate sulle proprietà algebriche degli [[Modello relazionale - Algebra Relazionale|operatori relazionali]]

#### Ottimizzatore fisico
SI occupa di tradurre l _albero logico_  in un _albero fisico_ o _piano di accesso_ di operazioni fisiche che rappresentano le operazioni da fare per relaziare le operazioni del _albero logico_


ogni DBMS ha i suoi operatori fisici qui si usano le operazioni fisiche del sistema _JRS_.

_Operatori per la scansione di relazioni_ ($R$)
- _TableScan($R$)_: ritorna la collezione dei record di $R$.
- _SortScan_($R$, ${A_i}$): ritorna la collezione dei record di $R$ ordinati sui valori degli ${A_i}$ in modo crescente (o decrescente).
 $R$ è il nome di una [[Modello dati - Modello Relazionale|relazione]], e quindi questi operatori sono necessariamente sulle foglie di un albero fisico.


Operatore per la _proiezione con duplicati_ ($\pi^b$) 
L’operatore fisico ha come argomento la collezione dei record $O$ restituiti da un _altro operatore fisico_:
- Project($O, {A_i}$): ritorna la proiezione dei record di $O$ sugli attributi $\{A_i\}$, senza l’eliminazione dei duplicati.
 

Operatore per _l’eliminazione di duplicati_ ($\delta$):
elimina i duplicati
- _Distinct_($O$): ritorna la collezione dei record _diversi_ di O 
	- I record $O$  devono essere ordinati


Operatore per l’_ordinamento_ ($\tau$) 
Per ordinare i dati ritornati da un _operatore fisico_ $O$ si usa il seguente operatore fisico:
- Sort($O, {A_i}$): ritorna la collezione dei record di $O$ ordinati sugli ${A_i}$.


> [!note] 
> - _SortScan_ prima ordina i record di una relazione in memoria permanente e poi li ritorna
>- il _Sort_ prima memorizza i record di $O$ in una relazione temporanea, poi li ordina e infine li ritorna. 
>	- Se non cè spazio disponibile nel [[DBMS - Macchina Fisica|buffer]], la relazione temporanea viene memorizzata in memoria permanente. Per ordinare una relazione in memoria permanente si usa il [[Merge Sort|merge sort]]


_Operazione per la restrizione_ $(\sigma)$

L’operazione $σ_\psi(R)$ può essere realizzata in modi diversi:
se la condizione $\psi$ usa attributi senza di [[DBMS - Macchina Fisica#Indici|indici]]
- si esaminano tutti i record di $R$ e si controlla quali di essi soddisfano la condizione $\psi$. 

se la condizione $\psi=A \ \theta\ c$ con $A$ un attributo con [[DBMS - Macchina Fisica#Indici|indici]] $c$ una costante e $\theta$ un operazione
- Si usa l indice per controllare dove vale la condizione.

Se la condizione è  $\psi = \psi_1 ∧ \psi_2$ (_and_) su _attributi con indice_ allora ci sono due metodi
- è basato sul fatto $\sigma_\psi(R) = \sigma_{\psi_1} (\sigma_{\psi_2} (R))$ si calcola $\sigma_{\psi_2} (R)$ __usando l indice__ e si esegue $\sigma_{\psi_1}(R)$ __senza usare Indici__
	- Quindi si puo usare quando solo uno dei due ha indici
- si calcola  $S_1=\sigma_{\psi_1}$ e $S_2=\sigma_{\psi_2}$ _usando gli indici_ e per recuperare i record si prende il risultato di $S_1 \cap S_2$.

se la condizione è  $\psi = \psi_1 \lor\psi_2$ (_or_) su attributi con indice allora 
- si calcola  $S_1=\sigma_{\psi_1}$ e $S_2=\sigma_{\psi_2}$ _usando gli indici_ e per recuperare i record si prende il risultato di $S_1 \cup S_2$.


gli _operatori fisici_ che realizzano questi algoritmi sono:
- Filter($O, \psi$): ritorna la collezione dei record di $O$ che soddisfano la condizione $\psi$.
- IndexFilter($R, Idx, \psi$): ritorna la collezione dei record di $R$ che soddisfano la condizione $\psi$, con l’uso dell’indice $Idx$ definito su attributi di $R$. 
	- La condizione $\psi$  deve essere un _prodotto logico_ (AND) e devono essere presenti solo attributi su cui è definito l’indice. 
	- Il _risultato_ è _ordinato_ sugli attributi di $R$ sui quali è definito l’indice. 
	- L’operatore esegue due operazioni: 
		- utilizza _l’indice_ per trovare rapidamente i riferimenti ai record che soddisfano la condizione 
		- recupera i record di $R$. 
> [!note]
> Queste due operazioni potrebbero essere realizzate con due operatori fisici che di solito nei DBMS commerciali sostituiscono l’operatore IndexFilter($R, Idx, \psi$)



Operatori di giunzione ($\bowtie$):

gli operatori fisici sono:
- NestedLoop($O_E, O_I, \psi_J$): ritorna la giunzione dei record di $O_E$ e $O_I$ che soddisfano la condizione di giunzione $\psi_J$.
- IndexNestedLoop($O_E,O_I,\psi_J$): ritorna la giunzione dei record di $O_E$ e $O_I$ che soddisfano la condizione di giunzione $\psi_J$
	- supponendo che
		- esiste un indice _Idx_ sugli attributi di _giunzione_ della __relazione interna__
		- la condizione di _giunzione_ sia $O_E.A_i = O_I.A_j$
		- _Idx_ sia un indice su $S.A_j$. 
	- L’operatore interno $O_I$ puo essere: 
		- IndexFilter($S, Idx, \psi_J$): per ogni record $r$ di $O_E$ si usa l’indice Idx su $S.A_j$ per trovare i record $s$ di $O_I$ che soddisfano la condizione di giunzione $S.A_j = O_E.A_i$ con $O_E.A_i = r.A_i$
		- Filter($O, \psi$) con $O$ un IndexFilter($S, Idx, \psi_J$): si esegue l _IndexFilter_ e poi al risultato  si applica _Filter_ in modo da restituire solo quelli che soddisfano anche  $\psi$
- MergeJoin($O_E, O_I, \psi_J$) (anche chiamato SortMerge): ritorna la giunzione dei record di $O_E$ e $O_I$ che soddisfano la condizione di giunzione $\psi_J$, supponendo che 
	- i record di $O_E$ e $O_I$ siano ordinati sui relativi attributi di giunzione 
	- la condizione di giunzione sia fra una chiave di $O_E$ e una chiave esterna di $O_I$.


dove gli algoritmi eseguiti negli operatori fisici sono i seguenti:
_siano_ $R,S$ le due [[Modello dati - Modello Relazionale|relazioni]] 
_vogliamo_ fare la  [[Modello relazionale - Algebra Relazionale|giunzione]] delle due  su $R.B$ e $S.D$
_ovvero_ vogliamo realizzare l [[Modello relazionale - Algebra Relazionale|operazione logica]] $\underset{R.B=S.D}{\bowtie}$ 


_NestedLoop_: l Algoritmo immediato che non ha bisogno di nulla per funzionare
```pseudo
	\begin{algorithm}
	\caption{NestedLoop}
	\begin{algorithmic}
	\Function{NestedLoop}{R,S}
	\State risultato = []
	\For{$\boldsymbol{each} \ r \in R$}
		\For{$\boldsymbol{each} \ s \in S$}
			\If{r[B]=s[D]}
			\State risultato += $<r,s>$
			\EndIf
		\EndFor
	\EndFor
	\Return risultato
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
Complessita: $O(nm)$

_IndexNestedLoop_: una versione più efficiente del NestedLoop che si puo usare solo se esiste l indice del parametro di giunzione delle relazione interna $O_I$ (in questo caso $S.D$)
```pseudo
	\begin{algorithm}
	\caption{IndexNestedLoop}
	\begin{algorithmic}
	\Function{IndexNestedLoop}{R,S,idxD}
		\state risultato = []
		\For{$\mathbf{each} \ r \in R$}
		\State L = idxD.Findwhere(s[D]=r[B]) (Ovvero $\{s \in S\mid  s[D]=r[B]\}$)
			\For{$\mathbf{each}\  s \in L$}
			\State risultato += $<r,s>$
			\EndFor
		\EndFor
		\Return Risultato
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
complessita: 

_mergeJoin_ (o detto _SortMerge_): si può usare se le relazioni sono ordinate sugli attributi di giunzione 
```pseudo
	\begin{algorithm}
	\caption{MergeJoin}
	\begin{algorithmic}
	\Function{SortMerge}{R,S}
		\State r = R[1];  (r = null se R è vuota)
		\State s = S[1];  (s = null se S è vuota)
		\state risultato = []
		\While{!r == null AND !s == null}
			
			\If {r[B] == s[D]} 
				\While{!s == null AND r[B] == s[D]} 
					\State risultato += $<r,s>$
					\State s = succ(s) 
				 \EndWhile
					\State r = succ(r) 
			\Else
			 	\If {r[B] < s[D]} 
					 \State r = succ(r)
				\Else 
					 \State s = succ(s);
				 \EndIf
			 \EndIf
		\EndWhile
		\Return risultato
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
dove _succ_($w$) il record successivo a $w$  oppure il valore null se $w$ e l’ultimo




Operatore per il raggruppamento($\gamma$):
- GroupBy($O,{A_i},{f_i}$): ritorna una collezione di record, uno per ogni gruppo di record di $O$, con attributi quelli di raggruppamento ${A_i}$ e le funzioni di aggregazione ${f_i}$, supponendo che 
	- i record di $O$  devono essere __ordinati su gli attributi di raggruppamento__
	- Il risultato e ordinato su gli attributi di raggruppamento



Operazione di unione, differenza e intersezione ($\cup,-,\cap$)
- UnionAll ($O_E,O_I$): ritorna l’unione dei record degli operandi senza l’eliminazione dei duplicati.
- Union($O_E, O_I$ ), Except ($O_E,O_I$), Intersect ($O_E, O_I$): ritornano la collezione dei record delle [[Operazioni Insiemistiche|operazioni insiemistiche]], supponendo che
	- i record degli operandi siano _dello stesso tipo_, _ordinati_ e _privi di duplicati_.





##### Esecuzione di un piano d accesso
Ogni operatore fisico di un piano di accesso è un [[Iteratori|iteratore]], cioè e realizzato con un oggetto con quattro metodi:
- _open_(): inizializza lo stato dell’operatore ed esegue il metodo open degli operatori fisici dei suoi argomenti.
- _next_(): ritorna il record successivo del risultato interagendo con gli operatori fisici dei suoi argomenti.
- _isDone_(): ritorna true se non ci sono altri record da ritornare, false altrimenti.
- _close_(): termina le operazioni dell’operatore fisico e dei suoi argomenti.
 
Supponendo che _AlberoFisico_ sia il nome di un piano di accesso, il risultato dell’interrogazione si ottiene eseguendo il seguente programma: 
```python
AlberoFisico.open(); #inizia le operazioni
while !AlberoFisico.isDone(): #finchè ci sono elementi 
	print(AlberoFisico.next()) #stampa prossimo record
AlberoFisico.close();   #termina le operazioni   
```
eseguendo il metodo open della radice dell’albero, esso inizializza lo stato dell’operatore ed esegue l’open del figlio e cosı via fino ad arrivare alle foglie. Cosi termina la fase di inizializzazione

Inizia la fase di generazione del risultato. Quando si esegue il metodo next della radice dell’albero, esso esegue il next del figlio per ottenere il prossimo record del risultato, il figlio fa la stessa operazione sul figlio e cosı via fino ad arrivare alla foglia: i record ritornati dalla foglia faranno la strada inversa.

Ogni operatore quindi è pronto a restituire un record alla volta, risultato dell’elaborazione del record ottenuto dal figlio (o dai figli, nel caso di operatori binari). 

Il __Sort__ è l’unico operatore che si discosta da questo schema: il metodo che compie gran parte del lavoro nel open, che richiede tutti i record al nodo figlio, li memorizza ordinati in una relazione temporanea per poi restituirli uno alla volta su richiesta del nodo padre.




#### Gestore della concorrenza 
La tecnica utilizzata più comunemente per realizzare il controllo della concorrenza nei sistemi centralizzati è la tecnica del [[Tecniche di prevenzione Deadlock - Two phase lock |blocco a due fasi]] (Two Phase Lock, 2PL) . 
Utilizzando questa tecnica, si associa ad ogni dato usato da un’operazione un blocco ([[Lock|lock]]) in lettura o in scrittura. Ogni transazione, prima di eseguire un’azione su di un dato, richiede il blocco corrispondente di lettura o scrittura.
Due transazioni non possono avere blocchi incompatibili sullo stesso dato, ovvero blocchi con almeno uno dei due di scrittura. Pertanto in ogni momento, per ogni dato possono essere stati assegnati o più blocchi in lettura o un solo blocco in scrittura.
La transazione che richiede un blocco incompatibile su un dato viene messa in attesa, e risvegliata solo quando il dato diventa disponibile. Per garantire la serializzabilità e l’isolamento, ogni transazione viene di solito eseguita con la tecnica del blocco a due fasi stretto, che prevede che i blocchi di una transazione vengano rilasciati tutti assieme, solo dopo che la transazione sia terminata. La tecnica del blocco prevede che una transazione venga posta in attesa quando richiede un blocco che non pu`o ottenere. Pu`o accadere che questa attesa diventi infinita: supponiamo che T1 ottenga un blocco in scrittura su X1 e T2 ottenga un blocco in scrittura su X2, e che successivamente T1 richieda anch’essa un blocco in scrittura su X2: in questo caso T1 viene messa in attesa del fatto che T2 rilasci il proprio blocco. Se a questo punto T2 richiede un blocco su X1, anche T2 va in attesa del fatto che T1 rilasci il proprio blocco, e si crea una situazione di attesa “circolare”, ovvero di stallo (deadlock). I metodi comunemente usati per sbloccare una situazione di stallo sono i seguenti.– Rilevazione tramite grafo delle attese: si costruisce un grafo avente come nodi le transazioni, aggiungendo un arco da T1 a T2 ogni volta che T1 va in attesa del rilascio di un blocco da parte di T2. Ogni volta che si crea un ciclo nel grafo, una delle transazioni coinvolta viene fatta abortire (tipicamente la pi` u giovane, quella che ha meno risorse o quella il cui aborto ha il minor costo).– Rilevazione per time-out: ogni volta che un’attesa si prolunga oltre un certo limite, la transazione in attesa viene abortita, presupponendo l’esistenza di uno stallo. Il blocco a due fasi garantisce la serializzabilit`a, ma limita la concorrenza possibile tra diverse transazioni. Ad esempio, un’applicazione lunga che legge una grande quantit`a di dati potrebbe non riuscire mai ad acquisire tutti i blocchi necessari, oppure, quando li avesse acquisiti tutti, potrebbe impedire ad ogni altra transazione che vo glia effettuare modifiche di partire. Per questo motivo, molti sistemi permettono al programmatore di limitare la quantit`a di blocchi richiesti dalle applicazioni, anche se questo comporta la perdita della serializzabilit`



#### Gestore del affidabilita

Compito del gestore dell’affidabilit`a `e di eseguire le operazioni delle transazioni e la loro terminazione garantendo che la base di dati contenga solo gli effetti delle transazioni terminate normalmente e sia protetta da fallimenti di transazione, di sistema e disastri. Le operazioni delle transazioni possono essere eseguite con algoritmi diversi. Supponiamo che si adotti l’algoritmo disfare-rifare, come accade nei sistemi DB2 e Oracle:– Unamodifica di un dato pu` o essere riportata sulla base di dati prima che la transazione termini. Nel caso di fallimento di transazione o di sistema occorre annullare le modifiche fatte dalla transazione sulla base di dati (disfare).– Unatransazione T ` e considerata terminata normalmente, e viene scritto nel giornale (descritto pi` u avanti) il record (T, commit), senza che le sue modifiche vengano preventivamente riportate nella base di dati; questo compito viene svolto dal gestore del buffer quando lo ritiene opportuno. Nel caso di fallimento di sistema occorre rifare le modifiche fatte dalle transazioni terminate normalmente perch´ e non si ` e certi che i loro effetti siano stati riportati sulla base di dati. La struttura dati che viene utilizzata in maniera cruciale tanto per disfare che per rifare gli effetti delle transazioni ` e il giornale delle modifiche (log). Questo `e un archivio gestito in maniera sicura (cio` e mantenuto in due copie su dispositivi con fallimento indipendente) che contiene, per ogni operazione effettuata da una transazione sui dati, le seguenti informazioni
– L’identificatore della transazione che ha effettuato l’operazione.– L’operazione eseguita (inserzione, aggiornamento, cancellazione, inizio transazione, commit, abort).– L’identificatore del record modificato.– Il vecchio ed il nuovo valore del record. Poich´e un malfunzionamento pu`o anche intercorrere tra il momento in cui un’operazione viene eseguita ed il momento in cui tale operazione viene registrata nel giornale, ` e essenziale registrare tutte le operazioni nel giornale prima che esse vengano eseguite. Pi` u precisamente, ` e necessario seguire le due regole seguenti: 1. Regola per disfare (Write ahead log): prima di eseguire una modifica, occorre salvare il vecchio valore nel giornale, in modo che non vada perduto in caso di malfunzionamento. 2. Regola per rifare (Commit Rule): prima di considerare terminata una transazione, occorre salvare nel giornale i nuovi valori dei dati modificati, in modo da poter rieseguire la transazione in caso di fallimento di sistema o di disastro.

286 Avendoadisposizione il giornale, ed una vecchia copia della base di dati, la procedura di ripristino in caso di malfunzionamento `e la seguente:– In caso di fallimento di transazione, si disfano gli effetti di tutte le operazioni della transazione, utilizzando le informazioni sul giornale, ed infine si memorizza una marca di abort sul giornale stesso.– Incasodifallimento di sistema, prima di rendere operativa la base di dati, si esegue il comando restart che scandisce il giornale per disfare gli effetti delle transazioni attive al momento del fallimento e per rifare gli effetti delle transazioni terminate normalmente. Per limitare poi la porzione di giornale da scandire, i DBMS effettuano ad intervalli brevi e regolari un’operazione di allineamento (checkpoint) che consiste nel riportare in memoria permanente tutti gli aggiornamenti effettuati nei buffer, e nel memorizzare poi sul giornale una marca di checkpoint. In questo modo, in caso di fallimento di sistema, la procedura di ripristino pu`o partire dallo stato del giornale e della base di dati in linea, avendo la certezza che non c’` e bisogno di rifare nessuna delle operazioni eseguite prima del checkpoint. Si osservi tuttavia che ` e necessario disfare le operazioni eseguite prima e dopo il checkpoint da transazioni non terminate normalmente.– In caso di disastro, si porta in linea la vecchia copia stabile dello stato della base di dati e si riapplicano ad essa tutte le operazioni registrate sul giornale da parte di transazioni che abbiano effettuato il commit. Se la vecchia copia era stata presa in un momento di attivit` a del sistema, ` e anche necessario disfare gli effetti di tutte le transazioni che erano in corso al momento della copia e che non avevano ancora effettuato il commit al momento del malfunzionamento. Si osservi che la regola per disfare garantisce che il vecchio valore di un record modificato non vada mai perduto, ma implica che, in seguito ad un malfunzionamento avvenuto poco dopo la scrittura del record nel giornale, non sia possibile sapere se l’operazione fosse stata realmente effettuata sui dati. Si osservi inoltre che un malfunzionamento pu`o avere luogo anche durante il ripristino. Per ambedue questi motivi, ` e importante che le operazioni di “disfacimento” e “rifacimento” che si effettuano durante il ripristino siano effettuate in maniera “idempotente”, ovvero in modo da ottenere l’effetto voluto sia che si stia disfacendo un’operazione realmente effettuata, sia che si stia disfacendo un’operazione gi`a disfatta.