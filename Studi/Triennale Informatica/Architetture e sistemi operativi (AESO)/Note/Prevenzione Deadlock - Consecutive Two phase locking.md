---
Subject: "[[Architetture e sistemi operativi (AESO)]]"
topic: nota
tags:
  - AESO
---

# Prevenzione Deadlock - Consecutive Two phase locking
---
[da leggere meglio, evidentente qui voglio parlare del consecutive two phase locking](https://en.wikipedia.org/wiki/Two-phase_locking)

[[Prevenzione Deadlock]]
 # Two-Phase Locking Protocol

Il protocollo di bloccaggio a due fasi (Two-Phase Locking, 2PL) è un meccanismo critico nei sistemi di gestione dei database per garantire la consistenza e l'isolamento delle transazioni.

## Fasi Principali:

### 1. Fase di Crescita (Growing Phase):

Durante questa fase, una transazione può acquisire nuovi blocchi, ma non può rilasciarli. Ciò impedisce l'interferenza da parte di altre transazioni.

### 2. Fase di Decrescita (Shrinking Phase):

Una volta che una transazione ha rilasciato almeno un blocco, entra nella fase di decrescita. In questa fase, la transazione non può più acquisire nuovi blocchi, ma può rilasciarli.

## Regole Fondamentali:

1. **Regola di Bloccaggio (Lock Point Rule):**
   - Un blocco può essere richiesto solo se la transazione non ha mai rilasciato alcun blocco.

2. **Regola di Rilascio (Unlock Point Rule):**
   - Una transazione può rilasciare un blocco solo se non ha mai acquisito alcun nuovo blocco dopo il rilascio precedente.

3. **Regola del Rilascio Finale (Final Unlock Rule):**
   - Una transazione deve rilasciare tutti i suoi blocchi prima del termine.

## Vantaggi:

- Assicura la serializzabilità delle transazioni, evitando deadlock.
- Garantisce che le transazioni siano atomiche, consistenti, isolate e durature (ACID properties).

## Limitazioni:

- Possibile rallentamento a causa di transazioni che detengono i blocchi per lungo tempo.
- Suscettibile al deadlock in situazioni complesse.

I protocolli di bloccaggio come 2PL sono fondamentali per mantenere l'integrità dei dati in ambienti multiutente con concorrenza.