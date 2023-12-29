---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Dipendenze funzionali derivate - Chiusura di Insiemi di dipendenze
---

#### Chiusura di un insieme di dipendenze (Definizione)
_sia_
- $R \langle T,F\rangle$ un _[[Modello dati - Modello Relazionale|schema relazionale]]_
- $F$ un insieme di [[Schemi relazionali - Dipendenze funzionali|dipendenze funzionli]]
_allora_ la _chiusara di_ $F$ è $$F^+=\{ X \rightarrow Y \mid F \vdash X \rightarrow Y \}$$ovvero è l [[Insiemi Matematici|insieme]] di tutte le _dipendenze funzionali_ [[Schemi relazionali - Dipendenze derivate|derivabili]] da $F$ 


### Problema di inlusione
un problema comune è decidere se una data _[[Schemi relazionali - Dipendenze funzionali|dipendenza funzionale]]_ $X \rightarrow Y$ appartiene alla chiusara $F^+$ detto _Problema di inclusione_

#### Algoritmo esaustivo 
un _Algoritmo Esaustivo_ è quello di applicare ad $F$ esaustivamente gli [[Dipendenze funzionali derivate - Assiomi di Armstrong|Assiomi di Armstrong]], questo è complesto è corretto ma molto lento infatti ha [[Complessita|complessita]] esponenziale nel numero degli attributi dello [[Modello dati - Modello Relazionale|schema relazionale]]

Infatti 
_sia_ 
- la [[Cardinalità di un insieme|cardinalita]] di $|T|=a$ 
_allora_ il numero di _Dipendenze banali_ $T \rightarrow X$ con $X \subseteq T$ non vuoto in $F^+$ è  $2^{a}-1$, questo viene dalla conto della _presenza-assenza degli elementi_


#### Algoritmo di chiusura lenta
Un algoritmo piu _veloce di quello esaustivo_ è formulabile grazie al [[Dipendenze funzionali derivate - Chiusura rispetto gli attributi#Teorema|teorema di Inclusione nella chiusure degli attributi]] , Questo ci dice che $X \rightarrow Y \in F^+ \iff Y \subseteq X^+_{F}$   e quindi si puo cercare direttamente la seconda parte del _se e solo se_

e quindi l algoritmo segue come:
```pseudo
\begin{algorithm} 
\caption{Chiusura lenta}
\begin{algorithmic}
\Function{ChiusuraLenta}{F,X}
\State $X^+ :=X$
\While{$X^+$ è cambiato}
	\For {$\boldsymbol{ea} \ W \rightarrow V \in F\mid W \subseteq X^+ \land V \not \subseteq X^+$ }
	\State $X^+:=X^+ \cup V$
	\EndFor
\EndWhile
\Return $X^+$
\EndFunction
\end{algorithmic}
\end{algorithm}
```
##### Teorema
L’algoritmo _Chiusura lenta_ è _corretto_. `

_Dimostrazione_:
Terminazione. Ad ogni iterazione si aggiunge qualche attributo a XPIU oppure si
termina. Poiche il numero degli attributi ´ e finito segue che l’algoritmo non pu ` o`
ciclare indefinitamente.
Correttezza. Per dimostrare che quando l’algoritmo termina XPIU = X
+, si dimo￾stra che XPIU ⊆ X
+ e X
+ ⊆ XPIU.
Per dimostrare che XPIU ⊆ X
+ e sufficiente provare per induzione sul numero `
di iterazioni j che XPIUj ⊆ X
+, per ogni j. Per j = 0 l’affermazione e ovvia `
essendo XPIU0 = X ⊆ X
+ per riflessivita. Per l’ipotesi induttiva, sia ` XPIUj ⊆ X
+
e proviamo che XPIUj+1 ⊆ X
+. Sia A un attributo aggiunto alla j + 1-esima
iterazione. Per come e stato definito l’algoritmo si ha che ` A ∈ V, W → V ∈ F,
W ⊆ XPIUj
. Per l’ipotesi induttiva W ⊆ X
+, e dal Teorema 5.2, X → W; per
transitivita` X → V e quindi X → A. Pertanto A ∈ X
+.
Dimostriamo ora che X
+ ⊆ XPIU. Si noti innanzitutto che se V ⊆ W, allora
V
+ ⊆ W+. Pertanto, poiche´ X ⊆ XPIU, X
+ ⊆ XPIU+. Basta allora dimostrare
che XPIU+ ⊆ XPIU, ovvero che se A 6∈ XPIU allora A 6∈ XPIU+, cioe esiste `
un’istanza valida r di R che non soddisfa XPIU → A. Si costruisce una relazione
r = {t, t0
} di due ennuple distinte che dipendono dal risultato dell’algoritmo
ponendo t[A] = t
0
[A] per ogni A ∈ XPIU e t[B] 6= t
0
[B] per ogni B ∈ T−XPIU.
Supponiamo di aver dimostrato che r soddisfa ogni dipendenza in F; si dimostra
che r non soddisfa XPIU → A: t e t
0
coincidono su XPIU per costruzione, mentre
non coincidono su A perche per ipotesi ´ A 6∈ XPIU.
Rimane da provare che r soddisfa ogni dipendenza in F. Sia W → V una di￾pendenza di F. Se W 6⊆ XPIU, allora t[W] 6= t
0
[W], ed r soddisfa ovviamente la
dipendenza. Se W ⊆ XPIU, si ha che V ⊆ XPIU poiche l’algoritmo termina con ´
XPIU. Ma V ⊆ XPIU implica t[V] = t
0
[V] e quindi r soddisfa la dipendenza