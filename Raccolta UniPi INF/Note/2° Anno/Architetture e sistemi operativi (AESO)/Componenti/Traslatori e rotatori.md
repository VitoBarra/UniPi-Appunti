# Traslatori e rotatori

I traslatori (shifter) e i rotatori (rotator) traslano i bit ed eseguono la moltiplicazione o la divisione per potenze di 2

## Traslatori

i traslatori traslano un numero binario a destra o a sinistra di uno specifico numero di
posizioni

## Traslatore logico:

trasla un numero verso sinistra (LSL, Logical Shift Left)
o verso destra (LSR, Logical Shift Right) e riempie gli spazi lasciati vuoti
con 0.
Esempi:

- 11001 LSR 2 = 00110
- 11001 LSL 2 = 00100

## Traslatore aritmetico:

esegue la stessa funzione di un traslatore logico, ma quando trasla un numero verso destra (ARS, Arithmetic Shift Right), riempie i bit più significativi con una copia del precedente bit più significativo. utile per quando è necessario moltiplicare o dividere numeri con segno. La traslazione aritmetica verso sinistra (ASL, Arithmetic Shift Left) si comporta
come la traslazione logica verso sinistra.
Esempi:

- 11001 ASR 2 = 11110
- 11001 ASL 2 = 00100

realizzazione dei traslatori

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Traslatori e rotatori/Untitled.png]]

traslare dei bit da sinistra significa moltiplicare il valore per $2^n$ mentre traslali algebricamente a destra significa dividere per $2^n$

## Rotatore

trasla un numero verso sinistra (ROL, Rotate Left) o verso destra
(ROR, Rotate Right) circolarmente, in modo che gli spazi lasciati vuoti vengano riempiti dai bit all’estremità opposta del numero.

Esempi:

- 11001 ROR 2 = 01110
- 11001 ROL 2 = 00111

---

Status : #NotSet

Tag: [Aeso](../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
