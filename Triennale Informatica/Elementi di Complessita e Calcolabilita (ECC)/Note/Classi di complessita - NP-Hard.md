---
Course: "[[Elementi di Complessità e Calcolabilità (ECC)]]"
tags:
  - ECC
Area: 
topic: 
SubTopic:
---


# Classi di complessita - NP-Hard
---
Le classi di complessità NP-Hard comprendono tutti quei problemi per i quali ogni problema appartenente alla classe NP può essere ridotto in tempo polinomiale. In termini formali, un problema $A$ è detto NP-Hard se per ogni problema $B \in \text{NP}$ esiste una riduzione polinomiale $B \leq_p A$. Ciò implica che la risoluzione efficiente di $A$ comporterebbe la possibilità di risolvere in tempo polinomiale qualsiasi problema in NP.

È importante osservare che la definizione di NP-Hard non richiede che il problema appartenga a NP, ossia non è necessario che le soluzioni siano verificabili in tempo polinomiale. Alcuni problemi NP-Hard possono infatti essere non decisionali o addirittura non ricorsivamente enumerabili. In termini di gerarchia, la classe NP-Hard include la classe NP-Completa come suo sottoinsieme, poiché un problema è NP-Completo se e solo se è sia NP-Hard che appartenente a NP.

Il concetto di NP-Hard rappresenta quindi una misura della difficoltà intrinseca di un problema rispetto ai problemi in NP. Se esistesse un algoritmo polinomiale per un singolo problema NP-Hard, allora ogni problema NP sarebbe risolvibile in tempo polinomiale, implicando $P = NP$. La riduzione polinomiale costituisce dunque lo strumento fondamentale per il confronto tra le complessità di problemi diversi, garantendo che la difficoltà computazionale sia preservata attraverso la trasformazione.

Dal punto di vista computazionale, la caratterizzazione dei problemi NP-Hard si colloca nell’ambito della teoria della complessità come indicatore di intractabilità, esprimendo limiti fondamentali alla computazione deterministica e alla possibilità di trovare soluzioni efficienti per problemi generali di ottimizzazione e decisione.
