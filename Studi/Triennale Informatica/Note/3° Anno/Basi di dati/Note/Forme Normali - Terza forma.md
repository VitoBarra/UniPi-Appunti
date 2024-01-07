---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Forme Normali - Terza forma
---
#### Terza Forme normale 
la _terza forma normale_ è un criterio per qualità per la rimozione delle anomalie 
la _terza forma normale_ è meno restrittiva della [[Forme Normali - Boyce-Codd|BCNF]]

la _terza forma normale_ preserva i [[Schemi Relazionali - Decomposizione di schemi|dati e le dipendenze]] ed è calcolabile in tempo polinomiale, Ma può mantenere certe _anomalie_

##### Terza forma normale (Definizione)
_sia_
- $R \langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
_se e solo se_ $\forall X \to A \in F^+$ se $X$ è [[Modello Relazionale - Chiavi|superchiave]] o è [[Modello Relazionale - Chiavi#Attributo primo (Definizione)|Primo]]
_allora_ $R$ è in _terza forma normale_ (3NF)


> [!note]
> questa definizione non è utilizzabile in pratica per via del _alto costo_ per calcolare la [[Schema relazionali - Copertura di insieme di dipendenze|chiusura]] di $F$

##### Teorema
_sia_
- $R \langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
_se e solo se_ $\forall X \to A_1\dots A_n \in F$   
- $\forall i. A_i \in X$ oppure 
- $X$ è [[Modello Relazionale - Chiavi|superchiave]] oppure
-  $\forall i. A_i$ è [[Modello Relazionale - Chiavi#Attributo primo (Definizione)|Primo]]
_allora_ $R$ è in _terza forma normale_ (3NF)

##### Corollario
_sia_
- $R \langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
- $F$ una [[Schema relazionali - Copertura di insieme di dipendenze|copertura canonica]]
_se e solo se_ $\forall X \to A \in F$ $X$ è [[Modello Relazionale - Chiavi|superchiave]] 
- con $X \to A$ un _[[Schema relazionali - Copertura di insieme di dipendenze#Dipendenza elementare|dipendenza elementare]]_
_allora_ $R$ è in _terza forma normale_ (3NF)


##### Proposizione
il problema di decidere se uno _schema di relazione_ è in _3NF_ è [[Classi di Complessita|NP-Completo]]

>[!note]
>questo viene dal fatto che decidere se un _attributo_ è primo è NP-complesto

#### Normalizzazione in forma 3NF
Un algoritmo per trasformare uno schema $R$ in uno schema in _forma normale 3NF_ si basa sulla seguente idea

dato un insieme di attributi $T$ è un [[Schema relazionali - Copertura di insieme di dipendenze|copertura canonica]] $G$ si [[partizione|partizione]] $G$ in gruppi $G_i$ tali che tutte le dipendenza in $G_i$ hanno la stessa parte sinistra
ogni $G_i$ da origine ad una relazione composta da tutti gli attributi che appaiono, e come [[Modello Relazionale - Chiavi|chiave]] (detta chiave _sintetizzata_ ) si sceglie la parte _sinistra comune_


un _algoritmo intuitivo_ chiamato _algoritmo di sintesi_ segue come
1. Trova una copertura canonica $G$ di $F$ e poni $\rho= \{  \}$
2. sostituisci in $G$ ogni insieme $X \to A_1,\dots,X\to A_h$ di dipendenze con lo stesso determinante, con la dipendenze $X \to A_1\dots A_h$
3. per ogni [[Schemi relazionali - Dipendenze funzionali|dipendenza]] $X \to Y \in G$ metti uno schema con attributi $XY$ in $\rho$
4. _Elimina_ da $\rho$ _ogni schema_ che sia contenuto in un altro schema di $\rho$ 
5. Se la decomposizione non contiene alcuno schema i cui attributi costituiscano una [[Modello Relazionale - Chiavi|superchiave]] per $R$ , aggiungi ad essa lo schema con attribuiti $W$ con $W$ una chiave di $R$


La _complessità_ del algoritmo dipende da quella del calcolo della _[[Schema relazionali - Copertura di insieme di dipendenze|copertura canonica]]_ pari a $O(a^2p^2)$


##### Teorema
_Sia_ $R\langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]_
_allora_ l _algoritmo di sintesi_ produce una _decomposizione_ $\rho=\{ S_i \}_{i=1,\dots,n}$ che preserva [[Schemi Relazionali - Decomposizione di schemi|dati e dipendenze]]

_Dimostrazione_:
l _algoritmo_ produce una decomposizione perché tutti gli attribuiti di $T$ appartengono allo _schema generato_, se ci sono attributi che non partecipano a nessuna dipendenza questi fanno parte di ogni chiave di $R$, per ciò compaiono nella relazione gita al passo 5
la _decomposizione_ preserva _le dipendenza_ perché per ogni dipendenza $X\to A_i \in G$ esiste uno schema che contiene $XA_i$. 
la _decomposizione_ preserva i dati poiché grazie al passo $5$, soddisfa la condizione espressa dal[[Schemi Relazionali - Decomposizione di schemi#Teorema|teorema di mantenimento dei dati]]



##### Teorema
_Sia_ $R\langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]_
_allora_ l _algoritmo di sintesi_ produce una _decomposizione_ $\rho=\{ S_i \}_{i=1,\dots,n}$ che è in _terza forma normale_

_dimostrazione_:
Supponiamo, per assurdo, che nella decomposizione ci sia uno schema $S$ non in 3NF, con attributi $XA_1\cdots A_h$, dove $X$ e la “_chiave sintetizzata_”. 
$X$ e una chiave di $S$
$X$ implica tutti gli altri attributi perché $\forall i.X \to A_i\in G$ , e non contiene _[[Schema relazionali - Copertura di insieme di dipendenze#Dipendenza ridondante|attributi ridondanti]]_ perché altrimenti  $G$ non sarebbe una _copertura canonica_.
Poiché $S$ non e in _3NF_, esiste una dipendenza  $V \to C \in (\pi_S(G))^+$, e quindi in $G^+$, in cui $V$ non e una _[[Modello Relazionale - Chiavi|superchiave]]_ di $S$, $C$ non e primo in  $S$ e $C \not\in V$. 
Poiché $X$ e una _chiave_ di  $S$, si ha che $C\not \in  X$ e quindi $C = A_i$ per qualche $i$. 
cercando di [[Tipi di dimostrazione|mostrare per assurdo]] Si prendono in esame due casi, 
$V \subset X$ :
allora l’_esistenza_ in $G$ della dipendenza $X \to A_i$ è in _contraddizione_  col fatto che $G$ e una _copertura canonica_.

$V \not\subset X$:
allora $V = YW$ per qualche $Y \subset X$ e $W \subseteq A_1 \cdots A_{i−1}A_{i+1} \cdots A_h$, con $W \not= \emptyset$.
Sappiamo che la dipendenza $X \to A_i$ appartiene alla [[Schema relazionali - Copertura di insieme di dipendenze|copertura canonica]]; 

raggiungiamo ora l’_assurdo_ dimostrando invece che essa e ridondante e quindi può essere derivata dall’insieme  $G' = G - {X \to A_i }$.

 mostriamo che $G' \vdash X \to YW$ e $G' \vdash YW \to A_i$ 

$G' \vdash X \to YW$, segue dal fatto che $Y \subseteq X$, mentre $W$ contiene solo attributi $A_j$ con $j \not= i$, e le dipendenze $X \to A_j (j \not= i)$ appartengono a $G'$

$G' \vdash YW \to A_i$ viene dal fatto che $G \vdash X \to S$ mentre $G \not \vdash YW \to S (YW = V$ non è una _superchiave_ per $S)$, si ha che $X \not\subseteq V^+_G$ ; 
quindi $V^+_{G'} = V ^+_G$ , poichè nel calcolo della  [[Schema relazionali - Chiusura rispetto gli attributi|chiusura]] di $V$ in G la dipendenza $X \to A_i$ non interviene.
Avendo supposto $G  \vdash YW \to A_i$ , cio implica che  $G' \vdash YW \to A_i$
