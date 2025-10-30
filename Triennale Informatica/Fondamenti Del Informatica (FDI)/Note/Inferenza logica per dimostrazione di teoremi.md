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

### Rregola Modus Ponens
 **Modus Ponens**, letteralmente "modo che afferma", formalizzata come:$$\frac{\alpha \Rightarrow \beta , \ \alpha} {\beta}$$
**And-Elimination**, ovvero, data una **congiunzione** (and $\land$), è possibile inferire ciascun **congiunto** separatamente, formalizzata come: $$\frac{\alpha \land \beta }{\alpha}$$
### Rregola di risoluzione
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

La correttezza della risoluzione deriva da una semplice osservazione sulla verità dei letterali coinvolti. infatti siccome $\ell_i, m_j$ sono contrapposti si ha che $\ell_i= True\implies m_j=False$, ma siccome vale che$$
\begin{array}{}
m_1 \lor \cdots \lor m_n=True \ \land\ m_j=False & \implies\\ m_1 \lor \cdots \lor m_{j-1} \lor m_{j+1}=True
\end{array}
$$  è quindi l'espressione finale è $True$, analogo per il caso inverso.


### Proprietà
Applicando queste di inferenza il cambiamento del **numero di conoscenze** in $KB$ è monotonica crescente, questo è vero perche l'aggiunta di nuove informazioni non può **invalidare inferenze già effettuate**
Formalmente abbiamo che:
***siano***  $\alpha$ e $\beta$ due **enunciati**
**vale sempre** $$KB \models \alpha \implies KB \land \beta \models \alpha$$


