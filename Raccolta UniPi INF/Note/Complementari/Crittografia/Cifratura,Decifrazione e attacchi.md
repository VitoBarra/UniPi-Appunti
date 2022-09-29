---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Criptazione Decrittazione  e attacchi
---
criptare e decriptare un messaggio sigifnica farle passare per le funzioni di Criptazione e decrittazione definite come 

- _Criptazione_: $\mathcal{C}:MSG \rightarrow CRT$
- _Decriptazione_: $\mathcal{D}:CRT \rightarrow MSG$

Dove $MSG$ è lo spazio dei messaggi e $CRT$ è lo spazio dei crittogrammi.
Le funzioni $\mathcal{C}$ e $\mathcal{D}$ sono una l [[Funzioni Invertubili|inversa]] del altra e sono funzioni _[[Funzioni Parziali|parziali]]_ e quindi i messaggi effettivamente scambiabbili sono un sottoinsieme di $MSG$ e i relativi crittogrammi generati sono un sottoinsieme di $CRT$. $\mathcal{C}$ deve essere [[Funzioni InniettiveI|Inniettiva]] 

nello _scheda di comunicazione_ si usano come 
$$\mathcal{D}(\mathcal{C}(m)) = m$$
![[C9E59A06-8A09-41F4-98E6-0A56527C08AE.jpeg]]
 