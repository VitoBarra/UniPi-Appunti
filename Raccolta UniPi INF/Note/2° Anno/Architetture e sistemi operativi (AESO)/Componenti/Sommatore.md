# Sommatore

## SemiSommatore (HalfAdder)

il semi sommatore si rializa con una porta XOR e un porta AND fa la somma dei due ingressi  e la mette in unscita utilizando lo XOR mentre per il riporto utiliza l AND

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Sommatore/Untitled.png]]

## SommatoreCompleto (FullAdder)

come il semisommatore ma accetta un Riporto in ingresso che aggiunge agli ingressi

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Sommatore/Untitled 1.png]]

## Sommatore a propagazione di riporto

 sono i dentici ai sommatore completi ma hanno la possibilita di propragare il riporto al bit successivo puo quindi accettare piu bit ed è realizabile in vari modi

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Sommatore/Untitled 2.png]]

## Sommatore a propagazione di riporto a onda

realizazione con piu full adder in cascata si utilizza il $R_{out}$ del precedente come ingresso per $R_{in}$ del successivo

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Sommatore/Untitled 3.png]]

funzioan ma scala male in termini di prestazioni con l aggiunga di bit siccome ogni sommatore dipende dal precedente

## Sommatore ad anticipazione di riporto

 divide la logica della somma dei bit in blocchi distinti per sempio una sommatore a 32 bit di ingresso possono essere divisi in 8 blocchi da 4 bit. questo ne clacola da subito il riporto nei casi in cui

- l ultima colonna genera sempre un riporto (sono entrabi ad 1) è in questo casi chiama riporto generato
- se viene propagato un riporto dal riporto di ingresso questo viene appunto chiamato riporto propagato

[[Raccolta UniPi INF/Note/2° Anno/Architetture e sistemi operativi (AESO)/Componenti/Sommatore/Untitled 4.png]]

 scala meglio in termini di prestazione rispetto  al Sommatore a propagazione di riporto a onda ma comunque rallenta un po con le dimenzioni, il percorso critico diventa la velocita del singolo blocco

## Sommatore a prefissi

è una tecnica potentissima (sommatori che scalano in modo logaritmico)

---

Status : #NotSet

Tag: [Aeso](../../Architetture%20e%20sistemi%20operativi%20(AESO)%201e0e264228a748feabc5de07d5a770db.md)
