# Virtually Addressed Caches

per aumentare ancora le performance si puo mettere una altra cache che permette di trovare direttamente il dato partendo dal indirizzo virtuale quindi senza passare per la consulatazione della memoria

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Traduzione degli indirizzi/Ottimizzazioni per l efficenza/Virtually Addressed Caches/Untitled.png]]

# Virtually Cache Consistency

essendo la Virtually Cache una [[Cache]] per la sua gestione bisogna tenere in considerazione le problematiche di consistenza che possono avvenire nei casi di:

- **Process context switch**: Stesso a quello del [TLB](Translation%20look%20aside%20buffer%20(TLB)%20e6d5a28be94d4187a7375e7f4164ee78.md)
- **Permission reduction e shootdown**:
    - Problematica: Stessa a quello del [TLB](Translation%20look%20aside%20buffer%20(TLB)%20e6d5a28be94d4187a7375e7f4164ee78.md)
    - Soluzione: per evitare problemi di incosistenza si consulta contemporaneamente la virtual cache e la TLB la prima fornisce il dato se nella seconda risulta che il permesso del operazione sia valido cosi da dover aggiornare solo la TLB.
- **memory address alias:**
    - Problematica: alcuni indirizzi virtuali potrebbero puntare alla stessa zona di memoria creando quindi un alias. se viene cambiato il dato nella zono di memoria deve essere cambiato in ogni alias di quella
    - Soluzione: la cache virtuale contiene anche l indirizzo fisico e alla lettura si consulta anche il TLB che generera l indirizzo fisico e i permessi d accesso nelle operazioni che cambiano la memoria si aggiornera la cache virtuale facendo una reverse lookup
