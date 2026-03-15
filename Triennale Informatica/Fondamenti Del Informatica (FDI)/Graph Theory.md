---
Course: "[[Fondamenti Del Informatica (FDI)]]"
tags:
  - FDI
Area:
SubTopic:
---

# Graph Theory
---
La **Graph Theory** è un ramo della matematica discreta che studia le proprietà strutturali dei **grafi**, oggetti matematici utilizzati per rappresentare relazioni tra entità discrete. 
Un **grafo** è formalmente definito come una tupla: $$G=(V,E)$$dove $V$ è l’insieme dei **vertici (nodi)** ed $E \subseteq V \times V$ l’[[Insiemi Matematici|insieme]] degli **archi (edges)** che collegano coppie di vertici, le connessioni sono ordinate quindi **orientate** (nel qual caso il grafo è detto **orientato**) o **non orientati** se vale la proprietà [[Relazioni tra insiemi|simmetrica]]
La teoria dei grafi analizza proprietà **topologiche** e [[Combinatoria|combinatorie]] delle reti indipendentemente dal dominio applicativo in cui esse emergono.
![[IMG - Esempio grafo complesso.png]]

## Definizioni fondamentali

###### **Grado di un vertice**
Il **grado** di un vertice $v$ misura il numero di archi incidenti sul vertice.
- Grafo **non orientato**:  
  $\deg(v)$ = numero di archi incidenti a $v$
- Grafo **orientato**:
  - $\deg^+(v)$ = **grado uscente**
  - $\deg^-(v)$ = **grado entrante**

---
###### **Cammino**
Un **cammino** è una sequenza di vertici  
$(v_1, v_2, ..., v_k)$  
tale che ogni coppia consecutiva $(v_i, v_{i+1})$ è collegata da un arco del grafo.
Un **cammino semplice** è un cammino in cui **tutti i vertici sono distinti**.

---
###### **Ciclo**
Un **ciclo** è un cammino che inizia e termina nello stesso vertice e in cui nessun altro vertice viene ripetuto.

---
###### **Distanza**
La **distanza** tra due vertici $u$ e $v$ è la lunghezza del **cammino minimo** che li collega: $d(u,v)$

---
###### **Diametro**
Il **diametro** di un grafo è la distanza massima tra tutte le coppie di vertici:$$\text{diam}(G) = \max\{d(u,v) \mid u,v \in V\}$$

---
###### **Taglio**
Un **taglio** è una partizione dell’insieme dei vertici in due sottoinsiemi disgiunti $S$ e $T$.  
Gli archi che collegano vertici appartenenti ai due insiemi sono detti **archi del taglio**.

I tagli sono fondamentali in problemi di ottimizzazione sui grafi, come il problema del **minimum cut**.

---

## Tipi di grafi

###### **Grafo completo**
Un **grafo completo** $K_n$ è un grafo in cui ogni coppia di vertici è collegata da un arco. Numero di archi: $$|E| = \binom{n}{2} = \frac{n(n-1)}{2}$$

---
###### **Grafo connesso**
Un grafo è **connesso** se per ogni coppia di vertici esiste un cammino che li collega:
$\forall u,v \in V, \exists$ cammino tra $u$ e $v$

---

###### **Grafo bipartito**
Un grafo è **bipartito** se l’insieme dei vertici può essere diviso in due sottoinsiemi disgiunti:$$V = V_1 \cup V_2$$con$$V_1 \cap V_2 = \emptyset$$e gli **archi collegano** solo vertici appartenenti a insiemi diversi.

---

## Misure strutturali

###### **Coefficiente di clustering**
Il coefficiente di clustering di un vertice misura quanto i suoi vicini sono interconnessi: $$C(v) = \frac{2T(v)}{\deg(v)(\deg(v)-1)}$$dove $T(v)$ è il numero di triangoli incidenti sul vertice $v$.

---

###### **Centralità**
Le misure di **centralità** quantificano l’importanza di un nodo nella rete.

- **Betweenness centrality** $$C_B(v) = \sum_{s \neq v \neq t} \frac{\sigma_{st}(v)}{\sigma_{st}}$$
dove $\sigma_{st}$ è il numero di cammini minimi tra $s$ e $t$ e $\sigma_{st}(v)$ quelli che passano per $v$.
- **Closeness centrality** $$C_C(v) = \frac{1}{\sum_{u \neq v} d(v,u)}$$