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
SI occupa di tradurre l _albero logico_  in un _albero fisico_ o _piano di accesso_ di operazioni fisiche che rappresentano le operazioni da fare per realizzare le operazioni del _albero logico_


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
questo algoritmo preserva l ordine della relazione esterna $R$

Complessità  in numero di accessi alla memoria: $Npag(R)+NRec(R)*Npag(S)$
ma dipende anche dallo spazio che e' disponibile nel buffer, infatti se c e' spazio per mantenere $Npage(S)$ lo si fa e non bisogna leggere piu volte le pagine di $S$ portando il numero di operazioni a $Npag(R)+Npag(S)$  


PagedNestedLoop: Come nested loop ma piu usato per la sua efficienza
```pseudo
	\begin{algorithm}
	\caption{PagedNestedLoop}
	\begin{algorithmic}
	\Function{NestedLoop}{R,S}
	\State risultato = []
	\For{$\boldsymbol{each } \ page \ p_r \in R$}
		\For{$\boldsymbol{each} \ page \ p_s \in S$}
			\For{$\boldsymbol{each } \ tuple \ r \in p_r$}
				\For{$\boldsymbol{each} \ tuple \ s \in p_s$}
					\If{$r[B]=s[D]$}
					\State risultato += $<r,s>$
					\EndIf
				\EndFor
			\EndFor
		\EndFor
	\EndFor
	\Return risultato
	\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
questa versione NON preserva nessun ordine 
la complessità in numero di accessi alla memoria: $Npag(R)+Npag(S)$ 



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




`

