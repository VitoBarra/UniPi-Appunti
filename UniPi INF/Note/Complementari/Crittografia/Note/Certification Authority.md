---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Certification Authority
---
la _certification authority_ è nata per risolvere il problema della sensibilità ad attacchi [[Tipologia di attacchi ai cifrari|man in the midle]] della fragilità dei [[Cifrari a chiave Asimmetrica|sistemi a chiave assimetrica]]

in generale un attacco di questo tipo avviene seguendo la procedura:
1. $U$ richiede a $V$ la sua _chiave pubblica_
2. un utente $X$ intercetta la risposta contenente $k_{V}[pub]$ e la sostituisce con la sua _chiave pubblica_ $k_{X}[pub]$
3. Da questo momento in poi $X$ si pone costantemente in ascolto inattesa dei crittogrammi spediti da $U$ a $V$ e _cifrati mediante_ $k[pub]$. Ciascuno di questi crittogrammi viene rimosso dal canale e poi $X$ le  _decifrara_ e lo _cifrera_ di nuovo mediante $k_{V}[pub]$ e spedira il nuovo crittogramma a $V$
questo procedimento è completamente trasparente a $U$ e $V$ finche il ritardo introdotto da $X$ è abbastanza basso da essere attribuito alla rete.


una _Certification Authority_ è un ente fidato che mantiene le associazioni $\langle utente ,chiave \ publica\rangle$ emettendo dei _certificati_ che ne assicurano la validità.
I certificato contengono:
+ Una indicazione del suo formato (numero di versione). 
+ Il nome della CA che l’ha rilasciato. 
+  Un numero seriale che individua univocamente questo certificato all’interno della CA emittente. 
+  La specifica dell’algoritmo utilizzato dalla CA per creare la firma elettronica, combinata con una descrizione del formato dei parametri di cui esso ha bisogno. 
+  Il periodo di validità del certificato (data di inizio e data di fine). 
+  Il nome dell’utente a cui questo certificato si riferisce e una serie di informazioni a esso legate. 
+  Un’indicazione del protocollo a chiave pubblica adottato da questo utente per la cifratura e la firma: nome dell’algoritmo, suoi parametri e chiave pubblica dell’utente. 
+  Firma della CA eseguita su tutte le informazioni precedenti.


Quando due utenti $U$ e $V$ vogliono comunicare basta che richiedano i rispettivi certificati alla _CA_ (_certification authority_), gli utenti siccome conoscono la chiave pubblica della _CA_ potranno _verificare_ l autenticità del certificato controllandone la _[[Protocolli di firma digitale|firma]]_ e il periodo di _valadita_. Fatto ciò ogni utente potrà usare la _chiave pubblica_ che è contenuta nel certificato per comunicare.
siccome ogni stato ha le proprie _CA_ organizzate ad albero possono essereci situazioni più complicate dove la _CA_ di $U$ e la CA di $V$ non siano le stesse e in quel caso si fa una sequenza ci _verifiche_ a catena

In generale siccome le continue richieste alle _CA_ per ottenere la chiave pubblica di un altro utente può diventare un collo di bottiglia si preferisce che ogni utente $U$ mantenga localmente un copia del proprio certificato $cert_{U}$ e sia lui stesso a distribuirlo quando necessario. In questo modo l interazione con la _CA_ si limita al emissione del certificato stesso.

### Protocollo con certificato (protocollo 4)
in questo modo unendo il _messaggi cifrato_,  [[Protocolli di firma digitale|firmato]] con [[Funzioni Hash One-Way|funzioni hash]] e _Certificato_ abbiamo un protocollo  di comunicazione tra due utenti $U$ e $V$ che segue come:
_firma, cifratura e certificazione_:
	il mittente $U$ calcola $h(m)$ e genera la firma $f=\mathcal{D}(h(m),k_{U}[prv])$, calcola il crittogramma $c=\mathcal{C}(m,k_{v}[pub])$ e spedisce a $V$ la tripla $\langle cert_{U},c,f \rangle$ 
		$cert_{U}$ contiene sia la _chiave pubblica_ di $U$ che la specifica funzione hash usata.
 _Verifica del certificato_:
	 il destinatario $V$ riceve la tripla $\langle cert_{U},c,f \rangle$ e verifica l _autenticità_ di $cert_{U}$  utilizzando la chiave pubblica della _CA_
_Decifrazione e verifica della firma_:
	$V$ decifra il crittogramma $c$ mediante la sua chiave privata ottenendo $m= \mathcal{D}(c,k_{V}[prv])$; verifica l autenticità della firma apposta da $U$ su $m$ controllando che risulti $\mathcal{C}(f,k_{U}[pub])= h(m)$

Un punto cruciale del _Certification Authority_ e la gestione dei certificati scaduto, le _CA_ solitamente lasciano un archivio pubblico di tutti i certificati scaduti.