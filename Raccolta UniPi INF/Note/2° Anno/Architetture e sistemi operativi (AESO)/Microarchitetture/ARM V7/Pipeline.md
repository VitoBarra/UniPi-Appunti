# Pipeline

è una microarchitettura a più cicli di clock ovvero ogni istruzione viene eseguita più cicli di clock  ma utilizza il concetto di [[Pipe-line]] per eseguire più istruzioni contemporaneamente

caratteristiche:

- ha bisogno di stato non architetturale (registri non del archiettura arm quindi registri diversi da r0-r15)
- CLU semplice per lo più semplice con poche parti più complesse rispetto al [[Single Cicle]]
- memoria dati e istruzioni separate

utilizzando più cicli di clock per ogni istruzione il singolo ciclo può essere più breve e le istruzioni brevi verranno completate in meno cicli mentre quelli lunghe nei cicli necessari.

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Microarchitetture/ARM V7/Pipeline/Untitled.png]]

[[Dipendenze]]

[[Predizioni Salti]]
