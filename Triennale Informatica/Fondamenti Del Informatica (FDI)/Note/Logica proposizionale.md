---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area: 
topic: 
SubTopic:
---

# Logica proposizionale
---
la __logica proposizionale__ è un [[Linguaggio formale|linguaggio formale]] per esprimere le __espressioni logiche__ Tramite simboli detti __letterali__ e __operazioni logiche__, questo tipo di logica lavora espressioni di verità, ovvero i valori ammessi sono solo __$True$__ e __$False$__ 

Un'**espressione logica** è una combinazione di **letterali** (variabili che assumono valori di verità: $True$ o $False$) e **operatori logici** ($\lor$, $\land$, $\neg$, $\Rightarrow$, $\Leftrightarrow$).  
Queste espressioni vengono valutate in base alle regole della **logica proposizionale**, determinando un valore di verità come risultato.  


gli __[[Operazioni algebriche|operazioni]] logici__ della logica proposizionale sono definiti come: 
__OR__($\lor$)  e l __and__ ($\land$) sono __operatori binari__ definiti dalla tabella di verità seguente:$$
\begin{array}{|c|c||c|c|}
\hline
P & Q & P \lor Q (\text{OR}) & P \land Q (\text{AND}) \\
\hline
\text{False} & \text{False} & \text{False} & \text{False} \\
\text{False} & \text{True}  & \text{True}  & \text{False} \\
\text{True}  & \text{False} & \text{True}  & \text{False} \\
\text{True}  & \text{True}  & \text{True}  & \text{True}  \\
\hline
\end{array}
$$la __negazione__ ($\neg$) è un __operatore unario__ definita come: $$ \begin{array}{|c||c|} \hline P & \neg P (\text{NOT}) \\ \hline \text{False} & \text{True} \\ \text{True} & \text{False} \\ \hline \end{array} $$l'__Implicazione logica__ ($\Rightarrow$) è un __operatore binario__ definito come:$$ \begin{array}{|c|c||c|} \hline P & Q & P \Rightarrow Q (\text{IMPL}) \\ \hline \text{False} & \text{False} & \text{True} \\ \text{False} & \text{True} & \text{True} \\ \text{True} & \text{False} & \text{False} \\ \text{True} & \text{True} & \text{True} \\ \hline \end{array} $$ La __doppia implicazione__ ($\iff$)  è un __operatore binario__ definito come: $$ \begin{array}{|c|c||c|} \hline P & Q & P \Leftrightarrow Q (\text{EQ}) \\ \hline \text{False} & \text{False} & \text{True} \\ \text{False} & \text{True} & \text{False} \\ \text{True} & \text{False} & \text{False} \\ \text{True} & \text{True} & \text{True} \\ \hline \end{array} $$ La __ExclusiveOR__ o __XOR__ ($\oplus$) è un __operatore binario__ definito come: $$ \begin{array}{|c|c||c|} \hline P & Q & P \oplus Q (\text{XOR}) \\ \hline \text{False} & \text{False} & \text{False} \\ \text{False} & \text{True} & \text{True} \\ \text{True} & \text{False} & \text{True} \\ \text{True} & \text{True} & \text{False} \\ \hline \end{array} $$
  
La __valutazione__ di un'__espressione logica__ dipende da: 
- le regole della tabella di verità degli __operatori coinvolti__.
- l __*interpretazione*__ ovvero l'insieme dei __valori assegnati__ ad ogni __letterale__.

Ad esempio, un espressione valida è:  $$ (P \lor Q) \land \neg R $$il cui risultato dipenderà dai valori di verità assegnati a $P$, $Q$ e $R$.  

Alcune espressioni logiche speciali sono:
- __Tautologia__: un espressione logica che è sempre $True$ per ogni __interpretazione__
- __Contraddizione__: un espressione logica che è sempre $False$ per qualsiasi __interpretazione__




### Equivalenze logiche 
Per la valutazione delle __espressioni logiche__ nella pratica si utilizza il [[Calcolo proposizionale (PROP)|Calcolo proposizionale]] che si basa per la semplificazione delle espressioni tramite proprietà 

usando le __Equivalenze logiche__$$
\begin{array}{|c|c|c|}
\hline
 & \lor (\text{OR}) & \land (\text{AND}) \\
\hline
\text{Unità} & P \lor \text{False} \Leftrightarrow P & P \land \text{True} \Leftrightarrow P \\
\text{Assorbimento} & P \lor \text{True} \Leftrightarrow \text{True} & P \land \text{False} \Leftrightarrow \text{False} \\
\text{Idempotenza} & P \lor P \Leftrightarrow P & P \land P \Leftrightarrow P \\
\text{Commutatività} & P \lor Q \Leftrightarrow Q \lor P & P \land Q \Leftrightarrow Q \land P \\
\text{Associatività} & P \lor (Q \lor R) \Leftrightarrow (P \lor Q) \lor R & P \land (Q \land R) \Leftrightarrow (P \land Q) \land R \\
\text{Distributività} & P \lor (Q \land R) \Leftrightarrow (P \lor Q) \land (P \lor R) & P \land (Q \lor R) \Leftrightarrow (P \land Q) \lor (P \land R) \\
\hline
\end{array}
$$ e le __Leggi per negazione__
$$
\begin{array}{|c|c|}
\hline
\text{Proprietà} & \text{Formula} \\
\hline 
\textbf{T : F} & \neg T \Leftrightarrow F\\
\text{doppia negazione} & \neg (\neg P) \Leftrightarrow P \\
\text{terzo escluso}  &  P \vee \neg P \Leftrightarrow T \\
\text{contraddizione} & P \wedge \neg P \Leftrightarrow F \\
\text{De Morgan OR} & \neg (P \vee Q) \Leftrightarrow \neg P \wedge \neg Q \\
\text{De Morgan AND}                 & \neg (P \wedge Q) \Leftrightarrow \neg P \vee \neg Q \\
\hline
\end{array}
$$
e altre __proprietà__ di __eliminazione__ $$
\begin{array}{|c|c|}
\hline
\text{Proprietà} & \text{Formula} \\
\hline
\text{riflessività} & P \Leftrightarrow P \\
\text{simmetria} & (P \Leftrightarrow Q) \Leftrightarrow (Q \Leftrightarrow P) \\
\text{eliminazione dell’implicazione} & P \Rightarrow Q \Leftrightarrow \neg P \vee Q \\
\text{eliminazione dell’implicazione negata} & \neg (P \Rightarrow Q) \Leftrightarrow P \wedge \neg Q \\
\text{eliminazione della doppia implicazione (1)} & (P \Leftrightarrow Q) \Leftrightarrow (P \Rightarrow Q) \wedge (Q \Rightarrow P) \\
\text{eliminazione della doppia implicazione (2)} & (P \Leftrightarrow Q) \Leftrightarrow (P \wedge Q) \vee (\neg P \wedge \neg Q) \\
\hline
\end{array}$$

