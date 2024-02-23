---
Subject: "[[Data Base (DB)]]"
topic: nota
tags:
  - DB
---

# Schemi relazionali - Dipendenze derivate
---
Le _dipende derivate_ in uno _[[Modello dati - Modello Relazionale|schema relazionale]] $R \langle T,F\rangle$_ sono tutte le [[Schemi relazionali - Dipendenze funzionali|dipende funzionali]] _Derivabili_ da quelle presenti in $F$.
Un [[Modello dati - Modello Relazionale|istanza valida]] oltre le dipendenze in $F$ deve sodisfare anche tutte _quelle derivate_


##### Dipendenza Derivata (Definizione)
_sia_ $R \langle T,F\rangle$ un _[[Modello dati - Modello Relazionale|schema relazionale]]_
_allora_ una _dipendenza derivata_ indicata con $F \models X \rightarrow Y$ ($F$ _Implica logicamente_ $X \rightarrow Y$) è tale 
_se_ ogni istanza $r$ di $R(T)$ che soddisfa $F$ soddisfa anche $X \rightarrow Y$


Da questa definizione vale immediatamente che 
- $\{ X \rightarrow Y,X \rightarrow Z \}\models X \rightarrow YZ$
- $\{  \} \models X \rightarrow X$ 


#### Ricerca Delle dipendenze derivate
per cercare tutte le _dipendenze derivate_ partendo da un insieme $F$ di [[Schemi relazionali - Dipendenze funzionali|dipendenze funzionali]] c è bisogno di un _insieme di regole_ che permettono di costruire un [[Algoritmi|algoritmo]]. 
Si utilizzano le [[Regole di inferenza|regole di inferenza]] in questo contesto detti “assiomi”

##### Definizione
_sia_
- $F$ un insieme di _[[Schemi relazionali - Dipendenze funzionali|dipendenze funzionali]]_
- $RI$ un [[Insiemi Matematici|insieme]] di [[Regole di inferenza|regole di inferenza]] per $F$
_allora_  si indica con $F \vdash X \rightarrow Y$ la derivabilità di $X \rightarrow Y$ usando $RI$ e
- L insieme $RI$ è _corretto_ se: $F \vdash X \rightarrow Y \implies F \models X \rightarrow Y$
- L Insieme $RI$ è _completo_ se $F \models X \rightarrow Y \implies F \vdash X \rightarrow Y$

> [!tip]
> L insieme corretto e completo piu famoso sono gli [[Schema relazionali - Assiomi di Armstrong|assiomi di Armstrong]]

##### Derivazione di una dipendenza (Definizione)
una _derivazione_ di $f$ da $F$ è una sequenza finita $f_{1},\dots f_{m}$ di _dipendenze_ dove 
- $f_{m}=f$ 
- ogni $f_{i}$ o è un _elemento_ di $F$ oppure è stato _derivato da_ $F$ con delle _[[Regole di inferenza|regole di inferenza]]_  
 
vale che ogni _sotto sequenza_ $f_{1},\dots,f_{k}$ è una _derivazione_ e quindi che $$F \vdash f_{k} \ \ \forall k\leq m$$