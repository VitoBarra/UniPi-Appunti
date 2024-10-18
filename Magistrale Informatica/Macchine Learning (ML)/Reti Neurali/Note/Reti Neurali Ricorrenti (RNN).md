---
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---

# Reti Neurali Ricorrenti (RNN)
---
si usa per dati seriali, ovvero che dipendono dallo valore precedente.

si fa facendo l unrollign di ogni penso e bias questo porta al problema del 
Vanishing gradient/exploding gradient 

##### Vanishing/Exploding gradient

ogni volta che si calcola la loss function si aggiunge un valore moltiplicato per un peso per il numero $n$ dati per quel input. il che significa che il valore del peso e’ $w^n$ e perciò 
- con $w<1$ il gradiente diventa troppo piccolo per fare degli spostamenti 
- con $w>1$ il gradiente diventa troppo grande per spostarsi senza “mancare” il minimo

Questo si risolve con [[Reti Neurali - Long Short-term Memory (LSTM)|Reti neurali LongShort-term Memory]]