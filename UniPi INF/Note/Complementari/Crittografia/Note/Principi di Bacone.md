---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Principi di Bacone
---
## Principi per una Cifrario Robusto
anticamente dei principi di robustezza sono stati stesi da Ruggero _Bacone_. sono ancora principi validi ma vanno reinterpretati nel epoca moderna
1. le funzioni $C$ e $D$ devono essere _facili_ da calcolare; 
2. e _impossibile_ ricavare la $D$ se la $C$ non e nota;
3. il crittogramma $c = C(m)$ deve apparire _innocente_.
 dove:
 _innocente_: i messaggi non devono sembrare messaggi cifrati, in tempi moderni messaggi e crittogrammi sono sequenza di bit quindi sono sempre innocenti
  _impossibile_: traducibile oggi in [[Complessita|computazionalmente difficile]]
  _facile_: traducibile oggi in [[Complessita|computazionalmente facile]]