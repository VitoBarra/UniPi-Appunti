---
type: nota
course: Data Base
topic: 
tags:
  - FDI
Parent MOC: "[[Data Base (DB)]]"
---

# Modello Relazionale - Chiavi
---
le Chiavi sono un concetto nel [[Modello dati - Modello Relazionale|modello relazionale]]
##### Superchiave (Definizione)
_sia_ 
- $R$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
- $X$ Un _sotto insieme_ degli attributi di $R$
_se_ per ogni _Instanza valida_ di $R$ vale che i valori degli atributi $X$ _determinano univocamente_ un'_ennupla_ di $R$ 
_allora_ $X$ è una __*superchiave*__ per $R$.

#### Chiave (Definizione)
_sia_ 
- $R$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
- $X$ una _superchiave_ di $R$
_se_  $X$ è _minimale_
_allora_ la $X$ è una __*chiave*__ per $R$.

> [!tip] Minimale
> 	 Togliendo un qualsiasi attributo da $X$ questo non è piu _superchiave_
##### Chiave primaria (Definizione)
_sia_
- $R$ uno [[Modello dati - Modello Relazionale|schema relazionale]]
- $X_{1},\dots X_{n}$ un insieme di _chiavi_ per $R$
_allora_ una _chiave primaria_ $X_{i}$ è una _chiave_ scelta tra $X_{1},\dots,X_{n}$

>[!note]
>Solitamente si sceglie la chiave con meno _attributi_

##### Chiavi esterne (Definizione)
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
