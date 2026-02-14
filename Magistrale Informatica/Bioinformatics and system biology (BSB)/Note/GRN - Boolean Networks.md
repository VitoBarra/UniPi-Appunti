---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GRN Boolean Networks
---
I **Boolean networks** sono uno dei modelli più comuni per rappresentare una [[Gene Regulatory Networks (GRN)|GRN]]. In questo modello ogni gene è rappresentato da una variabile booleana $x_i(t)\in\{0,1\}$ che descrive lo stato di attivazione del gene al tempo $t$.

Formalmente una **Boolean Network (BN)** è definita come una coppia:$$BN=(G,F)$$dove:
- $G=\{g_1,g_2,\dots,g_n\}$ è l’insieme dei geni (nodi)
- $F=\{f_1,f_2,\dots,f_n\}$ è l’insieme delle **funzioni di aggiornamento booleane**, una per ogni gene
Ad ogni istante discreto $t$ la rete si trova in uno stato globale:
$$x(t)=(x_1(t),x_2(t),\dots,x_n(t))\in\{0,1\}^n$$
che rappresenta la configurazione di attivazione di tutti i geni della rete.

In questo modo la struttura delle [[Gene Regulatory Networks (GRN)|GRN]] ovvero il grafo delle influenze viene arricchita con una **semantica dinamica** espressa da $F$, cioè con una regola precisa che stabilisce come lo stato dei geni regolatori determini lo stato del gene target al passo temporale successivo.

Le **Boolean Networks** sono **più espressive** della loro controparte grafica classicamente usata per i [[Gene Regulatory Networks (GRN)|GRN]]. Un grafo regolatorio standard indica solamente che un gene **influenza** un altro gene (attivazione o inibizione), ma non specifica **come** le diverse influenze si combinino tra loro per determinare l’attivazione del gene target.
![[IMG - Boolean Networks esempio di GRN come boolean network.png]]
Nel caso mostrato i geni $A$ e $B$ **attivano** $X$, mentre $C$ **inibisce** $X$. Tuttavia il grafo non specifica quale sia la **regola logica** che determina lo stato di $X$.

La stessa struttura della rete può infatti corrispondere a diverse funzioni booleane. Il nodo $X$ quindi **non è definito in modo univoco dalla struttura del grafo**, perché il grafo descrive solo le **influenze tra geni**, ma non la **logica di combinazione** tra i regolatori.


L’evoluzione del sistema è descritta da una funzione booleana per ogni gene:
$$x_i(t+1)=f_i(x_1(t),x_2(t),\dots,x_n(t))$$
La funzione $f_i$ rappresenta la **combinazione logica** delle influenze dei geni regolatori sul gene $i$. Le relazioni regolatorie sono quindi modellate tramite [[Algebra booleana|operatori logici]] come **AND, OR e NOT**, che rappresentano rispettivamente cooperazione tra regolatori, attivazione alternativa e inibizione.

L’intero sistema evolve nel tempo aggiornando gli stati dei geni secondo queste funzioni logiche. L’aggiornamento può seguire due strategie.

- **Aggiornamento sincrono**  
tutte le funzioni booleane $f_i$ vengono valutate **in parallelo** ad ogni passo temporale. L’evoluzione della rete è quindi **deterministica**: da ogni configurazione esiste un solo stato successivo. La traiettoria del sistema è una sequenza deterministica: $x(0) \rightarrow x(1) \rightarrow x(2) \rightarrow \dots$

-  **Aggiornamento asincrono**  
ad ogni passo viene aggiornato **un solo nodo** (o un sottoinsieme di nodi) selezionato in modo non deterministico, rendendo l’evoluzione del sistema **non deterministica**. Uno stesso stato può quindi avere **più possibili successori**. Questo comportamento riflette meglio i sistemi biologici, in cui le reazioni avvengono con **tempi diversi**.

Le possibili evoluzioni del sistema possono essere rappresentate tramite uno **State Transition Graph (STG)** definito formalmente come:$$STG=(S,T)$$dove:
- $S=\{0,1\}^n$ è l’insieme di **tutti gli stati possibili** della rete
- $T \subseteq S \times S$ è l’insieme delle **transizioni ammesse** tra stati
Una transizione $(x,y)\in T$, indicata anche come $x \rightarrow y$, rappresenta il fatto che lo stato $y$ può essere ottenuto dallo stato $x$ aggiornando una variabile (o un sottoinsieme di variabili) secondo le funzioni di aggiornamento della rete.
Nel grafo:
- i **nodi** rappresentano gli stati della rete $x \in S$
- gli **archi** rappresentano le transizioni ammesse $x \rightarrow y \in T$
![[IMG - Boolean Networks semantica asincrona STG.png]]

Le due strategie di aggiornamento **non sono equivalenti** e possono produrre dinamiche differenti. Considerando ad esempio il sistema:$$\begin{array}{}
A=\neg B \\
B=\neg A
\end{array}
$$Te traiettorie ottenibili partendo da $(0,0)$ con questo sistema sono
- **Sincrono**: $(0,0)\rightarrow(1,1)\rightarrow(0,0)\rightarrow\dots$ che produce un **ciclo infinito**
- **Asincrono**:  $(0,0)\rightarrow(0,1)\rightarrow(0,1)\rightarrow\dots$  ovvero converge ad uno **stato stabile**
le due strategie portano quindi a **stati raggiungibili differenti**.

L’aggiornamento **asincrono** è spesso considerato più realistico dal punto di vista biologico, perché le reazioni chimiche avvengono con **velocità diverse** e in tempi differenti. Tuttavia l’aggiornamento **sincrono** è frequentemente utilizzato nei modelli perché produce una dinamica **deterministica**, rendendo più semplice l’analisi del comportamento della rete.

Poiché ogni gene può assumere solo due stati, una rete con $n$ geni possiede uno **spazio degli stati finito** di dimensione $|\{0,1\}^n|=2^n$. La dinamica del sistema evolve quindi su questo spazio discreto di configurazioni e, proprio perché lo spazio degli stati è finito, a partire da qualsiasi **configurazione iniziale** la dinamica della rete **converge** verso un **attrattore**, cioè un insieme di stati in cui il sistema **rimane intrappolato durante la sua evoluzione**

Gli attrattori sono particolarmente rilevanti perché rappresentano **configurazioni stabili di espressione genica** associate a specifici stati funzionali della cellula.

Formalmente, un **attrattore** è definito come:    
**dato** un **STG** $(S,T)$, un **attrattore** è un [[Insiemi Matematici|insieme]] non vuoto di stati $A \subseteq S$ tale che valgono le proprietà:  
- **Closure**  $\forall x \in A$, se $x \rightarrow y \in T$ allora $y \in A$  
- **Minimality**  non esiste un sottoinsieme proprio di $A$ che soddisfa la proprietà di chiusura  
Questa definizione è generale e si applica sia alla dinamica **asincrona** sia alla dinamica **sincrona**.  
  
Un attrattore può essere:  
- con un singolo stato: **stato stabile** (**punto fisso**)  
- con più stati: **ciclo** di configurazioni che si ripete periodicamente (**attrattore ciclico**)


Ogni **attrattore** è associato a un **bacino di attrazione** (*basin of attraction*), cioè l’insieme delle configurazioni iniziali che conducono a quell’attrattore.

Formalmente, dato un attrattore $A$, il suo **bacino di attrazione** è definito come:$$Basin(A)=\{x \mid \exists \text{ percorso } x \rightarrow^{*} y \text{ con } y \in A\}$$L’insieme contiene quindi tutti gli stati da cui è possibile raggiungere l’attrattore tramite **una o più transizioni** nello **STG**
![[IMG - Boolean Networks attrattori  basin of attraction.png]]

Nel caso di **dinamica sincrona**, l’evoluzione della rete è deterministica: da ogni stato esiste un unico successore. Di conseguenza, i bacini di attrazione dei diversi attrattori risultano **disgiunti**, perché ogni stato appartiene al bacino di un solo attrattore.

Nel caso di **dinamica asincrona**, invece, l’evoluzione è **non deterministica** e uno stato può avere più possibili successori. Per questo motivo i bacini di attrazione possono **sovrapporsi**, poiché uno stesso stato iniziale può condurre a **attrattori diversi** a seconda della sequenza di aggiornamenti considerata.



