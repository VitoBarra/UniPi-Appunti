---
Course: "[[Elementi di Complessità e Calcolabilità (ECC)]]"
tags:
  - ECC
  - Status/AiGenerated
Area:
topic:
SubTopic:
---


# Classi di complessita- co-NP-completo
---

La classe **co-NP** rappresenta l’insieme dei linguaggi decisionali il cui complementare appartiene alla classe **NP**. Se un linguaggio $L$ è in co-NP, allora esiste un algoritmo non deterministico in grado di verificare in tempo polinomiale le **controprove** di appartenenza al linguaggio complementare $\overline{L}$. Formalmente, vale la relazione $L \in \text{co-NP}$ se e solo se $\overline{L} \in \text{NP}$.

La distinzione tra NP e co-NP si basa sulla direzione della verifica: mentre per NP l’esistenza di una **testimonianza positiva** permette di confermare rapidamente l’appartenenza di un’istanza, in co-NP la verifica avviene attraverso una **testimonianza negativa** che certifica la non appartenenza. Questa simmetria logica è espressa dall’operazione di complemento sui linguaggi, che rispecchia la negazione delle condizioni di accettazione nei modelli di calcolo non deterministici.

Un problema $L$ è detto **co-NP-completo** se soddisfa due condizioni: appartiene alla classe co-NP e ogni altro problema di co-NP è riducibile ad esso in tempo polinomiale. In simboli, per ogni linguaggio $A \in \text{co-NP}$ deve esistere una funzione di riduzione polinomiale $f$ tale che $x \in A \Leftrightarrow f(x) \in L$. I problemi co-NP-completi rappresentano quindi i più difficili della classe co-NP, analogamente a quanto accade per i problemi NP-completi in NP.

La relazione tra le classi NP e co-NP rimane oggetto di discussione teorica, poiché non è noto se esse coincidano. È tuttavia noto che se $\text{NP} = \text{co-NP}$, allora le due famiglie di problemi avrebbero la stessa capacità di verifica polinomiale sia per le soluzioni positive che per le negative, implicando conseguenze profonde sulla struttura gerarchica delle classi di complessità. In termini gerarchici, vale sempre $\text{P} \subseteq \text{NP} \cap \text{co-NP}$, e l’uguaglianza $\text{NP} = \text{co-NP}$ comporterebbe $\text{NP} = \text{co-NP} = \text{P}$, con la conseguente eliminazione della distinzione tra verifica e decisione deterministica.
