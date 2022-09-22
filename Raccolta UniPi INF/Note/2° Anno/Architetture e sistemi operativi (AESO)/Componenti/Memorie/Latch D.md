# Latch D

il latch D Come il Latch RS è una rete bistrate e risolve due problemi del latch RS

- semplifica l interfaccia del componente prendendo un solo ingresso D che rappresenta quale valore dare alla memoria
- permette di controllare il quando far cambiare il valore

facendo cosi la progettazione è più comoda e non adibiamo più gestire se attivare il SET o il RESET basta fargli il valore che vogliamo che venga salvato nel ingresso D, ha una temporizzazione controllata grazie ad un ingresso CLK che se è ALTO allora diventa trasparente  e valore della rete diventa D se invece è BASSO il Latch diventa opaco e il valore della rete non cambia  a prescindere da D, resta quello precedentemente salvato

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Memorie/Latch D/Untitled.png]]

in generale è un miglioramento della sua interfaccia e delle sue funzionalità

---

Status : #NotSet

Tag: [Aeso](../../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
