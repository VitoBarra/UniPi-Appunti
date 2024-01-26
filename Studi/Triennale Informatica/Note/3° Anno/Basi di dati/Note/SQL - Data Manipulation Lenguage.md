---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# SQL - Data Manipulation Lenguage
---
Il _Data Manipulation Lenguage_ è una parte del [[Linguaggio per Database - SQL|SQL]] ed è un sotto insieme di comandi che si occupa del _interrogazione_ e _modifica_ dei dati su un istanza di [[Introduzione ai Data Base|Database]] 

### Interrogazione DB
I _comandi di interrogazione_, o __QUERY__, permettono di effettuare una ricerca dei dati presenti nel database che soddisfano particolari condizioni, richieste dall’utente
e la sintassi è del tipo 
```SQL
SELECT ATTRIBUTI
FROM TABELLE
[WHERE CONFIZIONE]
```
dove $[\cdot]$ indica l opzionalita, quindi la parte WHERE conduzione è opzionale.

la semantica dei comandi è la seguente
- $SELECT$:  si specifica la “target list” ovvero la lista di attributi he vogliamo nei risultati del interrogazione
	- implementa la [[Modello relazionale - Algebra Relazionale|Proiezione]] 
- $FROM$:  Stabilisce in quali tabelle sono presenti i dati su cui ci interessa operare 
- $WHERE$: esprime le condizioni che i dati cercati devono soddisfare
	- implementa la [[Modello relazionale - Algebra Relazionale|Restrizione]] se la tabella è una
	- implementa il [[Modello relazionale - Algebra Relazionale|theta-Join]] se le tabelle sono almeno 2

alcuni operatori utilizzabili nella $WHERE$ sono
$LIKE$ : controlla che i dati di tipo _stringa_ rispecchiano certi pattern
- $\%$ indica zero o piu caratteri
- $\_$ denota un carattere
 per cercare i simboli che si usano per per le operazioni si utilizza il simboli di escape $\#$

$IN$ per selezionare righe che hanno attributi che assume valori contenuti in una lista 

$BETWEEN$ per selezionare righe che hanno attributi in un certo range 

$IS\ NULL$ per selezionare righe che hanno attributi nulli

I valori NULL rappresentano l’assenza di informazione, 
cioè: 
- Valore sconosciuto 
- Valore non disponibile 
- Attributo non applicabile 
Ciascun valore NULL è quindi considerato diverso dagli altri valori NULL 
Il risultato del confronto logico con un valore che è NULL da come output: sconosciuto (_UNKNOWN_), indicato con S

Tutti questi operatori si possono negare usando il $NOT$


### Agregatori
Le _funzioni diaggregazione_ sono funzione che aggregano tutta la tabella e ne restituiscono una con un unico valore per colonna

- $COUNT(*)$: Conta il numero di righe e ne restituisce il numero
- _$MIN_(A)$:  il minimo dei valori del attributo
- $MAX(A)$: il massimo dei valori del attributo
- $AVG(A)$: la media dei valori del attributo  
- $SUM(A)$:la Somma dei valori del attributo

In generale i valori NULLI vengono ignorati da queste funzioni
```SQL
	SELECT FAGREGAZIONE([Specifica] A1)
	FROM T
	[WHERE T.A2 OP ESP]
```

dove \[Specifica\] puo assumere i seguenti valori
- $*$ considera tutte le righe anche i _null_
- $ALL$ considera tutto tranne i _null_
- $DISTINCT$ considera solo i valori _distinti_


Non tutte le funzioni supportano tutte le specifiche infatti

- _$MIN/MAX$_: non le supportano , vale di default hanno sempre $ALL$
- $Count(*)$ : le supporta tutte e tre
- $AVR/SUM$: sopportano solo $ALL$ e $DISTINCT$

>[!warning] Errore Grave
> fare operazioni del tipo
>```SQL
>	SELECT A1, FAGREGAZIONE(A)
>	FROM T
>	[WHERE CONDIZIONE] 
>```
>perché cosi la tabella target non è omogenea e non si saprebbe a quale riga appartiene l attributo $A1$



#### Group By
Il raggruppamento si usa quando si vuole usare funzioni di _aggregazione_ non su tutta la tabella ma sulle dei gruppi nella tabella

```SQL
	SELECT FAGREGAZIONE(A1)
	FROM T1
	GROUP BY ATTRIBUTI
```

una regola importante da ricordare e che si possono mettere anche degli attributi nella select che non sono _funzioni aggreganti_ ma questi devono comparire anche nella clausola _Group by_
- Questo non é sempre vero, ci sono standard che permettono di usare  nella SELECT anche attributi che non sono nella GROUP BY se questi desumibili univocamente  


```SQL
	SELECT A1,FAGREGAZIONE(A2)
	FROM T1
	GROUP BY A1, ATRIBUTI
```


la clausola _HAVING_ si usa per fare una restrizione, Come lo _WHERE_ ma solo dopo il _GROUP BY_ e solo con _funzioni di aggregazione_
```SQL
	SELECT A1,FAGREGAZIONE1(A2)
	FROM T1
	GROUP BY A1, ATRIBUTI
	HAVING FAGREGAZIONE2(A3) OP C
	[WHERE CONDIZIONE]
```


#### Order By
è possibile dare un _ordinamento_ al risultato di una _SELECT_
```SQL
	SELECT ATTRIBUTI
	FROM T
	WHERE CONDIZIONE
	ORDER BY A [ASC/DESC],B [ASC/DESC]
```
dove $ASC$ indica ascendente e $DESC$ discendente e si può ordinare su più attributi, L ordine conta e determina l importanza, Il primo è il più importante e si va a scendere fino al ultimo






#### Join

il _[[Modello relazionale - Algebra Relazionale|cross Join]]_ che implementa un [[Prodotto Cartesiano|prodotto cartesiano]] viene fatto in SQL con i comando 
```SQL
	SELECT T1.* T2.*
	FROM T1,T2
```



L _Equi join_ (o detto solo _Join_) tra due tabelle  $T_1,T_2$ da come risultato una _terza tabella_ $T_3 \subseteq T_1\times T_2$  tale che $T_3$ contenga solo le righe devo la colonna di giunzione scelta ha gli stessi valori 

```SQL
	SELECT T1.A1 , T2.A4
	FROM T1,T2
	WHERE T1.A2=T2.A3
```

Il risultato viene mostrato solo le colonne _selezionate_ (_proiettate_) e quindi la colonna su cui si fa il Join si perde
![[IMG_1072.jpeg]]



l _inner Join_ è restituisce un risultato simile dal _equi-join_ ma la condizione può essere diversa della sola eguaglianza

```SQL
	SELECT ATTRIBUTI
	FROM T1 ,T2
	WHERE CONDIZIONE 
```


il _self Join_ è un caso di Join dove si fa il join sulla stessa tabella 
```SQL
	SELECT ATTRIBUTI
	FROM T1 AS X, T1 AS Y
	WHERE CONDIZIONE (CHE USANO X E Y)
```



la clausola _join_ in SQL si puo usare per semplificare e usare più esplicitamente i _Join_ 
```SQL
	SELECT ATTRIBUTI
	FROM T1 JOIN T2
	ON CODIZIONEJOIN
```

il _Natural Join_ implementa il _[[Modello relazionale - Algebra Relazionale|join naturale]]_ del algebra relazionale e quindi funziona come un join ma su __tutte__ le colonne uguali
```SQL
	SELECT ATTRIBUTI
	FROM T1 NATURAL JOIN T2
```
usando la clausola _using_ si può fare il _ natural join_ su di un sotto insieme delle colonne che hanno lo stesso nome

```SQL
	SELECT ATTRIBUTI
	FROM T1 NATURAL JOIN T2
	USING (A1,A2)
```



gli _outer Join_ si usano in caso di Join su colonne dove una delle due parti potrebbe non avere valori, ovvero potrebbe avere dei _null_

```SQL
	SELECT ATTRIBUTI
	FROM T1 LEFT [OUTER] JOIN T2

	SELECT ATTRIBUTI
	FROM T1 RGHT [OUTER] JOIN T2
	
	SELECT ATTRIBUTI
	FROM T1 FULL [OUTER] JOIN T2
	
```
dove rispettivamente il
- _LEFT_ preserva le colonne di sinistra con null 
- _RIGHT_ quello con le colonne di destra null 
- _FULL_ preserva entrambi le colonne 

#### SubQuery
Una _subquery_ è un comando select racchiuso tra parentesi tonde e inserito in un altra query


Le _subquery_ sono di 3 tipo
- __Scalare__: ovvero una querci che restituisce un solo valore, come ad esempi con le funzioni di __aggregazione__
- __Di colonna__: restituisce una sola colonna 
- __Di tabella__: restituisce un intera tabella


Le subquery permettono di creare query nidificate
```SQL
	SELECT ATTRIBUTI
	FROM TABELLE1
	WHERE ATTRIBUTO OP =   (SELECT ATRIBUTI
					FROM TABELLE2
					WHERE CONDIZIONE)
```
e queste si possono comporre in ogni modo, basta che si rispetti l la corretta cardinalità dei valori degli operandi dei _operatori_

Solitamente si può riscrivere un query da forma _piana_ (ovvero senza sub query) con una nidificata con subquery 
la versione nidificata è _Meno dichiarativa_ ma piu _facile da leggere_


Le regole di visibilità delle variabili sono le seguenti
- un blocco interno vede le variabili dichiarate nel suo blocco esterno
- un blocco esterno non vedere le variabili dichiarate nel blocco interno




#### Quantificatori
I quantificati in SQL sono simili ai [[Logica del primo ordine (FOL)|predicati della logica del primo ordine]] infatti ci sono i concetti di quantificatore universale e quantificatore esistenzaile


i _Quantificatori scalari_ sono:
- $ANY$: il predicato è vero se _**almeno uno** dei valori restituì_ dalla query soddisfano la condizione
- $ALL$: il predicato è vero se _**tutti** dei valori restituì_ dalla query soddisfano la condizione

e si usano come
```SQL
SELECT ATTRIBUTI
FROM TABELLE
WHERE ATTRIBUTO OP [ANY/ALL](SUBQUERY COLONNA)
```

Per usare i confronti con i quantificatori  SubQuery bisogna rispettare le seguenti regole
- la subquery deve essere subquery di colonna
- la subquery deve essere inserita dopo l _operatore di confronto quantificato_
- NON si puo fare il confronto tra due subquery 
- nella subquery non ci devono essere clausole _GROUP BY_ o _HAVING_

i _quantificatori esistenziali_ sono:
- $EXISTS$ SelectQuerty: il predicato è vero se _selectQuery_ ha almeno una ennupla

e si usano come
```SQL
SELECT ATTRIBUTI
FROM TABELLE
WHERE EXISTS(SUBQUERY TABELLA)
```

>[!note]
>I quantificatori possono essere negati con il NOT


In generale vale che si possono riscrivere tra di loro in forme equivalenti delle query con $EXISTS$ e $ANY$
in più vale che
- $=ANY$ è equivalente ad usare $IN$
- $<>ALL$ è equivalente ad usare $NOT \ \ IN$


l operatore esistenziale si può fare con 
- $EXISTS$ 
- $=ANY,<ANY,>ANY$
- _Giunzioni_

l _operatore universale_ invece si utilizza 
```SQL
SELECT ATTRIBUTI
FROM TABELLE
WHERE A <>ALL [NOT IN] (SUBQUERY)
```
dove SubQuery cerca le tabelle che ci renderebbe il _per ogni_ falso e controlla che non ci sia.

un versione alternativa è utilizzando l $NOT \ EXISTS$
```SQL
SELECT ATTRIBUTI
FROM TABELLE
WHERE NOT EXISTS(SUBQUERY)
```

con il _NOT EXISTS_ può capitare di usare una _variabile esterna_ nella __subquery__, questo per quanto sia corretto è inefficiente siccome in questo modo la subquery interna deve essere valutata una volta per ogni riga di _TABELLE_.
Si può passare ad una forma con il _NOT IN_ per portare la variabile esterna fuori dalla subquery e quindi _decorrelare_, in questo modo la subquery viene eseguita una svolta volta


#### Unione, intersezione e diffenreza

Nei database avvolte è utile utilizzare [[Operazioni Insiemistiche|operazioni insiemistiche]]

Queste operano su due tabelle _omogenee_ ovvero dello stesso tipo ovvero hanno lo stesso dominio (magari con nomi diversi)

e operazioni sono
- $UNION$: prende due tabelle e restituisce una tabella con tutte le righe della prima e tutte le righe della seconda
- $INTERSECT$:  prende due tabelle r restituisce tutte le righe comuni ad entrambi le tabelle
- $EXCEPT$ (o $MINUS$): prende due tabelle e restituisce tutte le righe che sono nella prima ma che non sono nella seconda
ed essendo [[Operazioni Insiemistiche|operazioni insiemistiche]] di default vengono ignorati i  duplicati almeno di specificare con $ALL$ che questi si vogliono


I nomi della tabella risultante dipendono dal [[Database Managment System (DBMS)|DBMS]] solitamente si usano i nomi della primo operando.
la sintassi è del tipo

```SQL
SELECT ATTRIBUTI1
FROM TABELLE1
OPERATORE_INSIEMISTICO [ALL]
SELECT ATTRIBUTI2
FROM TABELLE2
```



valore la forma equivalente 
```SQL
SELECT ATTRIBUTI1
FROM TABELLE1
EXCEPT [ALL]
SELECT ATTRIBUTI2
FROM TABELLE2


SELECT ATTRIBUTI1
FROM TABELLE1
WHERE A <>ALL [NOT IN]
(SELECT ATTRIBUTI2
FROM TABELLE2)
```




### Inserimento e Modifica Dati


L insirimento
```SQL
INSERT INTO TABELLA VALUES (V1,...,Vn)
```

L aggiornamento dei valori
```SQL
UPDATE TABELLA
SET A1=EXPRESSIONE, ..., AN=ESPRESSIONE
WHERE CONDIZIONE
```


la cancellazione
```SQL
DELETE FROM TABELLA
WHERE CONDIZIONE
```





la sintassi della select
![[Pasted image 20240113013351.png]]