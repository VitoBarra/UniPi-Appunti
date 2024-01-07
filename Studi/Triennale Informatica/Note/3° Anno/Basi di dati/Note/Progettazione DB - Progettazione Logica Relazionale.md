---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---
	
# Progettazione DB - Progettazione Logica Relazionale
---
la _progettazione logica_ è una parte delle [[Progettazione DB|progettazione di DB]] è questa traduce la [[Progettazione DB - Progettazione Concettuale|progettazione concettuale]] in qualcosa di più usabile in un sistema informatico, _NON_ Tiene conto degli aspetti della _performance_

in particolare per la _progettazione logica_ si tende ad usare il [[Modello dati - Modello Relazionale|Modello Relazionale]] per la sua semplicità e robustezza di teoria


#### Traduzione
la traduzione da _progettazione concettuale_ a _progettazione logica_ avviene secondo i seguenti step

##### 1.Rappresentazioni delle associazioni uno a molti e uno a molti
Le associazioni _uno a molti_ si rappresentano aggiungendo agli attributi della relazione rispetto a cui l’associazione è _univoca_ e _totale_ una _[[Modello Relazionale - Chiavi|chiave esterna]]_ che riferisce l’altra _relazione_

Se l’associazione _ha degli attributi_, questi si aggiungono alla relazione in cui e presente la _chiave esterna_. 

Se l’associazione nella direzione _univoca_ è _parziale_ ci sono due rappresentazioni 
-  si aggiunge allo _schema_ una _nuova relazione_ che contiene _due [[Modello Relazionale - Chiavi|chiavi esterne]]_ che riferiscono le due _relazioni coinvolte_ dall’associazione, e gli _eventuali attributi_ dell’associazione; 
	- questa relazione contiene un _ennupla_ per ogni istanza dell’associazione.
	- La _chiave primaria_ di questa relazione è la _chiave esterna_ che riferisce la relazione rispetto a cui l’associazione è _multipla_. 
- si aggiunge una _chiave esterna_ con _possibili valori nulli_, e gli _eventuali attributi_ della associazione, alla relazione rispetto a cui l’associazione _è univoca_

![[IMG_1054.jpeg]]

Per le associazioni _uno a uno_ si procede in maniera analoga, considerandole un caso particolare di associazioni _molti a uno_.

Si consideri che quando una associazione ha sia la diretta che l’inversa, e si aggiunge una relazione con due _chiavi esterne_, una qualunque delle due può essere scelta come _chiave primaria_. 
![[IMG_1055.jpeg]]

##### 2.Rappresentazioni delle associazioni molti a molti
Un’associazione _molti a molti_ tra due _classi_ si rappresenta _aggiungendo_ allo schema
una _nuova relazione_ che contiene _due chiavi esterne_ che riferiscono le _due relazioni coinvolte_

la _chiave primaria_ di questa relazione è dalle due chiavi _esterne_.
Questa relazione contiene un’ ennupla per ogni istanza dell’associazione.
Se l’associazione _ha degli attributi_, questi attributi vengono aggiunti alla _nuova relazione_

Il modo di rappresentare non cambia per _parzialita_
![[IMG_1051.jpeg]]
##### 3.Rappresentazioni delle gerarchie tra classi
_Sia_  
- $A$ un _classe_ con attributi $(X_{A})$ 
- $K_A$ la _[[Modello Relazionale - Chiavi|chiave primaria]]_ di $A$.
-  $B,C$ due sottoclassi, _tali che_ i tipi associati siano $(X_A,X_B)$ e $(X_AX_C)$, 

ci sono 3 modi per rappresentare questa situazione 
1. _relazione unica_: si definisce un’_unica relazione_ con _attributi_$$(X_A, X_B, X_C, Discriminatore)$$questa raccoglie tutti gli elementi delle tre classi e il _discriminatore_ serve a indicare la classe a cuiappartiene l’elemento, Gli elementi non usati possono essere messi a _NULL_
2. _partizionamento verticale_: si _definiscono tre relazioni_ $R_A(X_A),R_B(K_A, X_B),R_C(K_A,X_C)$. $R_A$ contiene tutti gli elementi della classe $A$, anche se stanno in qualche sottoclasse, mentre $R_B$ ed $R_C$ contengono solo quegli attributi, degli elementi di $B$ e di $C$, che non sono in $X_A$ (attributi _propri delle sottoclassi_), ed una _chiave esterna_ $K_A$ che permette di ritrovare in $R_A$ il valore degli altri attributi. $K_A$ è anche la _chiave primaria_ di $R_B$ ed $R_C$
3. _partizionamento orizzontale_: si definiscono _tre relazioni_ $R_A(X_A), R_B(X_A,X_B), R_C(X_A, X_C)$. $R_A$ contiene solo gli elementi della classe $A$ che _non stanno in nessuna delle sottoclassi_, mentre $R_B$ ed $R_C$ contengono tutti gli elementi di $B$ e di $C$; se le sottoclassi costituiscono una copertura, la relazione $R_A(X_A)$ _non viene definita_ perchè sarebbe _sempre vuota_.

Dei criteri per scegliere cosa usare sono i seguneti
1. Se gli _attributi propri_ delle sottoclassi sono _pochi_ si sceglie la _relazione unica_, per la sua semplicita semplice.
2. il _partizionamento orizzontale_ divide gli elementi della _superclasse_ in piu relazioni diverse, per cui _non e possibile mantenere un vincolo referenziale_ verso la _superclasse_ stessa; 
	1. _Quindi_, _NON_ si usa se un altra relazione fa riferimento alla superclasse tramite _chiave esterna_, ovvero se nello _schema relazionale_ grafico c’e una freccia che entra nella _superclasse_; `
3. il _partizionamento verticale_ rende più complessa la ricostituzione di tutte le informazioni relative ad un elemento della sottoclasse, mentre _il partizionamento orizzontale_ rende piu complessa l’operazione di visita a tutti gli elementi della superclasse, per cui e necessario valutare _l’importanza relativa_ di queste due operazioni;
4. il _partizionamento orizzontale_ e preferibile in presenza di un vincolo di _copertura_ perchè ne può _garantire il mantenimento_; 
5. il _partizionamento orizzontale_ funziona al meglio in presenza di un _vincolo di disgiunzione_, perche, in caso contrario un oggetto puo appartiene a piu sottoclassi, e siccome il _partizionamento orizontale_ replica la chiave e gli attributi della _superclasse_ in tutte le relazioni _sottoclassi_ a cui l’oggetto appartiene si pone il problema di gestire la ridondanza dei dati 

![[IMG_1052.jpeg]]
##### 4. Definizione delle chiavi primarie
questo passo della _trasformazione_ non può essere eseguito sullo _schema grafico_ ma va eseguito _a partire da un’analisi degli attributi_.

Per ognuna delle relazioni una [[Modello Relazionale - Chiavi|Chiave primaria]]

Considerando le _classi_ senza _sottoclassi_. 
La _chiave primaria_ è _di norma_ un _attributo artificiale_, tipicamente un _numero progressivo_ assegnato dal sistema.
é possibile utilizzare un attributo presente nella classe, purche l’attributo sia univoco, totale  

per le classi derivate da _sotto classi_  la chiave primaria sarà la stessa della _superclasse_. 

per le relazioni che corrispondono ad associazioni _molti a molti_ nello schema originario, la _chiave primaria_ sara costituita dalla _concatenazione delle chiavi esterne_. `

L’_inserimento_ di una _chiave primaria_ in ogni collezione trasforma effettivamente tutte le classi in [[Relazioni tra insiemi|relazioni]] in senso matematico
##### 5. Rappresentazione degli atributo multi valore
Una _proprieta multivalore_ di una classe  $C$ si rappresenta eliminando il corrispondente attributo da $C$ e creando una nuova relazione $N$ con una chiave di _due attributi_: 
- una _chiave esterna_ che fa riferimento alla _chiave primaria_ di $C$ 
-  un attributo che corrisponde all’attributo multivalore da trasformare.
 
Un _oggetto_ di $C$ con _[[Modello Relazionale - Chiavi|chiave primaria]]_
$k$ ed in cui l’attributo assume valore $a_1, \dots , a_n$ si rappresenta poi inserendo nella nuova relazione $N$ le coppie $(k, a_1), \dots ,(k, a_n)$.

>[!example]
>considerando l atributo multi valore “telefoni” e applicando la trasformaizonione si ottiene ![[IMG_1056.jpeg]]
##### 6. Appiattimento degli attributi composti 
Se un _attributo_ $A_i$ di uno _schema di relazione_ è di tipo $[A_{i1} : T_{i1}, \dots , A_{ij} : T_{ij}]$, si sostituisce con gli attributi $A_{i1} : T_{i1}, \dots , A_{ij} : T_{ij}$. Se $A_i$ faceva parte della _chiave primaria_ dello _schema di relazione_, si sostituisce $A_i$ con gli _attributi_ $A_{i1}, \dots , A_{ij}$ nella chiave, e poi si verifica che non esista un sottoinsieme degli attributi della nuova _chiave_
primaria che e esso stesso una _chiave_. 


>[!example]-
>l atributo indirizzo è composto come [via:stirng,numero:int,citta:string]
>applicando la trasformazione si ottiene ![[IMG_1057.jpeg]]