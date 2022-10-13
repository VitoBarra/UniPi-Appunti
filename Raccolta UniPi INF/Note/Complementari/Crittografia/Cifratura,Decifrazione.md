---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Criptazione Decrittazione
---
criptare e decriptare un messaggio significa farle passare per le funzioni di Criptazione e decrittazione definite come 

- _Criptazione_: $\mathcal{C}:MSG \rightarrow CRT$
- _Decriptazione_: $\mathcal{D}:CRT \rightarrow MSG$

Dove $MSG$ è lo spazio dei messaggi e $CRT$ è lo spazio dei crittogrammi.
Le funzioni $\mathcal{C}$ e $\mathcal{D}$ sono una l [[Funzioni Invertibili|inversa]] del altra e sono funzioni _[[Funzioni Parziali|parziali]]_ e quindi i messaggi effettivamente scambiabili sono un sottoinsieme di $MSG$ e i relativi crittogrammi generati sono un sottoinsieme di $CRT$. $\mathcal{C}$ deve essere [[Funzioni InniettiveI|Inniettiva]] 

nello _scheda di comunicazione_ si usano come 
$$\mathcal{D}(\mathcal{C}(m)) = m$$
![[C9E59A06-8A09-41F4-98E6-0A56527C08AE.jpeg]]
la comunicazione avviene su un canale _insicuro_ cosi non fosse non ci sarape la necessita di [[Crittografia Concetti Generali|criptare]] il messaggio. un canali insicuro significa che qualcuno potrebbe provare ad legge il messaggio e nel caso dei messaggi criprati struttura degli [[Tipologia di attacchi per scoprire il messaggio criptato|attacchi]] per decrittare il message.

## Principi per una Cifrario Robusto
anticamente dei principi di robustezza sono stati stesi da Ruggero Bacone. sono ancora principi validi ma vanno reinterpretati nel epoca moderna
1. le funzioni $C$ e $D$ devono essere _facili_ da calcolare; 
2. e _impossibile_ ricavare la $D$ se la $C$ non e nota;
3. il crittogramma $c = C(m)$ deve apparire _innocente_.
 dove:
 _innocente_: i messaggi non devono sembrare messaggi cifrati, in tempi moderni messaggi e crittogrammi sono sequenza di bit quindi sono sempre innocenti
  _impossibile_: traducibile oggi in [[Complessita|computazionalmente difficile]]
  _facile_: traducibile oggi in [[Complessita|computazionalmente facile]]
