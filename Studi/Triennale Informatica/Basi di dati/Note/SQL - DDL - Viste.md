---
Course: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# SQL - DDL - Viste
---
Le __Viste Logiche__ o __Viste__ o __View__ di un [[Introduzione ai Data Base|database]]  [[Modello dati - Modello Relazionale|relazionale]] sono definibili con utilizzando il linguaggio [[Linguaggio per Database - SQL|SQL]]  
Sono definite come __tabelle virtuali__ ovvero aggregazioni dei dati contenuti nelle tabelle “__fisiche__”, 
le __tabelle virtuali__ sono chiamate in questo modo perché non sono fisicamente memorizate ma il [[Database Managment System (DBMS)|DBMS]] conserva solo la [[SQL - Data Manipulation Lenguage|query]] che la definisce nel __[[Architettura di un DBMS|catalogo]]__, eseguire questa query ogni volta che la Vista vera usata

 Le viste contengono gli stessi dati delle tabelle fisiche ma ne forniscono una diversa visione, dinamicamente aggiornata
 La vista appare all’utente come una __normale tabella__, in cui può effettuare interrogazioni e effettuare modifiche ai dati in accordo ai [[SQL - Controllo degli accessi|privilegi che possiede]]


Le viste sono utili per
- semplificano la rappresentazione dei dati. 
	- Oltre ad assegnare un nome alla vista, la sintassi dell’istruzione CREATE VIEW consente di cambiare i nomi delle colonne 
- scrivere piu agilmente query molto complesse 
Le viste consentono di proteggere i database: le view ad accesso limitato possono essere utilizzate per controllare le informazioni alle quali accede un certo utente del database

 Le viste consentono inoltre di convertire le unità di misura e creare nuovi formati


le Viste hanno alcune limitazioni
- non è possibile utilizzare gli operatori booleani UNION, INTERSECT ed EXCEPT; 
	- INTERSECT e EXCEPT possono essere realizzati con delle SELECT mentre l UNION no
- Non è possibile utilizzare la clausola __[[SQL - Data Manipulation Lenguage#Order By|ORDER BY]]__



#### Operazioni Viste

Per creare una vista si usa il comando:
```SQL
CREATE VIEW NomeVista [ ( ListaAttributi ) ] AS SelectSQL [ with [ local | cascaded ] check option ]
```
I nomi delle colonne indicati nella lista attributi sono i nomi assegnati alle colonne della vista, che corrispondono ordinatamente alle colonne elencate nella SELECT. 
Se questi non sono specificati, le colonne della vista assumono gli stessi nomi di quelli della/e tabella/e a cui si riferisce.



in generale la struttura di una VIEW non e' modificabile infatti se una vista è definita su una subquery Select * From T1 
E in seguito alla tabella T1 viene aggiunta una colonna questa non verrà riportata anche sulla vista, la vista conterrà sempre le stesse colonne che aveva prima dell’inserimento della nuova colonna in T1

Si possono invece Modificare se valgono le seguenti regole siccome queste assicurano una corrispondenza biunivoca fra le righe della vista e le righe della  tabella di base 
- SELECT senza DISTINCT e solo di attributi 
- FROM una sola tabella modificabile 
- WHERE senza SottoSelect 
- GROUP BY e HAVING non sono presenti nella definizione

> [!question] 
> capire se per modificare intende la struttura o i dati


per eliminare una vista si usa il comando 
```SQL
DROP VIEW nome_view {Restrict/Cascade} 
```
dove 
- _Restrict_: la vista viene eliminata solo se non è riferita nella definizione di altri oggetti 
- _Cascade_: oltre che essere eliminata la vista, vengono eliminate tutte le dipendenza da tale vista di altre definizioni dello schema




###### Vista di gruppo
Una _vista di gruppo_ è una vista in cui una delle colonne è una funzione di [[SQL - Data Manipulation Lenguage#Agregatori|aggregazione]]. 
E'  obbligatorio assegnare un nome alla colonna della vista corrispondente alla funzione di aggregazione

E’ una vista di gruppo anche una vista che è definita in base ad una vista di gruppo


###### Aggiornamento sulla view
Le operazioni di INSERT/UPDATE/DELETE sulle VIEW non sono sempre state supportate ma ora lo sono con delle restrizioni.

Queste operazioni e hanno senso in caso si vuole dare solo un certo accesso ad un certo tipo di utente, ad esempio un utente puo poter scrivere solo una parte della riga di una tabella


nel aggiornare la vista ci si puo trovare in una situazione dove la vista e' definita con un WHERE.
Provare a fare modifiche su questo tipo di vista significherebbe fare modifiche alla tabella base senza modificcare i dati presenti sulla vista, il che significa modificare dati a cui non si ha accesso.

Per risolvere questo problema si usa l’opzione __WITH CHECK OPTION__ messa alla fine della definizione della vista
```SQL
CREATE VIEW nome_view(nome_colonne) 
AS 
SELECT ATTRIBUTI 
FROM TABELLA 
WHERE CONDIZIONE
WITH [CASCADE/LOCAL] CHECK OPTION
```
__WITH CHECK OPTION__ assicura che le operazioni di inserimento e di modifica dei dati effettuate utilizzando la vista soddisfino la clausola WHERE della subquery.

la parte opzionale CASCADE/LOCAL indica le modalità di controllo da usare in caso in cui una vista $V_1$  che ha questa opzione sia definita a partire da un altra vista $V_2$.
- _CASCADE_: Controlla che venga sodisfatto sia il WHERE  di $V_1$ che di $V_2$ indipendente dal fatto che $V_2$ abbia __WITH CHECK OPTION__
	- questa e' il comportamento di default
- _LOCAL_: Controlla che venga soddisfatto solo il WHERE di $V_1$




#### Vantaggio delle viste
generalmente uno dei requisiti per la progettazione di un database relazionale è la [[Normalizzazione di schemi relazionali|normalizzazione]] dei dati. 
la normalizzazione pero porta ad una struttura difficile da capire, con le visto questo problema si puo risolvere dato una rappresentazione dei dati piu intuitiva


Si puo usare per limitare l accesso ai dati da parte del utente a cui alcuni dati devono essere nascosti o non sono significativi


Le Viste garantiscono l indipendenza logica delle applicazioni e delle operazioni eseguite dagli utenti rispetto alla struttura logica dei dati. Ciò significa che se la vista resta uguale (cambiando eventualmente la query) è possibile poter operare modifiche allo schema senza dover apportare modifiche alle applicazioni che utilizzano il database 


  
