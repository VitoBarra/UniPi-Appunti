---
Course: "[[Elementi di Complessità e Calcolabilità (ECC)]]"
tags:
  - ECC
  - Status/AiGenerated
Area:
topic:
SubTopic:
---


# Classi di complessita - NP-Completo
---
Le classi di complessità NP-Completo comprendono i problemi che risultano al tempo stesso appartenenti a NP e NP-Hard. Un problema $A$ è definito NP-Completo se soddisfa due condizioni fondamentali: in primo luogo, $A \in \text{NP}$, ossia ogni soluzione candidata può essere verificata in tempo polinomiale; in secondo luogo, $A$ è NP-Hard, ovvero ogni problema $B \in \text{NP}$ può essere ridotto ad $A$ mediante una riduzione polinomiale $B \leq_p A$.

Questa doppia condizione implica che i problemi NP-Completi rappresentano i problemi più difficili all’interno della classe NP, nel senso che una soluzione efficiente per uno solo di essi fornirebbe automaticamente una soluzione efficiente per tutti gli altri problemi in NP. La relazione concettuale tra le classi $P$, $NP$, $NP$-Completo e $NP$-Hard evidenzia la centralità del quesito irrisolto $P = NP$, poiché la scoperta di un algoritmo polinomiale per un singolo problema NP-Completo implicherebbe l’uguaglianza tra le due classi.

Dal punto di vista teorico, i problemi NP-Completi costituiscono una base di riferimento per la valutazione della difficoltà computazionale. La loro individuazione avviene tipicamente dimostrando che un nuovo problema appartiene a NP e può essere ridotto in tempo polinomiale da un problema NP-Completo già noto. Questo meccanismo di riduzione garantisce la propagazione della complessità tra i problemi e definisce una struttura gerarchica stabile all’interno della teoria della complessità computazionale.

I problemi NP-Completi incarnano quindi il confine tra la trattabilità e l’intrattabilità computazionale, rappresentando una categoria di importanza cruciale nello studio dei limiti algoritmici dei modelli di calcolo deterministici e non deterministici.
