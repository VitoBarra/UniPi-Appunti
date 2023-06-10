---
type: nota
course: Fondamenti Di Informatica
topic: 
tags: FDI
---

Prev: [[Fondamenti Del Informatica (FDI)]]

# Logica proposizionale
---
un modo per esprimere le espressioni logiche Tramite simboli detti _letterali_ e operazioni, questo tipo di logica lavora espressioni di verità, ovvero i valori ammessi sono solo _True_ e _False_


## Sintassi


## Semantica

#### Semantica composizionale

### Interpretazione
l insieme dei valori assegnati ad ogni letterale è detta interpretazione 


## Definizioni
- _Tatutologia_: formula preposizionale che è sempre vera per ogni interpretazione
- _Contraddizione_:  formula preposizionale che è sempre falsa per qualsiasi interpretazione

### Equivalenze logiche 
|                | OR                                                   | AND                                           |
| -------------- | ---------------------------------------------------- | --------------------------------------------- |
| Unita          | $P \lor False \iff P$                                | $P \land True \iff P$                         |
| Assorbimento   | $P \lor True \iff True$                              | $P \land False \iff False$                    |
| idempotenza    | $P \lor P\iff P$                                     | $P \land P\iff P$                             |
| Commutativita  | $P \lor Q \iff Q \lor P$| $P \land Q \iff Q \land P$                    |
| Associtivita   | $P \lor (Q \lor R) \iff (P \lor Q) \lor R$           | $P \lor (Q \land R) \iff (P \land Q) \land R$ |
| Distributivita | $P \lor (Q \land R) \iff (P \lor Q) \land (P \lor R)$ | $P \land (Q \lor R) \iff (P \land Q) \lor (P \land R)$                                              |


![[D0CDB587-A471-4FCF-9E1C-BD57687332A4.jpeg]]