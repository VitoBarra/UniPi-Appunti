---
Course: "[[Analisi]]"
topic: nota
tags:
  - Analisi
---
# Teorema di Fubini-Tonelli
Il [[Teorema di Fubini-Tonelli|teorema di Fubini-Tonelli]] consente di calcolare [[Integrali|integrali]] multipli come integrali iterati.
- Sia $A=A_1\times A_2$ con $A_1,A_2$ insiemi misurabili, e sia $f$ una [[Funzioni|funzione]] definita su $A$.
- Se $f\geq 0$ oppure se $f$ è assolutamente integrabile su $A$, allora vale:
$$\iint_{A_1\times A_2}f(x,y)\,dx\,dy=\int_{A_1}\left(\int_{A_2}f(x,y)\,dy\right)dx=\int_{A_2}\left(\int_{A_1}f(x,y)\,dx\right)dy$$
- Il teorema permette di scambiare l'ordine di integrazione quando le ipotesi sono soddisfatte.
- Il risultato è fondamentale nello studio di [[Integrali|integrali]] doppi e, più in generale, delle funzioni di più variabili.
