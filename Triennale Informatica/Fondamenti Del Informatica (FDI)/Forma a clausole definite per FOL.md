---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area: 
topic: 
SubTopic:
---

# Forma a clausole definite per FOL
---
La **Forma a clausole definite** per la [[Logica del primo ordine (FOL)|logica del primo ordine]] rappresenta un’estensione naturale della [[Forma a Clausola definita e Clausola di Horn|forma a clausole definite]] utilizzata nella [[logica proposizionale|logica proposizionale]]. quindi sono un tipo di [[Forma normale congiuntiva (CNF)|CNF]] dove ogni **clausola** è una disgiunzione ($\lor$) di letterali di cui esattamente uno è positivo. 
i **quantificazioni esistenziali** NON sono ammesse, mentre i **quantificatori universali** sono lasciati impliciti: la presenza di una variabile $x$ in una clausola implica la quantificazione universale $\forall x$. In questo modo, ogni clausola è interpretata come valida per tutti gli oggetti del dominio.

questa definizione è vera per :
- **letterali atomici**
- **implicazioni** dove le premesse sono una congiunzione ($\land$)  di **letterali positivi** e il conseguente è un **singolo letterale positivo**, in forma generale è del tipo: $$A_1 \land A_2 \land \dots \land A_n \Rightarrow B$$ dove ciascun $A_i$ e $B$ sono **[[Logica del primo ordine (FOL)|letterali atomici]] positivi**
