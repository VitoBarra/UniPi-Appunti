# Single Cicle

è una microarchitettura a ciclo unico ovvero tutte le istruzioni vengono eseguite in un unico ciclo di clock

caratteristiche:

- non ha bisogno di stato non architetturale (registri non del architettura ARM quindi registri diversi da r0-r15)
- CLU semplice siccome è rete combinatoria
- memoria dati e istruzioni separate

utilizzando un unico ciclo per ogni istruzione bisogna rendere la lunghezza di questo quanto il tempo necessario ad eseguire l istruzione più lenta. cosi facendo pero le istruzioni brevi verranno eseguite nello stesso tempo di quelle lente

[[Untitled 29.png]]

## Control unit

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Untitled 1 12.png]]
