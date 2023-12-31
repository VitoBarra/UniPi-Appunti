---
type: nota
course: Data Base
topic: 
tags:
  - DB
Parent MOC: "[[Data Base (DB)]]"
---

# Schemi Relazionali - Decomposizione di schemi
---
La _decomposizione_ degli [[Modello dati - Modello Relazionale|schemi relazionali]] è un operazione necessaria per la rimozione delle _anomalie_ 
questo si fa _scomponendo_ che si presentano con _relazioni grandi_ in _relazioni più piccole_ che sodisfano certe proprietà ovvero sono in _[[Normalizzazione di schemi relazionali|forme normale]]_ 


#### Decomposizione (Definizione)
_sia_ $R(T)$ uno [[Modello dati - Modello Relazionale|schema relazionale]] 
_se_ $\bigcup_{i}T_{i} =I$
_allora_ $\rho=\{ R_{1}(T_{1}),\dots R_{K}(T_{K}) \}$ è una _decomposizione_  di $R(T)$

>[!note]
>le relazione nella decomposizione $\rho$ non sono _necessariamente disgiunte_


#### Decomposizione che preservano i dati
_Sia_ 
- $R \langle T,F \rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
- $\rho= \{ R_{1}(T_{1}),\dots,R_{k}(T_{k})\}$ è una _decomposizione_ di $R$
_Se_ per ogni relazione $r$ che soddisfa $R \langle T,F \rangle$ vale che $$r = \pi_{T_1}(r)\bowtie,\dots \bowtie\pi_{T_k}(r)$$_allora_ $\rho$ è una _decomposizione che preserva i dati_ 



##### Teorema
_sia_
- $R\langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]] 
- $\rho= \{ R_{1}(T_{1}),\dots,R_{k}(T_{k}) \}$ una _decomposizione_ di $R$
_allora_ si ha che _per ogni istanza_ $r$ di $R(T)$ vale $$r \subseteq \pi_{T_1}(r) \bowtie,\dots \bowtie\pi_{T_k}(r)$$

_dimostrazione_:
	siccome $\bigcup_{i}T_{i}$ anche la relazione $\pi_{T_1}(r) \bowtie,\dots \bowtie\pi_{T_k}(r)$ è definita su $T$
	Data l _ennupla_ $t\in r,t[T_{i}]\in \pi_{T_i}(r)$ e data la definizione di [[Modello relazionale - Algebra Relazionale|giunzione naturale]] segue che $t\in \pi_{T_1}(r) \bowtie,\dots \bowtie\pi_{T_k}(r)$


##### Teoria 
Questo teorema definisce cos è una _perdita di informazione_, Con perdita di informazione si riferisce al fatto che fare il join sulle relazioni della decomposizione restituisce più ennuple di quante c è  ne fossero nella relazione originaria



##### Teorema
_sia_ 
- $R(T)$ uno [[Modello dati - Modello Relazionale|schema relazionale]] 
- $\rho= \{ R_1(T_1),R_2(T_2) \}$ una _decomposizione_ di $R$
_se e solo se_ $T_{1} \cap T_{2} \rightarrow T_{1} \in F^+$ oppure $T_{1} \cap T_{2} \rightarrow T_{2} \in F^+$
_allora_ La _decomposizione_ $\rho$ _preserva i dati_


_Dimostrazione_:
$( \ \Longleftarrow\ )$: 
_Sopponiamo_ che $T_{1} \cap T_{2} \rightarrow T_1 \in F^+$
_sia_ 
- $r$ un istanza valida di $R\langle T,F\rangle$ 
- $s=\pi_{T_1}(r) \bowtie\pi_{T_2}(r)$ una decomposizione di $R$
- $t$ una _ennupla_
assumendo $t \in s$ bisogno dimostrare che $t \in r$
per _definizione_ di $s$ _esistono_ due _ennupla_ $u,v\in r$ tale che
- $u[T_1]=t[T_1]$
- $v[T_2]=t[T_2]$
- $u[T_1 \cap T_2] =v[T_1 \cap T_2]=t[T_1 \cap T_2]$
_siccome_ $T_1 \cap T_2 \rightarrow T_1 \in F^+$ vale che 
- $u[T_1]=v[T_1]\implies t=v$

Il caso $T_{1} \cap T_{2} \rightarrow T_2 \in F^+$ è _analogo_ con $t=u$

$( \implies )$: 
Sopponiamo che _pero ogni_ istanza valida $r$ di $R \langle T,F\rangle$ valga che $r =\pi_{T_1}(r) \bowtie \pi_{T_2}(r)$ 

Bisogna dimostrare che valga $T_1 \cap T_2 \rightarrow T_1 \in F^+$ o $T_1 \cap T_2 \rightarrow T_2 \in F^+$ 
dimostriamo per [[Tipi di dimostrazione|assurdo]] assumendo che nessune delle due implicazioni _condizioni sino verificate_

_sia_
- $W = (T_1 \cap T_2)^+$
- $Y_1=T_1-W$
- $Y_2=T_2 - W$
abbiamo che $Y_1,Y_2$ sono non vuoti per _ipotesi_ e $Y_1,Y_2,W$ sono una [[partizione|Partizione]] di $T$ 

per ogni $A_i\in T,1\leq i\leq k$ consideriamo due valori $a_i,a_i'\in dom(A_i)$ con $a_i\not=a_i'$
_costruiamo_ le relazione $r$ con attributi $WY_1Y_2$ formate dalle due ennuple
- $e_{1}=a_{i} \ \ \ 1 \leq i\leq k$
- $e_{2}=\begin{cases}a_{i}&if&A_{i} \in W\\ a_{i}'& if & A_{i}\in Y_{1}Y_{2}\end{cases}$
$r$ _soddisfa ogni dipendenza_ $V \rightarrow Z \in F$ infatti 
- _se_ $V \not\subseteq W \implies e_1[V] \not=e_2[V]$ ed $r$ soddisfa ovviamente la dipendenza 
- _se_ $V \subseteq W\implies(T_1 \cap T_2 )\rightarrow V$ e per _[[Schema relazionali - Assiomi di Armstrong|transitività]]_ vale $(T_1 \cap T_2 )\rightarrow Z$ quindi $Z \subseteq W$  e $e_1[Z]=e_2[Z]$ e quindi $r$ sodisfa la [[Schemi relazionali - Dipendenze funzionali|dipendenza]]

poiché $Y_1,Y_2$ non sono _vuoti_ $\pi_{T_1}(r)$ e $\pi_{T_2}(r)$ contengono due _ennuple_ e la loro [[Modello relazionale - Algebra Relazionale|giuzione naturale]] ne contiene $4$ che sono più di quelle di $r$ quindi $$\pi_{T_1}(r)\bowtie\pi_{T_2}(r)\not=r$$ _contradicendo l ipotesi_.
>[!note]
>questo risultato è stato _generalizzato_ con un numero $n$ di relazioni nella decomposizione anzi che solo 2


#### Decomposizione che preservano le dipendenze


