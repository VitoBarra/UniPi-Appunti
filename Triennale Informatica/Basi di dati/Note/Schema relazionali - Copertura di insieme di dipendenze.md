---
Course: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# Schema relazionali - Copertura di insieme di dipendenze
---
per operare con gli [[Insiemi Matematici|insiemi]] di [[Schemi relazionali - Dipendenze funzionali|dipendenze funzionali]] conviene trasformarli in un insieme _minimo_ 

#### Copertura (Definizione)
_siano_ $F,G$ insiemi di _dipendenze per gli attributi_ $T$ _se_ $F^+ = G^+$ ovvero le [[Schema relazionali - Chiusura di Insiemi di dipendenze|chiusure]] coincidono
_allora_ $F,G$ si dicono _equivalenti_ indicato con $F \equiv G$ e sono l uno una __copertura__ del altro



#### Copertura canonica 
_sia_ $F$ un insieme di _dipendenze funzionali_

##### Dipendenza elementare
_sia_ $X \rightarrow Y$ una _dipendenza funzionale_
_se_ l insieme $Y$ è composto da un solo elemento
_allora_ $X \rightarrow Y$ è chiamata _dipendenza elementare_

##### Attributo estraneo
_sia_ 
- $X \rightarrow Y \in F$ un insieme di _[[Schemi relazionali - Dipendenze funzionali|dipendenze funzionali]]_
- $A \in X$ un _attributo_ 
_se_   $(F-\{ X \rightarrow Y \} \cup \{ X-\{A\} \rightarrow Y \}) \equiv F$  
_allora_ $A$ è detto _attributo estraneo_

##### Dipendenza ridondante
_sia_ $F$ un insieme di _[[Schemi relazionali - Dipendenze funzionali|dipendenze funzionali]]_
_se_ $(F-\{ X \rightarrow Y \}) \equiv F$
_allora_ $X \rightarrow Y$ è una _dipendenza ridondante_


##### Copertura canonica (Definizione)
nu _insieme di dipendenze_ $F$ è una _copertura canonica_
_se_
- ogni parte destra di una dipendenza ha _un unico attributo_ (Dipendenza elementare)
- le _dipendenze_ non contengono _attributi estranei_
- non ci sono _dipendenze ridondanti_ 

> [!nota]
> _Esiste sempre_ ma non necessariamente è _unica_

#### Teorema di esistenza
_per ogni_ insieme di dipendenze $F$ esiste una _copertura canonica_


#### Algoritmo per trovare coperture canoniche
Il _teorema di esistenza della copertura canonica_ viene dimostrato con il seguente algoritmo che calcola la copertura canonica.
Assumendo che ogni dipendenza come Elementare siccome e' semplice fare la trasformazione 
```pseudo
	\begin{algorithm}
	\caption{calcolo copertura canonica}
	\begin{algorithmic}
	\Function{TravaCoperturaCanonica}{F}
	\State G=F
	\For{$\boldsymbol{each}\  X \rightarrow Y \in G$}
	\State Z =X
	\For{$\boldsymbol{each} \ A \in X$}
		\If{$Y \subseteq [Z- \{A\}]^+_F$}
		 \State $Z = Z - \{A\}$
		 \EndIf
	 \EndFor
	 \State $G=(G-\{X \rightarrow Y\})\cup \{Z \rightarrow Y\}$
	 \EndFor
	\For{$\boldsymbol{each}\ f \in G$}
		\If{$f \in (G-\{f\})^+$}
		\State $G=G-\{f\}$
		\EndIf
	\EndFor
\EndFunction
	\end{algorithmic}
	\end{algorithm}
```
L algoritmo prima elimina gli _attributi estranei_ e poi elimina le _dipendenze ridondanti_, è importante farlo in quest ordine siccome se non si eliminassero prima gli _attributi estranei_ delle _dipendenze ridondanti_ potrebbero non essere riconosciute

si osservi che 
- $Y \subseteq [Z-\{ A \}]_{F}^+$ va fatto rispetto ad $F$ siccome la _dipendenza con attributo estraneo_ che vogliamo _eliminare_ potrebbe essere usata per dimostrare che $Z-\{ A \} \rightarrow Y$
- $f \in (G-\{ f \})^+$ va fatta _togliendo_ $f$ altrimenti sarebbe _banalmente verificata_

##### Calcolo complessita
la [[Complessita|complessita]] del _algoritmo_ è calcolata come segue
_sia_
- $|T|=a$ il numero di _[[Modello dati - Modello Relazionale|attributi]]_
- $|F|=p$ il numero di _dipendenze funzionali_

per l eliminazione degli _attributi estranei_ e delle _dipendenze ridondanti_ vengono calcolate la [[Schema relazionali - Chiusura di Insiemi di dipendenze#Algoritmo di chiusura lenta|chiusura degli attributi]] e questa ha complessità $O(ap\cdot\min(a,p))$ 

per la verifica di $Y \subseteq [X-A]^+_{F}$ si usa un [[Algoritmi|algoritmo]] di _complessità_ $O(ap)$

_quindi_ la _[[Complessita|complessita]]_ totale è $O(a^2p^2)$ 




#### Insieme di Dipendenza Minimo (Definizione)
_sia_ $F$ un insieme di [[Schemi relazionali - Dipendenze funzionali|dipendenze funzionali]]
_se_ ha meno dipendenze di _ogni alto_ insieme _equivalente_
_allora_ $F$ è un _insieme di dipendenze minimo_


#### Insieme di Dipendenza Ottimo (Definizione)
_sia_ $F$ un insieme di [[Schemi relazionali - Dipendenze funzionali|dipendenze funzionali]]
_se_ ha meno _simboli di attributi_ di _ogni alto_ insieme _equivalente_
_allora_ $F$ è un _insieme di dipendenze ottimo_
