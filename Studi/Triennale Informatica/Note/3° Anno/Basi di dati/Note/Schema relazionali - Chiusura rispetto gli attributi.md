---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Schema relazionali - Chiusura rispetto gli attributi
---
#### Chiusura di insieme  attributi su insieme di dipendenze (Definizione)
_sia_
- $R\langle T,F \rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]] 
-  $X \subseteq T$ un sotto insieme di _attributi_
 _allora_ la _chiusura_ di $X$ rispetto a $F$ è data da $$X_F^+=\{ A \in  T \mid F \vdash X \rightarrow A \}$$
ovvero è l [[Insiemi Matematici|insieme]] di tutti gli _attributi_ che _[[Schemi relazionali - Dipendenze funzionali|dipendono funzionalmente]]_ direttamente o tramite [[Schemi relazionali - Dipendenze funzionali derivate|derivazione]] da $X$ utilizzando gli [[Schema relazionali - Assiomi di Armstrong|assiomi di Armstrong]]  

è indicato con $X^+$ quando $F$ è chiaro dal contesto

##### Teorema
_sia_ $F$ un [[Insiemi Matematici|insieme]] di _[[Schemi relazionali - Dipendenze funzionali|dipendenze funzionali]]_ 
_Se_ la [[Schemi relazionali - Dipendenze funzionali derivate|derivazione]] è fatta con gli [[Schema relazionali - Assiomi di Armstrong|Assiomi di Armstrong]]
_allora_ $$F \vdash X \rightarrow Y \iff Y \subseteq X^+$$
_Dimostrazione_: _Sia_ $Y = A_1 \dots A_k, A_i \in  T$.
$(\implies)$ :
	per _decomposizione_ vale che $F \vdash X \rightarrow A_i \ \ 1 \leq i \leq k$
	per _definizione_ di $X^+$ vale che $A_i \in  X^+,\ \  1 \leq i \leq k$ 
	_quindi vale_ $Y \subseteq X^+$
	
$(\ \Longleftarrow\ )$ :
	per _definizione_ di $X^+$ vale che $F \vdash X \rightarrow A_i \ \ 1 \leq i \leq k$
	per _unione_ vale che $F \vdash X \rightarrow A_1, \dots , A_k$ 
	_quindi vale_   $F \vdash X \rightarrow Y$	