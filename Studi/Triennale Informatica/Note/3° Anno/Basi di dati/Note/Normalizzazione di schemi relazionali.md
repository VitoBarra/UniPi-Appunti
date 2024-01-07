---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Normalizzazione di schemi relazionali
---
lo [[Progettazione DB - Progettazione Logica Relazionale|schema relazionale]] è semplice siccome si basa al concetto semplice di [[Relazioni tra insiemi|relazione tra insiemi]] ma per ogni relazione ci sono diverse rappresentazioni valide e quindi uno dei problemi e la _scelta_ di questa rappresentazione.
Ci sono vari parametri su cui basare la scelta tra cui il _costo delle operazioni_ e la presenza o Assenza di _anomalie_

#### Teoria della normalizazione
per operare una scelta si utilizza la _Teoria della normalizzazione_ che ha lo scopo di 
- Definire quando due _schemi sono equivalenti_
- Definire _criteri di bontà_ per schemi, ovvero definire formalmente cosa significa che uno schema è _migliore o peggiore_ di un altro
	- Definito come Assenza di _anomalie_
- Trovare _metodo algoritmici_ per ottenere da uno schema esistente uno altro schema _migliore ed equivalente_ 

Dalla _teoria di normalizzazione_ deriva il processo di __*normalizzazione degli schemi relazionali*__ che trasforma una _rappresentazione esistente_ in una rappresentazione in _forma normale_
una _forma normale_ è una forma _equivalente_ al originaria che assicura le buone qualità di un [[Introduzione ai Data Base|Database]], ovvero è migliore secondo la _teoria della normalizzazione_


il  _processo di normalizzazione_ tiene conto solo del eliminazione delle _anomalie_ e NON tiene conto del _costo del operazioni_  

##### Assunto della normalizzazione 
La _Teoria della Normalizzazione_ assume l esistenza di uno  _schema di relazione Universale del DB_, questo assicura che _attributi_ con lo _stesso nome_ anche in _relazioni_ diverse abbiano lo stesso significato, ovvero condividono il dominio e il _fatto_ che stanno rappresentando 
Questo permette di evitare di fare _ridenominazioni_ durante le operazioni di normalizzazione e permette di usare sempre il [[Modello relazionale - Algebra Relazionale|Join Naturale]]   
###### Schema di relazione universale (Definizione)
 uno _Schema di relazione universale_ $U$ di un _database Relazionale_ ha come attributi l [[Operazioni Insiemistiche|unione]] degli attributi di tutte le [[Relazioni tra insiemi|relazioni]] del _database_
 
##### Anomalie
Le anomalie per un database sono definite come

_Ridondanza dell’informazione_: Ripetere più volte la stessa informazione e problematico sia per spreco di  memoria e per l aggiornamento delle informazioni 
_Impossibilità di rappresentare certi fatti_: questo succede quando la rappresentazione di certi _fatti_ dipende dalla rappresentazione di altri fatti

per evitare questi problemi si decompongono le relazioni in Piu relazioni diverse collegate tra loro tramite uno degli attributi.
La decomposizione è un processo delicato e va fatto con cura infatti si possono incappare nei problemi di 
_Perdita di informazioni_: questo avviene quando il [[Modello relazionale - Algebra Relazionale|Join]] tre le due relazioni prodotto della decomposizione produce più ennuple della relazione originale, Questo avviene quando viene scelta come [[Modello Relazionale - Chiavi|chiave esterna]] per una delle due relazione un _[[Aspetti della modellazione della conoscenza|Atributo]]_ che non rappresenta univocamente quel _[[Aspetti della modellazione della conoscenza|Entità]]_, ovvero che non è una [[Modello Relazionale - Chiavi|chiave valida]] per quel entità 
_Perdita di dipendenze funzionali_: questo avviene quando una [[Schemi relazionali - Dipendenze funzionali|dipendenza funzionale]] presente nella [[Relazioni tra insiemi|relazione]] originale non è più deducibile dalle due _relazioni_ di decomposizione. 

### Forme normali
Le _forme normali_ sono un criterio di valutazione su cio controllare i _schemi relazionali_ esistenti in modo da trasformarli in schemi che rispettano i criteri

#### Prima e seconda forma normale
le prime de _forme normali_ sono elencante per motivi storici siccome sono vere implicitamente con i sistemi moderni usati
1. _prima forma normale_: ogni valori dei domini di una relazione sono _atomici_
2. _seconda forma normale_: tutti gli attributi dipendono dalla [[Modello Relazionale - Chiavi|chiave primaria completa]]
3. [[Forme Normali - Terza forma|Terza forma normale]]
4. [[Forme Normali - Boyce-Codd|Forma normale Boyce-Codd]]

ognuna di questa _implica la precedente_


#### Scelta tra BCNF e 3NF
la scelta tra la _3NF_ e la _BCNF_ nel processo di normalizzazione richiede al progettista di decidere in anticipo.
La strategia di controllare prima la possibilità di una decomposizione in BCNF che preservi le dipendenze, e in caso negativo adottare la 3NF, non è praticabile dato che richiede un algoritmo con _[[Complessita|complessità]] esponenziale_.
