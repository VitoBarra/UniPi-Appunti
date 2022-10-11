---
type: nota
course: Elementi di calcolabilita e complessita
topic: 
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Calcolabilità
---
La calcolabilità studia che cosa può o non può essere calcolato senza limiti di risorse (es tempo, spazio, energia) 


il meccanismo di calcolo puo essere visto come un [[Automa a stati finiti|automa]] e in questo automa se gli elementi sono fatti di [[Stringhe|stringhe]] su un alfabeto allora abbiamo un [[Linguaggio formale]]  

 l elemento base per dire che quel cosa è calcolabile è l [[Cos è una procedura detta algoritmo|algoritmo]] se un modello di calcolo rispetta queste properita allora si dice che quel modello puo calcolare 





## Sintassi astratta

$$
\begin{aligned}
E:= n  | X | E_1 + E_2 | E_1 *E_2 | E_1 /  E_1| E_1 - E_2 \\
B := b | E_1-E_2 | \neg b | B_1 \lor B_2 \\
C := skip | x=E | C_1;C_2 | if\  B \ then \ C_1 \ else \ C_2 | \ while \ B \ do\  C | \ for \ x=E \ to \ E_1 \ do\  C
\end{aligned}
$$

Un linguaggio e composto da espressioni comandi mantiene dati che dipendono dal linguaggio questo booleani e naturali

Sodisfacibilita e calcolabilita: una espressione e soddisfacibile se esiste un procedura di un numero finiti di passi per calcolare l espressione

Due tipologie di linguaggio: 
- Linguaggio While: oltre al resto puo calcolare algoritmi che non terminano rendendolo Turing-completo 
- linguaggio For: oltre al resto non puo calcolare le cose che non terminano perche il for finisce sempre dopo una sequenza di passi finiti

## Funzioni poi si vede
SD $\xi : Exp \times store \rightarrow N$ 
	




Tutta Roba vista a Prog Algo da Scrivere per sfizio se mi va