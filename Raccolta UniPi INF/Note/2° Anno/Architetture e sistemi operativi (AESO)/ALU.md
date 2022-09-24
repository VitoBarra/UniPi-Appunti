---
type: nota
course: Architettura E Sistemi Operativi
topic: 
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# ALU
---

Un’unita logica/aritmetica (ALU, Arithmetic/Logical Unit) unisce all’interno di una singola unità una serie di operazioni logiche e matematiche.

 una ALU tipica è in grado di eseguire le operazioni di addizione,
sottrazione, [[Porte Logiche#Porta And|AND]] e [[Porte Logiche#Porta And| OR]] logici bit a bit. L’ALU è il cuore della maggior parte dei calcolatori.

si utilizza un segnale di selezione della funzione da esegurei

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 16.png]]

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 1 7.png]]

internamente l ALU è fatta

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 2 5.png]]

in agiunta l ALU ha delle Flag per indicare alcuni casi

- overflow (V) se i sommatori sommano due numeri con lo stesso segno troppo grandi e ne restituiscono uno con il sengo opposto questo  per il [[Numeri binari con segno|complemento a due]]
- carry (C) se i [[Sommatore|sommatori]] harro poroprtato un $R_{out}$
- Negativa (N) se è un numero negativo  ad è connesso al bit piu significativo per il [[Numeri binari con segno|complemento a due]]
- Zero (Z) se tutti i bit del risultato sono a zero

![[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Media/Untitled 3 5.png]]

---
