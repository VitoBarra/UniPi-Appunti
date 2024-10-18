---
Course: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# SQL - Controllo degli accessi
---
Ogni componente dello schema (risorsa) può essere protetta (tabelle, attributi, viste, domini, ecc.) 
Il possessore della risorsa (colui che la crea) assegna dei privilegi agli altri utenti 
Un utente predefinito ( \_system) rappresenta l’amministratore della base di dati ed ha completo accesso alle risorse 
Ogni privilegio è caratterizzato da: 
- la risorsa a cui si riferisce 
- l’utente che concede il privilegio 
- l’utente che riceve il privilegio 
- l’azione che viene permessa sulla risorsa 
- se il privilegio può esser trasmesso o meno ad altri utenti

Tipi di privilegi: 
- SELECT: lettura di dati 
- INSERT \[(Attributi)]: inserire record (con valori non nulli per gli attributi) 
- DELETE: cancellazione di record 
- UPDATE \[\(Attributi)]: modificare record (o solo gli attributi) 
- REFERENCES \[(Attributi)]: definire chiavi esterne in altre tabelle che riferiscono gli attributi. 
- WITH GRANT OPTION: si possono trasferire i privilegi ad altri utenti

Chi crea lo schema della BD è l'unico che può fare CREATE, ALTER e DROP 
Chi crea una tabella stabilisce i modi in cui altri possono farne uso utilizzando il comando
```SQL
GRANT <Privilegi|all pribileges> ON Oggetto TO Utenti [WITH GRANT OPTION]
```


Per revocare il privilegio:
```SQL
REVOKE Privileges ON Resource FROM Users [RESTRICT | CASCADE]
```
La revoca deve essere fatta dall’utente che aveva concesso I privilegi e le opzioni
- RESTRICT:  specifica che il comando non deve essere eseguito qualora la revoca dei privilegi all’utente comporti qualche altra revoca (dovuta ad un precedente grant option)
	- e' l operazione di default 
- CASCADE: rimuove  i permessi al utente e se questo utente e' l unico che gli ha dato il permesso anche a tutti quegli utenti a cui questo utente ha concesso quel permesso 
	- Quando si toglie un privilegio a U, lo si toglie anche a tutti coloro che lo hanno avuto solo da U.


Chi definisce una tabella o una [[SQL - DDL - Viste|VIEW]] ottiene automaticamente tutti i privilegi su di esse, ed è l’unico che può fare un DROP e può autorizzare altri ad usarla con GRANT. 
- Nel caso di viste, il "creatore" ha i privilegi che ha sulle tabelle usate nella definizione.


i permessi posso essere espressi con un [[Struttura dati - Grafo|grafo]]
![[Pasted image 20240113020330.png]]
Se un nodo N ha un arco uscente con un privilegio, allora esiste un cammino da SYSTEM a N con ogni arco etichettato dallo stesso privilegio