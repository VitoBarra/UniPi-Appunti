---
type: nota
course: Crittografia
topic: 
tags: CRI
---

Prev: [[Crittografia (CRI)]]

# Criteri di Shannon per i cifrari
---
grazie alla [[Critto analisi Statistica|crittoanalisi statistica]] Shannon proropose dei criteri che son ancora alla base dei [[Cifrari a chiave Simmetrica|cifrari a chiave simmetrica]] questi sono 
- _Diffusione_: si deve alterare la struttura del messaggi in chiaro "spargendo" i caratteri su tutto il testo cifrato.
	- Questo si ottiene permutando le lettere (o i bit) come avviene nei cifrari a [[Classificazione di cifrari|cifrari trasposizione]]
	- In questo modo si mantiene la distribuzione delle singole lettere ma si perde informazione sulla distribuzione dei $q$-grammi.
	- oppure si combinano tra loro le lettere del messaggi in modo da perdere sia l informazione sulla _distribuzione delle lettere_ che sui q-grammi. 
- _Confusione_: si deve combinare il messaggio e una chiave in modo complesso in modo da non permettere al critto analista di separare messaggio e chiave analizzando solo il crittogramma 
	- questo solitamente succede nei [[Classificazione di cifrari|cifrari poliafabetici]] e migliora con la lunghezza della chiave e nel [[Cifrario One-time Pad|Cifrario One-time Pad]] in _modo perfetto_
