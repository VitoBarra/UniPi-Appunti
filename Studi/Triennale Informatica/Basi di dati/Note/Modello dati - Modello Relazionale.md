---
Subject: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# Modello dati - Modello Relazionale
---
il _modello relazionale_ è  [[Modelli di dati|modello dati]] per la _[[Modellazione della conoscenza|Modellazione della conoscenza]]_

### Introduzione
I meccanismi per definire una [[Introduzione ai Data Base|base di dati]] con questo modello sono l'_ennupla_ e la _[[Relazioni tra insiemi|relazione]]_. 

- Un _tipo ennupla_ è un [[Insiemi Matematici|insieme]] di coppie (_attributo, tipo primitivo_), 
- Un _valore di tipo ennupla_ è un insieme di coppie (_attributo, valore_), e ogni coppia e detto anche _campo_
	- il _valore_ ha il tipo specificato nella coppia (_attributo,tipo primitiva_)

Una _relazione_ è un _[[Insiemi Matematici|insieme]] di ennuple_ con lo stesso tipo. 

nel _modello relazionale_ esiste il concetto di [[Modello Relazionale - Chiavi|chiave]]
![[IMG_1046.jpeg]]

Il vantaggio del _Modello relazionale_ oltre alla sua _intuitività_ sono le [[Insiemi Matematici|operazioni insiemistiche]] che restituiscono sempre altre [[Relazioni tra insiemi|relazioni]],  
c è anche un _operazione_ che consente di creare una _nuova relazione come giunzione_ di due relazioni

##### Confronto con modello ad oggetti
Questo modello si differenzia dal [[Modello dati - Modello ad oggetti|modello ad oggetti]], in particolare, per l'_assenza di metodi_, di _gerarchie di inclusione e di ereditarietà_, per il fatto che gli attributi di un'ennupla _devono avere un tipo primitivo_ e poiché non esiste un concetto simile all'_identità_ del modello ad oggetti due ennuple con gli stessi valori degli _attributi coincidono_ rappresentano la stessa entità.
 
 Il _Modello relazionale_ ha una semantica _insiemistica estremamente semplice_, rendendolo più facile da comprendere ed è particolarmente adatto a un _trattamento formale_, che ha consentito lo sviluppo di una teoria della progettazione di basi di dati come i processi di [[Normalizzazione di schemi relazionali|normalizzazione]] 




### Modello relazionale
Il modello relazionale su basa sul concetto di [[Relazioni tra insiemi|Relazione]] matematica ovvero un sotto insieme di un [[Prodotto Cartesiano|prodotto cartesiano]] $D_{1}\times \dots \times D_{n}$ dove $D_{i}$ è un dominio.
Gli _elementi_ della relazione dono _ennuple_ dove ogni componente è associata al suo dominio in modo _Posizionale_.
In _informatica_ si utilizza il prodotto cartesiano _etichettato_ ovvero ogni elemento specifica il dominio di appartenenza tramite un etichetta invece che tramite la posizione

#### Aspetto Intenzionale

##### Tipo ennupla (Definizione)
_sia_ 
- $T_{1},\dots,T_{n}$ dei _tipi primitivi_ (int,real,bool e string) 
- $A_{1},\dots,A_{n}$ delle etichette distinte
_allora_ un _tipo ennupla di grandi $n$_ e definita come $$(A_{1}:T_{1},\dots,A_{n}:T_{n})$$L ordine della coppie $A_{i}:T_{i}$ non conta due insiemi con le stesse coppie ma in ordine diverso sono lo stesso insieme

##### Tipo Relazione (Definizione)
_sia_ $T$ un _tipo ennupla_
_allora_ $\{ T \}$ è un _Tipo insieme di ennuple_ o _Tipo relazione_
Due _tipo relazione_ sono uguali se hanno la stesso _tipo ennupla_

##### Schema di relazione (Definizione)
uno _Schema di relazionale_ $R:\{T\}$ è una _coppia_ dove $R$ è il _nome della relazione_ è $\{T\}$ è  un _tipo relazione_

##### Schema relazionale (Definizione)
lo _schema relazionale_ è costituito da un insieme di _schemi di relazioni_ $R_{i}:\{T_{i}\}$ e da un _[[Insiemi Matematici|insieme]]_ di _vincoli di integrità_ relativi a tali schemi.

Può essere abbreviato con $R(T)$

#### Aspetto estensionale

##### Ennupla (Definizione)
_siano_ 
- $T=(A_{1}:T_{1},\dots,A_{n}:T_{n})$ un _tipo ennupla_
- $V_{1},\dots V_{n}$ una lista di _valori_ di tipo (posizionalmente) $T_{1},\dots,T_{n}$   
_allora_ un _ennupla_ e definita come $$t=(A_{1}:=V_{1},\dots A_{n}:=V_{n})$$
Due _ennuple_ sono uguali se contengono le stesse coppie $(A_{i}:V_{i})$

##### Istanza dello schema (Definizione)
_sia_ $R_{i}:\{ T_{i} \}$ uno _schema relazionale_ (o _relazione_)
_Allora_ un _instanza dello schema_ $R_{i}:\{ T_{i} \}$ è [[Insiemi Matematici|insieme]] finito di _ennuple_ $$\{ t_1,\dots t_k \}$$ con $t_{i}$ di _tipo del ennupla_ $T_i$

##### Cardinalita di una relazione (Definizione)
_sia_ $I$ un Istanza di una relazione
_allora_ la cardinalità di $I$ è il numero delle sue _ennuple_.



#### Notazione
uno _schema di relazione_, invece della
notazione $R : {(A_1 : T_1, \dots , A_n : T_n)}$, 
si userà la notazione $R(A_1 : T_1, \dots , A_n : T_n)$, o  $R(A_1, \dots , A_n)$ quando _non interessa_ evidenziare il tipo degli _attributi_.
In questo caso si assume che _attributi uguali_ in schemi di _relazione diversi_ abbiano lo _stesso tipo_

$dom(A_i)$: indica l _insieme_ dei possibili valori
del attributo $A_i$ 

$adom(A_i) \subseteq dom(A_{i})$: indica l _insieme_ di valori presi dal attributo $A_{i}$ in una _estensione_ (istanza di tutto il database) della _[[Introduzione ai Data Base|base di dati]]_



### Vincoli di integrità
Uno _schema relazionale_ è composta anche da _vincoli di integrità_ questo sono vincoli sui dati per assicurarsi che un _istanza_ sia _valida_.

La _validità di un istanza_ è un concetto _semantico_ ovvero è legata alla realtà che volgiamo rappresentare
Un istanza _valida_ rispetta la struttura della relata 

I _vincoli di integrità_ servono a modellare parte della struttura della realtà.

Esempi di vincoli:
- _NULL/not NULL_ : vincolo sulla null abilità di un _attributo_. Può capitare che un dato sia mancante o non si possa conosce in un dato momento questo si modella con un attributo che accetta _NULL_ quando questo non deve succedere si utilizza il vincolo _not NULL_
- Altri vincoli sono quelli di [[Modello Relazionale - Chiavi|chiave]]
