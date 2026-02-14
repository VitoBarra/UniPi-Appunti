---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Sensitivity analisys
---
la **Sensitivity analysis** è la disciplina che quantifica in modo formale come le variazioni dei parametri di un modello matematico influenzino le sue variabili di stato o le sue quantità di interesse.
Un modello matematico è una rappresentazione formale di un sistema reale tramite:
- Le **variabili di stato** descrivono l’evoluzione del sistema nel tempo (es. concentrazioni, popolazioni, livelli di espressione).
- I **parametri** indicati dal vettore $p = (p_1, \dots, p_m)$ sono quantità fisse all’interno del modello che ne determinano il comportamento (es. costanti cinetiche, tassi di crescita, coefficienti di interazione).

La **sensitivity analysis** permette di:
- Quantificare l’influenza dei parametri sull’output.
- Studiare la robustezza del modello.
- Guidare la stima parametrica.
- Identificare parametri dominanti.
- Ridurre la dimensionalità del problema.
Essa costituisce uno strumento nell’analisi quantitativa di modelli deterministici e dinamici. L’obiettivo è quantificare quanto piccole o grandi variazioni di $p$ producano variazioni nell’output $y$.


Un **modello dinamico** descrive l’evoluzione temporale delle variabili di stato:$$\dot{x}(t) = f(x(t), p)$$dove:
- $x(t) \in \mathbb{R}^n$ è il vettore delle variabili di stato,
- $p \in \mathbb{R}^m$ è il vettore dei parametri,
- $f$ definisce la dinamica del sistema,
- $\dot{x}(t)=\frac{d x}{d t}$ indica la [[Derivate|derivata]] temporale.
Il sistema è completato da una condizione iniziale:$$x(0)=x_0$$La soluzione del sistema dipende implicitamente dai parametri:$$x(t)=x(t; p)$$La **sensitivity** in questo contesto misura quanto la traiettoria $x(t)$ cambia se si modificano i parametri.

Formalmente, per ogni parametro $p_i$ si definisce la funzione di **sensitivity**:$$S_i(t) = \frac{\partial x(t; p)}{\partial p_i}$$che rappresenta la variazione istantanea della soluzione rispetto al parametro $p_i$.

Un **modello statico** è identico ma non definisce un punto di inizio e non c è una progressione di $t$  



La sensitivity analysis può essere interpretata secondo due prospettive complementari: **locale** e **globale**.

La **sensitivity locale** analizza l’effetto di piccole perturbazioni attorno a un insieme nominale di parametri $p_0$ (tipicamente stimato o corrispondente a uno stato stazionario). Il modello viene approssimato tramite una linearizzazione di primo ordine:
$$
g(p) \approx g(p_0) + \frac{\partial g}{\partial p}\Big|_{p_0} (p - p_0)
$$
Si assume quindi che il comportamento del modello sia quasi lineare in un intorno di $p_0$. L’interpretazione è quella di una **derivata in un punto**: misura la pendenza locale della risposta del modello rispetto ai parametri. È computazionalmente economica, fornisce indicazioni rapide sull’importanza relativa dei parametri, ma è valida solo per perturbazioni piccole e non cattura non linearità marcate o interazioni complesse tra parametri. È appropriata quando i parametri sono ben stimati e con bassa incertezza, oppure quando si desidera un’analisi diagnostica veloce.

La **sensitivity globale** esplora invece l’intero dominio parametrico $p \in \Omega$, senza assumere linearità locale. I parametri sono trattati come variabili che variano su intervalli assegnati (spesso con distribuzioni di probabilità), e si analizza la variabilità dell’output indotta da tali variazioni. In molti approcci, l’influenza di un parametro è quantificata tramite la frazione di varianza dell’output che esso spiega:
$$
Var(y) = Var(g(p))
$$
L’interpretazione è quindi quella di una misura di **varianza spiegata**: si quantifica quanto ciascun parametro contribuisca alla variabilità complessiva dell’output. Questo approccio cattura non linearità, effetti soglia, saturazioni e interazioni tra parametri, ma richiede campionamento e simulazioni multiple, risultando più costoso computazionalmente. È indicato quando i parametri sono incerti o variano su intervalli ampi, oppure quando il modello presenta dinamiche fortemente non lineari o comportamenti di tipo switch.

![[IMG - local vs global sensitivity analisys.png]]