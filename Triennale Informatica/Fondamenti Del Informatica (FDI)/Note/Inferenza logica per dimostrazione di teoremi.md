---
Corse 1: "[[Artificial Intelligence Fundamentals (AIF)]]"
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
  - AIF
  - IIA
Area: "[[Logica]]"
topic: 
SubTopic:
---

# Inferenza logica con dimostrazione di teoremi (Theorem Proving)
---
il **theorem proving** è un approccio per l'[[Sistemi di inferenza logica|inferenza logica]] che permette di stabilire la [[Conseguenza Logica (Deduzione)|conseguenza logica]] tra due [[Logica|enunciati]] applicando **regole di inferenza** direttamente sugli **enunciati** presenti nella **knowledge base** $KB$ dove ogni **enunciato** è rappresentato da un [[Linguaggi formali|linguaggio formale]].

la notazione per una **regola di inferenza** è la seguente: 
dati gli **[[Logica|enunciati]]** $p_i$ che $c_j$ si ha la regola di inferenza:  $$\frac{p_1, \dots,p_n}{c_1,\dots,c_m}$$ dove $p_i$ sono le **premesse** necessarie a dedurre le $c_i$ **conclusioni**, quindi è equivalente a $$p_1\land \dots \land p_n \models c_1 \land \dots \land c_m$$
le **regole di inferenza** basate sulla [[Logica proposizionale|Logica proposizionale]] sono:


# Regole notevoli

 **Modus Ponens**, letteralmente "modo che afferma", formalizzata come:$$\frac{\alpha \Rightarrow \beta , \ \alpha} {\beta}$$
**And-Elimination**, ovvero, data una **congiunzione** (and $\land$), è possibile inferire ciascun **congiunto** separatamente, formalizzata come: $$\frac{\alpha \land \beta }{\alpha}$$
### Regola di risoluzione
La **regola di risoluzione** permette di eliminare due **enunciati** che sono in contraddizione tra di loro. è espressa formalmente come:$$
\frac{\ell_1 \lor \cdots \lor \ell_k, \quad m}{\ell_1 \lor \cdots \lor \ell_{i-1} \lor \ell_{i+1} \lor \cdots \lor \ell_k}
$$dove $\ell_i$ e $m=\lnot \ell_i$  ovvero sono **complementari** e uno è il negato del altro.

Più in generale, la risoluzione si estende alla forma completa, applicabile a due clausole qualsiasi:$$
\frac{\ell_1 \lor \cdots \lor \ell_k, \quad m_1 \lor \cdots \lor m_n}{\ell_1 \lor \cdots \lor \ell_{i-1} \lor \ell_{i+1} \lor \cdots \lor \ell_k \lor m_1 \lor \cdots \lor m_{j-1} \lor m_{j+1} \lor \cdots \lor m_n}
$$con $\ell_i$ e $m_j$ letterali complementari. 

La regola prevede che si possa risolvere **una sola** coppia di letterali complementari per ciascuna applicazione, evitando di trattare più coppie simultaneamente. 
es.  non è corretto fare: $$\frac{P\lor Q, \ \ \  \lnot P \lor \lnot Q}{\{\}}$$siccome questo porterebbe ad una **contraddizione** mentre le condizioni originali $(P\lor Q) \land (\lnot P \lor \lnot Q)$ sono una **tautologia**.

invece è corretto fare:$$\frac{P\lor Q ,\ \ \  \lnot P \lor  \lnot Q}{P\lor \lnot P} \ \ \ \ \ \frac{P\lor Q, \ \ \  \lnot P \lor  \lnot Q}{Q\ \lor\lnot Q} $$che risultano in due **tautologie** cosi come l'espressione iniziale.

in caso di **ripetizioni di letterali** nella conclusione ottenuta del applicazione di questa regola si fa il ***factoring***, ovvero le si unisce in un unico letterale. es $A \lor A\equiv A$


La **regola di risoluzione** è **corretta** perché preserva la verità logica: ogni assegnazione di verità che rende vere le clausole di partenza rende vera anche la clausola ottenuta per risoluzione.  Consideriamo due clausole generiche:
$$
C_1 = (\ell_i \lor A), \qquad C_2 = (\lnot \ell_i \lor B)
$$
dove $\ell_i$ è un letterale e $A$, $B$ rappresentano disgiunzioni di altri letterali.  
La regola di risoluzione costruisce la clausola detta *resolvente*:$$
R = (A \lor B)
$$dimostriamo che $R$ è logicamente conseguente da $C_1$ e $C_2$, cioè$$
(C_1 \land C_2) \Rightarrow R
$$Per verificarlo, si analizzano tutti i possibili valori di verità di $\ell_i$:
1. **Caso $\ell_i = \text{True}$**  
   - La clausola $C_1 = (\ell_i \lor A)$ è vera, qualunque sia il valore di $A$.  
   - La clausola $C_2 = (\lnot \ell_i \lor B)$ diventa $(\text{False} \lor B)$, dunque per essere vera deve valere $B = \text{True}$.  
   - Se $B = \text{True}$, allora anche $R = (A \lor B)$ è vera.
1. **Caso $\ell_i = \text{False}$**  
   - La clausola $C_1 = (\ell_i \lor A)$ diventa $(\text{False} \lor A)$, quindi per essere vera deve valere $A = \text{True}$.  
   - La clausola $C_2 = (\lnot \ell_i \lor B)$ è vera, poiché $\lnot \ell_i = \text{True}$.  
   - Anche in questo caso, $R = (A \lor B)$ è vera perché $A = \text{True}$.

In entrambe le situazioni, qualunque sia il valore di $\ell_i$, se entrambe le clausole di partenza sono vere, la clausola risolvente $R$ è necessariamente vera.  
Pertanto la risoluzione è una **regola di inferenza corretta**, nel senso che non può produrre una clausola falsa a partire da premesse vere:$$
\models \big[\,(\ell_i \lor A) \land (\lnot \ell_i \lor B)\,\big] \Rightarrow (A \lor B)
$$La correttezza della regola non dipende dal contenuto specifico di $A$ e $B$, ma solo dalla relazione complementare tra $\ell_i$ e $\lnot \ell_i$. Essa garantisce che l’insieme delle clausole resti logicamente equivalente a ogni passaggio, permettendo l’eliminazione controllata di letterali contraddittori senza alterare la soddisfacibilità dell’intero sistema.



### Proprietà
Applicando queste di inferenza il cambiamento del **numero di conoscenze** in $KB$ è monotonica crescente, questo è vero perche l'aggiunta di nuove informazioni non può **invalidare inferenze già effettuate**
Formalmente abbiamo che:
***siano***  $\alpha$ e $\beta$ due **enunciati**
**vale sempre** $$KB \models \alpha \implies KB \land \beta \models \alpha$$


