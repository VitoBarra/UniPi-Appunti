---
type: nota
course: Intelligenza Artificiale
topic: 
tags:
  - IA
Parent MOC: "[[Interazione Uomo Macchina (IUM)]]"
---

# Agenti Logici - Calcolo proposizionale
---
Per gli [[AI - Agenti Razionali|agenti]] che utilizzano il [[Calcolo proposizionale (PROP)]]  hanno bisogno delle componenti tipiche del calcolo proposizionale

#### Sintassi
la sintassi definisce quali sono le frasi legittime (_ben formate_) del linguaggio definita cone una [[Grammatica formale]]
$$
\begin{array}{}
formula &\rightarrow &formulaAtomica \mid formulaComplessa \\
formulaAtomica &\rightarrow &true \mid false\mid simbolo \\
simbolo & \rightarrow &P \mid R \mid Q \mid \dots \\
formulaComplessa &\rightarrow & \neg formula \\
&&\begin{array}{}
\mid &(formula \ \land \ formula) \\
\mid &(formula \ \lor \ formula) \\
\mid &(formula \ \implies \ formula) \\
\mid &(formula \ \iff \ formula) \\
\end{array}


\end{array}$$

##### Precedenze
utilizzando le regole di precedenza rappresentato con un [[Ordinamenti|ordinamento]] si possono omettere le parentesi
$$\neg >\land > \lor>\implies >\iff$$

### Semantica
- la semantica ci indica il significa delle frasi: definisce se una enunciato è vero o falso rispetto ad un _interpretazione_ (mondo possibile)
- un interpretazione definisce una valore di verta per tutti i simboli proposizionali
- il valore di una formula complessi è fissato di conseguenza
- un _modello_ di un insieme di formule è l interpretazione che rende vere tutte le formule, l insieme delle formule puo contenere anche una sola formula
- il significa di una frase è determinata dal significato dei suoi componenti, a partire dalle frasi atomiche. seguendo le [[Logica proposizionale|Regole della logica]]


