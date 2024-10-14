---
Subject: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# SQL - Data Declaration Lenguage
---
Data Definition Language (DDL) è un linguaggio parte di [[Linguaggio per Database - SQL|SQL]] che gestisce la creazione degli [[Modello dati - Modello Relazionale|schemi]], delle [[Progettazione DB - Viste|viste]] e per le impostazioni dei  [[Modellazione della conoscenza|vincoli di integrita]], questo serve quindi a definire lo [[Progettazione DB - Progettazione Logica Relazionale|schema logico]] del [[Introduzione ai Data Base|DataBase]]

in particolare abbiamo che SQL e' anche

Un linguaggio per la definizione di basi di dati (Data-definition language (DDL))
 - CREATE SCHEMA Nome AUTHORIZATION Utente 
 - CREATE TABLE o VIEW, con vincoli 
 - CREATE INDEX 
 - CREATE PROCEDURE 
 - CREATE TRIGGER 
Un linguaggio per stabilire controlli sull'uso dei dati: GRANT 
Un linguaggio per modificare i dati.


### Creazioni Tabelle
Le tabelle (corrispondenti alle [[Relazioni tra insiemi|relazioni]] dell‘[[Modello relazionale - Algebra Relazionale|algebra relazionale]]) vengono definite in SQL mediante l‘Istruzione __CREATE TABLE__. Questa istruzione  
- definisce uno schema di relazione e ne crea un’istanza vuota 
- specifica attributi, domini e vincoli

 a __CREATE TABLE__ segue un nome che la caratterizza, e dalla lista delle colonne (attributi), di cui si specificano le caratteristiche. Alla fine si possono anche specificare eventuali vincoli di tabella

 Una volta creata, la tabella è pronta per l’inserimento dei dati che dovranno soddisfare i vincoli imposti.

La visualizzazione dello schema di una tabella, dopo che è stata creata, può essere ottenuta mediante il comando  __DESCRIBE__.

la sintassi della create e' del tipo
```SQL
 CREATE TABLE Nome 
 ( 
   Attributo Tipo [Default] [VincoloAttributo],
   ...,
   Attributo Tipo [Default] [VincoloAttributo],
   VincoloTabella
 ) 
 ```
dove vale che Default := DEFAULT {valore | null | username}

##### Tipi
I tipi più comuni per i valori degli attributi sono: 
- __CHAR__(n) per stringhe di caratteri di lunghezza fissa n; 
- __VARCHAR__(n) per stringhe di caratteri di lunghezza variabile di al massimo n caratteri; 
- __INTEGER__ per interi con la dimensione uguale alla parola di memoria standard dell’elaboratore; 
- __REAL__ per numeri reali con dimensione uguale alla parola di memoria standard dell’elaboratore; 
- __NUMBER__(p,s) per numeri con p cifre, di cui s decimali; 
- __FLOAT__(p) per numeri binari in virgola mobile, con almeno p cifre significative; 
- __DATE__ per valori che rappresentano istanti di tempo (in alcuni sistemi, come Oracle), oppure solo date (e quindi insieme ad un tipo TIME per indicare ora, minuti e secondi).



##### Operazioni di eliminazione e modifica
il comando __DROP__ elimina cio che e' stato creato con il comando __CREATE__
Il comando __ALTER__ lo modifica

Nuovi attributi si possono aggiungere con: 
__ALTER TABLE__ Nome __ADD COLUMN__ NuovoAttr Tipo


Con il comando ALTER TABLE è possibile (standard SQL): 
1. Aggiungere una colonna (__ADD \[COLUMN\]__) 
2. Eliminare una colonna (__DROP \[COLUMN\]__) 
3. Modificare la colonna (__MODIFY__) 
4. Aggiungere l’assegnazione di valori di default (__SET DEFAULT__)
5. Eliminare l’assegnazione di valori di default (__DROP DEFAULT__) 
6. Aggiungere vincoli di tabella (__ADD CONSTRAINT__) 
7. Eliminare vincoli di tabella (__DROP CONSTRAINT__)
8. Altre opzioni sono possibili nei linguaggi specifici (vedi manuali)


###### Colonne
per aggiungere le colonne si usa il comando:
```SQL
ALTER TABLE nome_tabella 
ADD [COLUMN] nome_col tipo_col default_col vincolo_col
```
In mancanza di altre specifiche, la nuova colonna viene inserita come ultima colonna della tabella.
Altrimenti è possibile dare questa specifica:
```SQL
ALTER TABLE nome_tabella 
ADD COLUMN {FIRST/AFTER<nome_colonna>} nome_col tipo_col default_col vincolo_col
```
dove 
- FIRST permette di aggiungerla come prima colonna
- AFTER colonna subito dopo la colonna indicata

Si può aggiungere una colonna in qualsiasi momento se non viene specificato __NOT NULL__

per eliminare le colonne si usa il comando
```SQL
ALTER TABLE nome_tabella 
DROP COLUMN nome_colonna {RESTRICT/CASCADE} 
```
dove le opzioni RESTRICT/CASCADE sono alternative ed è obbligatorio specificare l’una o l’altra 
- _RESTRICT_: se un’altra tabella si ha un vincolo di integrità referenziale con questa colonna, l’esecuzione del comando drop fallisce. 
- _CASCADE_: eliminando la colonna, vengono eliminate tutte le dipendenze logiche di altre colonne dello schema da questa.

Se si vogliono modificare le caratteristiche di una colonna dopo averla definita, si usa il comando:
```SQL
ALTER TABLE nome_tabella 
MODIFY nome colonna tipo_col default_col vincoli_col 
```


###### Valori di default
si puo impostare un valore di default ad una colonna usando il comando
```SQL
ALTER TABLE nome_tabella 
ALTER [COLUMN] nome_colonna SET DEFAULT valore_default
```

si puo eliminare un valore di default con il comando:
```SQL
ALTER TABLE nome_tabella 
ALTER [COLUMN] nome_colonna DROP DEFAULT
```



###### Vincoli
per aggiungere un vincolo di tabella, si usa il comando: 
```SQL
ALTER TABLE nome_tabella 
ADD CONSTRAINT nome_vincolo vincolo_di_tabella
```


per rimuovere un vincolo di tabella si usa il comando:
```SQL
ALTER TABLE nome_tabella 
DROP CONSTRAINT nome_vincolo{RESTRICT/CASCADE}
```
dove 
- _RESTRICT_: non si possono eliminare vincoli di unicità e di [[Modello Relazionale - Chiavi|chiave primaria]] su una colonna se esistono vincoli di [[Modello Relazionale - Chiavi|chiave esterna]] che si riferiscono a tale colonna. 
- _CASCADE_: non opera questa restrizione. 

Da notare che per eliminare un vincolo, esso deve essere definito mediante un identificatore


###### Tabelle
per eliminare una tabella si usa il comando:
```SQL
DROP TABLE name_table [RESTRICT/CASCADE]
```
dove RESTRICT/CASCADE sono opzionali
- _RESTRICT_: se la tabella è utilizzata nella definizione di altri oggetti dello schema, la sua eliminazione viene impedita. 
- _CASCADE_: vengono eliminate tutte le dipendenze degli altri oggetti dello schema da questa tabella

#### Vincoli
I [[Modellazione della conoscenza|vincoli di integrità]] consentono di limitare i valori ammissibili per una determinata colonna della tabella in base a specifici criteri. 

##### Vincoli intrarelazionali
I vincoli di integrità intrarelazionali non fanno riferimento ad altre relazioni e sono: 
- NOT NULL 
- UNIQUE definisce chiavi 
- PRIMARY KEY: chiave primaria (una sola, implica NOT NULL) 
- CHECK


###### Vincolo NOT NULL
ogni attributo che ha questo vincolo non puo essere __NULL__

###### Vincolo di unicità
Il vincolo __unique__ Può essere espresso in due modi: 
- _Vincolo di tabella_: direttamente nella definizione di un attributo, se si riferisce solo al attributo che sta venendo definito
- _Vincolo di di riga_: come vincolo separato, usato quando si applica ad un insieme di attributi 


Il vincolo __unique__ utilizzato nella definizione dell’attributo significa che 
- non ci devono essere due valori uguali in quella colonna.

> [!tip]
> E quindi vale anche che e’ una [[Modello Relazionale - Chiavi|chiave]] della [[Modello dati - Modello Relazionale|relazione]], ma non una [[Modello Relazionale - Chiavi|chiave primaria]]

Il vincolo __unique__ può anche essere riferito su insiemi di attributi.
- non ci devono essere due righe che hanno quel insieme di attributi uguali 
In questo caso il vincolo viene dichiarato dopo aver dichiarato tutte le colonne mediante un vincolo di tabella, utilizzando il comando $$UNIQUE (lista\_  attributi)$$


###### Vincolo di chiave primaria
ll vincolo __primary key__ Può essere espresso in due modi: 
- _Vincolo di tabella_: direttamente nella definizione di un attributo, se si riferisce solo al attributo che sta venendo definito
- _Vincolo di di riga_: come vincolo separato, usato quando si applica ad un insieme di attributi 



Il vincolo __primary key__ utilizzato nella definizione dell’attributo significa che 
- per quel attributo deve valere il vincolo __UNIQUE__ e __NOT NULL__


Il vincolo __primary key__ può anche essere riferito su insiemi di attributi.
-  per quel insieme di attributi deve valere il vincolo __UNIQUE__ e __NOT NULL__
In questo caso il vincolo viene dichiarato dopo aver dichiarato tutte le colonne mediante un vincolo di tabella, utilizzando il comando $$PRIMARY \ KEY (lista\_attributi)$$
La __[[Modello Relazionale - Chiavi|primary key]]__ serve ad indentificare la tabella univocamente e' verra poi usata nel vincolo di __FOREIN KEY__ (Chiave esterna)


###### Vincolo CHECK
ll vincolo __CHECK__ Può essere espresso in due modi: 
- _Vincolo di tabella_: direttamente nella definizione di un attributo, se si riferisce solo al attributo che sta venendo definito
- _Vincolo di di riga_: come vincolo separato, usato quando si applica ad un insieme di attributi 

Il vincolo __CHECK__ deve essere una espressione booleana che coinvolge uno o piu attributi ed è valutata usando i valori della colonna che vengono inseriti o aggiornati 



##### Vincoli interrelazionali
I vincoli interrelazionali sono quei vincoli che vengono imposti quando gli attributi di due diverse tabelle devono essere messi in relazione. 
Questo è fatto per soddisfare l‘esigenza di un database di non essere ridondante e di avere i dati sincronizzati. 

Se due tabelle gestiscono gli stessi dati, è bene che di essi non ce ne siano più copie, sia allo scopo di non occupare troppa memoria, sia affinché le modifiche fatte su dati uguali utilizzati da due tabelle siano coerenti.


###### REFERENCES e FOREIGN KEY
ll vincolo __REFERENCES__ e __FOREIGN KEY__ Può essere espresso in due modi: 
- direttamente nella definizione di un attributo, se si riferisce solo al attributo che sta venendo definito
	- Si usa solo __REFERENCES__
- come vincolo separato, usato quando si applica ad un insieme di attributi
	- si usa __FOREIGN KEY__(nome_attributi) __REFERENCE__ tabella(AtributiDellaTabella)  


Questi sono vincoli di __integrità referenziale__, il che significa che gli attributi con questi vincoli devono avare valori che si devono riferire ad una altra tabella e quindi deve identificare una altra riga che deve esistere.

In pratica non si possono mettere valori che riferiscono chiavi che non sono nel DB





#### Relazioni alla violazione  del vincoli di Foreign key
Alla creazione di un __vincolo foreign key__ in una tabella si può specificare l’azione da intraprendere quando delle righe nella tabella riferita vengono cancellate o modificate. 
Le azioni da intraprendere si posso specificare usando i comandi
- __ON DELETE__: per alla cancellazione
- __ON UPDATE__: per alla modifica

le azioni possibili sono:
- CASCADE: 
	- __ON DELETE__: Cancella tutte le righe dipendenti dalla tabella quando la corrispondente riga è cancellate dalla tabella riferita.
	- __ON UPDATE__ : Le righe della tabella referente vengono aggiornati al nuovo valore della riga sulla tabella riferita 
- SET NULL: Assegna NULL ai valori della colonna referente quando la riga corrispondente viene cancellata o modificata nella tabella riferita. 
- SET DEFAULT: Assegna il valore di Default ai valori della colonna referente quando la riga corrispondente viene cancellata o modificata nella tabella riferita. 
- NO ACTION: Impedisci delete, o la modifica (se viola il vincolo referenziale)
	- Questa è l’azione che viene attivata per default. 


![[Pasted image 20240112192555.png]]


