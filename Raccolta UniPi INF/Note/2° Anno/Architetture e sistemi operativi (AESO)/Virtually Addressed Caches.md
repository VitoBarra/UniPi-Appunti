---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Virtually Addressed Caches
---

per aumentare ancora le performance si puo mettere una altra cache che permette di trovare direttamente il dato partendo dal indirizzo virtuale quindi senza passare per la consulatazione della memoria

![[Untitled 36.png]]

# Virtually Cache Consistency

essendo la Virtually Cache una [[Cache]] per la sua gestione bisogna tenere in considerazione le problematiche di consistenza che possono avvenire nei casi di:

- **Process context switch**: Stesso a quello del [[Translation look aside buffer (TLB)|TLB]]
- **Permission reduction e shootdown**:
    - Problematica: Stessa a quello del [[Translation look aside buffer (TLB)|TLB]]
    - Soluzione: per evitare problemi di incosistenza si consulta contemporaneamente la virtual cache e la [[Translation look aside buffer (TLB)|TLB]] la prima fornisce il dato se nella seconda risulta che il permesso del operazione sia valido cosi da dover aggiornare solo la [[Translation look aside buffer (TLB)|TLB]].
- **memory address alias:**
    - Problematica: alcuni indirizzi virtuali potrebbero puntare alla stessa zona di memoria creando quindi un alias. se viene cambiato il dato nella zono di memoria deve essere cambiato in ogni alias di quella
    - Soluzione: la cache virtuale contiene anche l indirizzo fisico e alla lettura si consulta anche il [[Translation look aside buffer (TLB)|TLB]] che generera l indirizzo fisico e i permessi d accesso nelle operazioni che cambiano la memoria si aggiornera la cache virtuale facendo una reverse lookup
