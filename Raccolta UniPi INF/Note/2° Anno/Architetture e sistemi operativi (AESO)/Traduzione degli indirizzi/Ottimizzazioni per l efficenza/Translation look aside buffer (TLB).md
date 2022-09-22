# Translation look aside buffer (TLB)

La Translation lookaside buffe (TLB) è una [[Cache]] impegnata per salvare i risultati di una traduzione. Questo conviene molto siccome le istruzioni spesso sono eseguite contiguamente è molto probabile dover fare la traduzione dello stessa pagina virtuale e quindi fare più volte lo stesso lavoro la cache risolve questo problema

[[Translation look aside buffer (TLB]]%20e6d5a28be94d4187a7375e7f4164ee78/1B446573-E574-4EDB-A0F2-C3B2D891B042.jpeg)

La TLB è realizzato con accesso parallelo che restituisce l indirizzo fisico se trova un hit nella cache altrimenti avvia i processi di traduzione ordinaria

[[Translation look aside buffer (TLB]]%20e6d5a28be94d4187a7375e7f4164ee78/B8143FC9-0F1E-4E38-A32E-3E0261C6E66D.jpeg)

Per migliorare l efficienza l inserimento della cache deve ridurre di molto il costo della traduzione di indirizzo questo avviene se il tasso di miss è molto basso. Il costo della traduzione con TLB è

$$
Cost(Address \ translation) = Cost(TLB \ lookup ) + Cost(full\ translation) \times (1-P(hit))
$$

# TLB Consistency

essendo TLB una [[Cache]] per la sua gestione bisogna tenere in considerazione le problematiche di consistenza che possono avvenire nei casi di:

- **Process context switch**:
    - Problematica: nel caso c è uno switch di contesto da un processo ad un altro senza fare nulla il nuovo processo entrante potrebbe accedere  a delle arie di memoria del vecchio processo portando a problemi di sicurezza o di affidativa
    - Soluzione:  fare il flush del TLB ma questo è penalizzante dal punto di visto delle prestazioni
    - Soluizione2: si può taggare ogni entry con l id del processo che l ha caricato in modo da poter controllare che il processo che vuole riusare quel entry sia lo stesso che l ha caricato

    ```cpp
    struct tagged_TLB_entry
    {
    	process ID;
    	virtual page number;
    	physical page frame number;
    	access permissions;
    }
    ```

    [[Translation look aside buffer (TLB]]%20e6d5a28be94d4187a7375e7f4164ee78/Untitled.png)

- **Permission reduction**:
    - Problematica: nel caso in cui dei permessi a delle entry della nella page table devo essere ridotto c è un problema siccome se quelle pagine sono condivise con altri processi il sistema operativo si deve assicurare che nessuno delle entry nel TLB abbia permessi maggiori. in casi di estensione di permessi verrà sollevata un eccezione se un processo carcera di accedere ad una pagina con permessi più stringenti dando quindi il sistema operativo la possibilità di gestire la cosa con un handler.
    - Soluzione: il sistema operativo si assicura di cancellare le entry vecchie individualmente e ricaricarle al prossimo utilizzo
- **TLB shootdown (stesso sopra ma multyproccessore)**:
    - problematica:  In un contesto di multi-processore se un entry nella page table viene modificata (ad esempio cambiano i permessi restringendosi) allora bisogna assicurarsi che in tutte le TLB quelle entry vengano pulite per eliminare il problema di inconsistenza
    - Soluzione:  quando viene modificata un entry nella page table il sistema manda un interrupt a tutti i processore che si assicureranno di pulire la loro copia di quella entry nella TLB solo alla fine di tutto il processo i processori possono tornare a lavorare. le performance degradano linearmente con il numero di processori. questo fenomeno è chiamato  TLB shootdown.

    [[Translation look aside buffer (TLB]]%20e6d5a28be94d4187a7375e7f4164ee78/Untitled%201.png)
