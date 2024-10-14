---
Subject: "[[Architetture e sistemi operativi (AESO)]]"
topic: nota
tags:
  - AESO
---

# Sommatore
---


## SemiSommatore (HalfAdder)

il semi sommatore si rialza con una porta [[Porte Logiche#Porta XOR|XOR]] e un porta AND fa la somma dei due ingressi  e la mette in uscita utilizzando lo [[Porte Logiche#Porta XOR|XOR]] mentre per il riporto utilizza l AND

![[UniPi-Appunti/Studi/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 12.png]]

## SommatoreCompleto (FullAdder)

come il semisommatore ma accetta un Riporto in ingresso che aggiunge agli ingressi

![[UniPi-Appunti/Studi/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 1 4.png]]

## Sommatore a propagazione di riporto

 sono i dentici ai sommatore completi ma hanno la possibilità di propagare il riporto al bit successivo può quindi accettare più bit ed è realizzabile in vari modi

![[UniPi-Appunti/Studi/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 2 3.png]]

## Sommatore a propagazione di riporto a onda

realizzazione con più full adder in cascata si utilizza il $R_{out}$ del precedente come ingresso per $R_{in}$ del successivo

![[UniPi-Appunti/Studi/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 3 3.png]]

funzioan ma scala male in termini di prestazioni con l aggiunga di bit siccome ogni sommatore dipende dal precedente

## Sommatore ad anticipazione di riporto

 divide la logica della somma dei bit in blocchi distinti per esempio una sommatore a 32 bit di ingresso possono essere divisi in 8 blocchi da 4 bit. questo ne calcola da subito il riporto nei casi in cui

- l ultima colonna genera sempre un riporto (sono entrambi ad 1) è in questo casi chiama riporto generato
- se viene propagato un riporto dal riporto di ingresso questo viene appunto chiamato riporto propagato

![[UniPi-Appunti/Studi/Triennale Informatica/Architetture e sistemi operativi (AESO)/Media/Untitled 4 2.png]]

 scala meglio in termini di prestazione rispetto  al Sommatore a propagazione di riporto a onda ma comunque rallenta un po' con le dimensioni, il percorso critico diventa la velocita del singolo blocco

## Sommatore a prefissi

è una tecnica potentissima (sommatori che scalano in modo logaritmico)
