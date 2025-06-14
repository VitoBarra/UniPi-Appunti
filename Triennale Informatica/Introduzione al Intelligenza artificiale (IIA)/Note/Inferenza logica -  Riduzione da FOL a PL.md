---
Course: "[[Artificial Intelligence Fundamentals (AIF)]]"
tags:
  - AIF
Area: 
topic: 
SubTopic: 
---

# Inferenza logica - Riduzione da FOL a PL
---
Un approccio per fare [[Sistema di inferenza per FOL|inferenza con KB FOL]] consiste nel **ridurre la formula** dalla logica del primo ordine alla [[Logica proposizionale|logica proposizionale]], ottenendo una base di conoscenza proposizionalizzata $KB_{PL}$. In questo modo, è possibile applicare le tecniche di [[Inferenza logica per dimostrazione di teoremi|inferenza logica per dimostrazione di teoremi]] già disponibili per la [[logica proposizionale|logica proposizionale]].

Grazie al [[Teorema di Herbrand]], sappiamo che questo metodo è **completo**, ovvero ogni formula [[Conseguenza Logica (Deduzione)|logicamente implicata]]  vale  $KB_{FOL} \models \alpha \iff  KB_{PL} \models \alpha$.

L’algoritmo di inferenza può essere schematizzato nei seguenti passi:
1. Applicare le regole di istanziazione (Universal e Existential/Skolem) a $KB_{FOL}$ per generare le istanze iniziali in $KB_{PL}$.  
2. Generare progressivamente nuove istanze con termini ground di profondità crescente, includendo simboli di funzione se presenti.  
3. Applicare un algoritmo di deduzione proposizionale su $KB_{PL}$ per verificare se $\alpha$ può essere derivata.  

Se $\alpha$ viene derivata, allora $KB_{FOL} \models \alpha$. Se invece $KB_{FOL} \not\models \alpha$, l’algoritmo può non terminare, poiché continua a espandere $KB_{PL}$ senza alcun criterio generale per stabilire la non derivabilità. Questo è un risultati generale infatti decidere se $KB_{FOL} \models \alpha$ è un problema [[Calcolabilità|semideducibile]]