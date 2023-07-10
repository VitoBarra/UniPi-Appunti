---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Cifratura e Decifratura
---
criptare e decriptare un messaggio significa farle passare per le funzioni di Criptazione e decrittazione definite come 

- _Criptazione_: $\mathcal{C}:MSG \rightarrow CRT$
- _Decriptazione_: $\mathcal{D}:CRT \rightarrow MSG$

Dove $MSG$ è lo spazio dei messaggi e $CRT$ è lo spazio dei crittogrammi.
Le funzioni $\mathcal{C}$ e $\mathcal{D}$ sono una l [[Funzioni|inversa]] del altra e sono funzioni _[[Funzioni|parziali]]_ e quindi i messaggi effettivamente scambiabili sono un sottoinsieme di $MSG$ e i relativi crittogrammi generati sono un sottoinsieme di $CRT$. $\mathcal{C}$ deve essere [[Funzioni|Inniettiva]] 

nello _scheda di comunicazione_ si usano come 
$$\mathcal{D}(\mathcal{C}(m)) = m$$
![[C9E59A06-8A09-41F4-98E6-0A56527C08AE.jpeg]]
la comunicazione avviene su un canale _insicuro_ cosi non fosse non ci sarebbe la necessita di [[Crittografia Concetti Generali|criptare]] il messaggio. un canali insicuro significa che qualcuno potrebbe provare ad legge il messaggio e nel caso dei messaggi criptati struttura degli [[Tipologia di attacchi per scoprire il messaggio criptato|attacchi]] per decrittare il Messaggio.
