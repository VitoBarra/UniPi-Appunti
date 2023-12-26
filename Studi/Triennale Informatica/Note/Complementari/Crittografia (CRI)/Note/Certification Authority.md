---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Certification Authority
---
La _certification authority_ è nata per risolvere il problema della sensibilità ad attacchi [[Tipologia di attacchi ai cifrari|man in the midle]] della fragilità dei [[Cifrari a chiave Asimmetrica|sistemi a chiave assimetrica]]

una _Certification Authority_ è un _ente fidato_ che mantiene le associazioni $\langle utente ,chiave \ publica\rangle$ emettendo dei _certificati_ che ne assicurano la validità.
I certificato contengono:
+ Una indicazione del suo formato (numero di versione). 
+ Il nome della _Certification Authority_ che l’ha rilasciato. 
+  Un numero seriale che _individua univocamente_ questo certificato all’interno della _CA_ emittente. 
+  La specifica dell’algoritmo utilizzato dalla _CA_ per creare la firma elettronica, combinata con una descrizione del formato dei parametri di cui esso ha bisogno. 
+  Il periodo di validità del certificato (data di inizio e data di fine). 
+  Il _nome dell’utente_ a cui questo certificato si riferisce e una serie di informazioni a esso legate. 
+  Un’indicazione del protocollo a chiave pubblica adottato da questo utente per la cifratura e la firma: nome dell’algoritmo, suoi parametri e chiave pubblica dell’utente. 
+  Firma della _CA_ eseguita su tutte le informazioni precedenti.


Quando due utenti $U$ e $V$ vogliono comunicare basta che richiedano i rispettivi certificati alla _CA_ (_certification authority_) per essere sicuri di non subire un attacco _[[Tipologia di attacchi ai cifrari#attacco Man in the midle|man in-the-midle]]_.
Gli utenti conoscono la _chiave pubblica_ della _CA_ potranno _verificare_ l autenticità del certificato controllandone la _[[Protocolli di firma digitale|firma]]_ applicata dalla $CA$ e il periodo di _valadita_. 
Fatto ciò ogni utente potrà usare la _chiave pubblica_ che è contenuta nel certificato per comunicare con l altra utente interessato.
Siccome ogni stato ha le proprie _CA_ organizzate eventualmente ad albero possono essereci situazioni più complicate dove la _CA_ di $U$ e la _CA_ di $V$ non siano le stesse e in quel caso si fa una sequenza ci _verifiche_ a catena

In generale siccome le continue richieste alle _CA_ per ottenere la chiave pubblica di un altro utente può diventare un _collo di bottiglia_ si preferisce che ogni utente $U$ mantenga localmente un copia del proprio certificato $cert_{U}$ e una copia della _chiave publica_  $k_{CA}[pub]$ della CA che ha rilasciato il certificato e sia lui stesso a distribuirlo quando necessario, in questo modo l interazione con la _CA_ si limita solo al emissione del certificato stesso.


Un punto cruciale del _Certification Authority_ e la gestione dei certificati scaduto, le _CA_ solitamente lasciano un archivio pubblico di tutti i certificati scaduti.