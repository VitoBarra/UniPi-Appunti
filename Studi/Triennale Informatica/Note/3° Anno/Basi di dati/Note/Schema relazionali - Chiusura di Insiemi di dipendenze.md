---
Subject: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# Schema relazionali - Chiusura di Insiemi di dipendenze
---

#### Chiusura di un insieme di dipendenze (Definizione)
_sia_
- $R \langle T,F\rangle$ un _[[Modello dati - Modello Relazionale|schema relazionale]]_
- $F$ un insieme di [[Schemi relazionali - Dipendenze funzionali|dipendenze funzionli]]
_allora_ la _chiusura di_ $F$ è $$F^+=\{ X \rightarrow Y \mid F \vdash X \rightarrow Y \}$$ovvero è l [[Insiemi Matematici|insieme]] di tutte le _dipendenze funzionali_ [[Schemi relazionali - Dipendenze funzionali derivate|derivabili]] da $F$ 


### Problema di inclusione
un problema comune è decidere se una data _[[Schemi relazionali - Dipendenze funzionali|dipendenza funzionale]]_ $X \rightarrow Y$ appartiene alla chiusura $F^+$ detto _Problema di inclusione_

#### Algoritmo esaustivo 
un _Algoritmo Esaustivo_ è quello di applicare ad $F$ esaustivamente gli [[Schema relazionali - Assiomi di Armstrong|Assiomi di Armstrong]], questo è _completo e corretto_ ma molto lento infatti ha [[Complessita|complessita]] esponenziale nel numero degli attributi dello [[Modello dati - Modello Relazionale|schema relazionale]]

Infatti 
_sia_ 
- la [[Cardinalità di un insieme|cardinalita]] di $|T|=a$ 
_allora_ il numero di _Dipendenze banali_ $T \rightarrow X$ con $X \subseteq T$ non vuoto in $F^+$ è  $2^{a}-1$, questo viene dalla conto della _presenza-assenza degli elementi_


#### Algoritmo di chiusura lenta
Un algoritmo più _veloce di quello esaustivo_ è formulabile grazie al [[Schema relazionali - Chiusura rispetto gli attributi#Teorema|teorema di Inclusione nella chiusure degli attributi]] , Questo ci dice che $X \rightarrow Y \in F^+ \iff Y \subseteq X^+_{F}$   e quindi si può cercare direttamente la seconda parte del _se e solo se_

e quindi l algoritmo segue come:
```pseudo
\begin{algorithm} 
\caption{problema di inclusione}
\begin{algorithmic}
\Function{ChiusuraLenta}{F,X}
\State $X^+ :=X$
\While{$X^+$ è cambiato}
	\For {$\boldsymbol{each} \ W \rightarrow V \in F$ }
	\If{$W \subseteq X^+\  \boldsymbol{and}\ V \not \subseteq X^+$}
	\State $X^+:=X^+ \cup V$
	\EndIf
	\EndFor
\EndWhile
\Return $X^+$
\EndFunction
\end{algorithmic}
\end{algorithm}
```
##### Teorema
L’algoritmo _Chiusura lenta_ è _corretto_. 

###### _Dimostrazione_
_Terminazione_
	Ad ogni iterazione si aggiunge qualche attributo a $XPIU$ oppure si _termina_.
	siccome il numero degli attributi è _finito_ l’algoritmo non può _ciclare indefinitamente_.
_Correttezza_: c è bisogno che al termine del programma  $XPIU = X^+$, per mostrare ciò basa  dimostra che $XPIU \subseteq X^+$ e $X^+\subseteq XPIU$.

 $(XPIU \subseteq X^+)$:
 _sia_ $j$ il numero di interazioni
 Si vuole dimostrare che $XPIU^j \subseteq  X^+ \ \forall j$. 
si procede per [[Tipi di dimostrazione#Dimostrazione per induzione|induzione]]  
   
- (_caso base_): $j = 0$ 
	- l’affermazione è ovvia  essendo $XPIU^0 = X \subseteq X^+$ _per [[Schema relazionali - Assiomi di Armstrong|riflessività]]_.
- (_l’ipotesi induttiva_):  $XPIU^j \subseteq X^+$ 
 si _dimostra_ che che $XPIU^{j+1} \subseteq X^+$ 
_Sia_ $A$ un attributo aggiunto alla $j + 1$-esima iterazione. 
Per come e stato definito l’algoritmo si ha che 
- $A \in V$
- $W \rightarrow V \in  F$
- $W \subseteq XPIU^j$
 Per l’ _ipotesi induttiva_ vale $W \subseteq XPIU^j\subseteq X^+$, e  da questo usando il [[Schema relazionali - Chiusura rispetto gli attributi|Teorema di chiusura rispetto a gli attributi]] si ha che $X \rightarrow W$; 
per [[Schema relazionali - Assiomi di Armstrong|transitivita]] $X \rightarrow V \implies X \rightarrow A$. 
_Pertanto_ $A \in  X^+$ e quindi  $A \in XPIU^{j+1} \subseteq X^+$


$(X^+ \subseteq XPIU)$
osservando che in _generale vale_ $V \subseteq W \implies V^+\subseteq W^+$ 
Possiamo dire che  $X \subseteq XPIU \implies X^+\subseteq XPIU^+$
e allora basta _dimostrare_ che $XPIU^+ \subseteq XPIU$, ovvero che $A \notin  XPIU \implies A \notin XPIU^+$ 
cioè esiste un’istanza valida $r$ di $R$ che non soddisfa $XPIU \rightarrow A$. 
Si costruisce una relazione
$r = \{t, t’\}$ di due _ennuple_ distinte che dipendono dal risultato dell’algoritmo 
_ponendo_ 
- $t[A] = t’[A]$ per ogni $A \in  XPIU$ 
- $t[B] \not= t’[B]$ per ogni $B \in T−XPIU$
_Supponiamo_ di aver dimostrato che $r$ soddisfa ogni dipendenza in $F$;
Si dimostra che $r$ non soddisfa $XPIU \rightarrow A$
- $t$ e $t’$ coincidono su $XPIU$ per _costruzione_
- mentre _non coincidono_ su $A$ perchè per ipotesi  $A \notin XPIU$.
bisogna provare che $r$ _soddisfa_ ogni dipendenza in $F$. 

_Sia_ $W \rightarrow V$ una dipendenza di $F$ 

_Se_ $W \not\subseteq XPIU$
	_allora_ $t[W] \not= t’[W]$, ed $r$ soddisfa ovviamente la dipendenza. 

_Se_ $W \subseteq XPIU$, 
	_allora_  $V \subseteq XPIU$ per _costruzione del algoritmo_ 
	questo implica $V \subseteq XPIU \implies  t[V] = t’[V]$ e quindi $r$ soddisfa la [[Schemi relazionali - Dipendenze funzionali|dipendenza]] 


##### Analisi della complessità
_Sia_ 
- $|T|=a$ il _numero_ degli attributi
- $|F|=p$ il _numero_ delle [[Schemi relazionali - Dipendenze funzionali|dipendenze funzionali]]
Il __ciclo while__ viene eseguito 
- _Al più_ $p$ volte siccome ogni dipendenza funzionale da il suo contributo alla chiusura _al più_ una volta
- _Al più_ $a$ volte siccome si possono aggiungere _al più_ $a$ attributi.
risultando in esecuzione $O(min(a,p))$

Per ogni ciclo While, il __ciclo interno for__ viene eseguito al più $p$ volte e ogni volta si controllano _due inclusioni di [[Insiemi Matematici|insiemi]]_.
il test di inclusione _tra insiemi ordinati_ di $a$ elementi ha una [[Complessita|complessità]] di tempo $O(a)$
e quindi la complessità del ciclo interno è $O(pa)$

quindi in totale l’algoritmo _Chiusura lenta_ ha [[Complessita|complessità]] di tempo, nel caso peggiore $O(ap \cdot min(a, p))$.


#### Algoritmo di chiusura veloce
Con lo dovute [[Strutture Dati|struttura dati]] si può scrivere un algoritmo di _chiusura veloce_ con [[Complessita|complessità]] in tempo $O(ap)$ 