---
Course 2: "[[Fondamenti Del Informatica (FDI)]]"
Course: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
tags:
  - FDI
  - IIA
Area:
topic: nota
SubTopic:
---

# Logica proposizionale
---
la __logica proposizionale__ è un [[Linguaggi formali|linguaggio formale]] per le __espressioni [[Logica|logiche]]__, ovvero espressioni di verità dove gli unici valori ammessi sono  __$True$__ e __$False$__ 

__Sintassi___: definisce quali sono le frasi legittime (_ben formate_) del linguaggio. Ogni enunciato è un'**espressione logica** ben formata che è una combinazione di **letterali**, ovvero variabili che assumono valori di verità: $True$ o $False$ e **operatori logici** come $\lor$, $\land$, $\neg$, $\Rightarrow$, $\Leftrightarrow$. la [[Grammatica formale]] è espressa con notazione [[Backus Naur Form (BNF)|BNF]] come:
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


\end{array}$$ e le regole di precedenza espresse da l [[Ordinamenti|ordinamento]]. questo permette di omettere e parentesi.
$$\neg >\land > \lor>\implies >\iff$$




__Semantica__: assegna il significato alle espressioni. le **espressioni** vengono valutate in base alle regole della **logica proposizionale**, determinando un valore di verità come risultato.  


gli __[[Operazioni algebriche|operazioni]] logici__ della logica proposizionale sono definiti come: \
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
  

### Equivalenze logiche 
un **equivalenze logiche** sono delle identità tra **enunciati** scritto come $\alpha \equiv \beta$  usate per semplificare la valutazione di un espressione logica iniziale. In certi l'contesti usare queste equivalenze a questo scopo viene chiamato **Calcolo proposizionale**.

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

