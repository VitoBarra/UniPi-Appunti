---
Subject: "[[Introduzione al Intelligenza Artificiale (IIA)]]"
topic: nota
tags:
  - IA
---


# Agenti logici - Sistemi a regole
---
è un tipo  di [[AI - Agenti Razionali|Agente razionale]] che utilizzano come motore un _Sotto insieme_ della [[Logica del primo ordine (FOL)|Logica del primo ordine]] 

si utilizzano le clausole _Horn Definite_: ovvero hanno esattamente un letterale positivo 
$$\{Q,\lnot P_1,\dots,\lnot P_k\} \ \ con\ \  k \ge 0$$
possiamo quindi riscrivere le regole 
- $\lnot P_1 \lor \dots \lor \lnot P_k \lor Q$
- $\lnot (P_1 \land \dots \land  P_k) \lor Q$
- $(P_1 \land \dots \land  P_k) \implies Q$ detta _Regola_
- $Q$ detto _fatto_


Se la [[AI - Base di conoscenza (KB)| base di conoscenza]] è formata solo da clausole Horn Definite i [[AI - Sistemi di deduzione (o di Inferenza)|meccanismi di inferenza]] sono molto più semplici e non si rinuncia _completezza_.
- Risolutori in tempo lineare per caso proposizionale 
- nota: è restrittivo non coincide con FOL

### Programmazione logica
I programmi logici sono [[AI - Base di conoscenza (KB)|KB]] costruiti di clausole Horn definite espressi con _fatti_ e _regole_,con una sintassi alternativa
- $A$ fatto
- $A:-B_1,B_2,\dots,B_n$
- Rappresentazione del goal 
- $(B_1 \lor B_2 \lor \dots\lor B_n)$ è il goal 
- $\lnot(B_1 \lor B_2 \lor \dots\lor B_n)\lor False$ è il goal negato ovvero
-  $(B_1 \lor B_2 \lor \dots\lor B_n)\implies False$
- $:-(B_1, B_2, \dots, B_n)$

_Interpretazione dichiarativa_ di una regola 
- $A :- B_1,B_2,\dots,B_n$ dove (A _Testa_, $B_1,B_2,\dots,B_n$ _corpo_)
- $A$ è vero se sono veri $B_1,B_2,\dots,B_n$  in accordo al significato logico del implicazione 
_Interpretazione procedurale_
- la testa puo essere vista come una chiamata di procedura e il corpo come una serie di procedure da eseguirei in sequenza


