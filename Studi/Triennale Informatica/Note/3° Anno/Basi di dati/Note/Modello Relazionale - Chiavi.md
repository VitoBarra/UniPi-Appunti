---
Subject: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# Modello Relazionale - Chiavi
---
le Chiavi sono un concetto nel [[Modello dati - Modello Relazionale|modello relazionale]]
#### Superchiave (Definizione)
_sia_ 
- $R\langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
- $W \subseteq T$ Un _sottoinsieme_ degli attributi di $R$
_se_ la [[Schemi relazionali - Dipendenze funzionali|dipendenza funzionale]] $W \rightarrow T \in F^+$ è nella [[Schema relazionali - Chiusura di Insiemi di dipendenze|chiusura]] di $F$  
_allora_ $W$ è una __*superchiave*__ per $R$.

_Ovvero_ per ogni _Istanza valida_ di $R$ vale che i valori degli attributi $W$ _determinano univocamente_ un'_ennupla_ di $R$

#### Chiave (Definizione)
_sia_ 
- $R\langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
- $W \subseteq T$ una _superchiave_ di $R$
_se_  _NON esiste_ un $X \subset W$ che sia _superchiave_
_allora_ la $W$ è una __*chiave*__ per $R$.

cioè $W$ è _minimale_ ovvero rimuovendo un qualsiasi attributo da $W$ questo smette di essere _superchiave_

#### Attributo primo (Definizione)
_sia_
- $R\langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
_Se_ $A \in T$ appartiene ad una _chiave_
_allora_ $A$ è detto _attributo primo_ 
_altrimenti_ $A$ è detto _NON primo_

> [!note]
> Determinare se un attributo è _primo_ richiede un _algoritmo esponenziale_ ed è un problema [[Classi di Complessita|NP-Completo]]

#### Chiave primaria (Definizione)
_sia_
- $R\langle T,F\rangle$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
- $W_{1},\dots W_{n}$ un insieme di _chiavi_ per $R$
_allora_ una _chiave primaria_ $W_{i}$ è una _chiave_ scelta tra $W_{1},\dots W_{n}$

>[!tip] scelta
>Solitamente si sceglie la chiave con meno _attributi_

#### Chiavi esterne (Definizione)
__Sia__ 
- $R,S$ due [[Modello dati - Modello Relazionale|schemi relazionali]]
- $B$ la _chiave primaria_ di $S$
- $A$ un _[[Insiemi Matematici|sotto insieme]]_ degli attributi di $R$
__Se__ in ogni istanza valida della _base di dati_, vale che $$\forall t_r \in R \ \exists t_{s} \in  S\mid t_r.A_i=t_s.B_i$$ dove $t.X$ indica il valore del attributo $X$ della _ennupla_ $t$
__allora__ $A$ è una _chiave esterna_ che _riferisce_ la _chiave primaria_ $B$

>[!tip]
>_vale che_ $$adom(A_{i}) \subseteq adom(B_{i}) \ \ \forall i$$
>ovvero i valori presi gli attributi in $A$ sono un sotto insieme dei valori presi dagli attributi in $B$

le _chiavi esterne_ sono usate per modellare le _associazioni_ nel [[Modello dati - Modello Relazionale|modello relazionale]]
