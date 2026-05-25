---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
  - ML
Area: Deep Learning for Graph
topic: Models
SubTopic: Reservoir graph models
---

# Graph Echo State Network
La **Graph Echo State Network** trasferisce l'idea delle [[Reservoir Computing - Echo State Network (ESN)|echo state network]] al dominio dei grafi. Il principio resta invariato: la dinamica interna, cioe il reservoir, non viene addestrata end-to-end ma viene inizializzata casualmente sotto vincoli di stabilita, mentre il training riguarda soprattutto il readout.

Si definisce per ogni nodo $v$ uno stato latente $h_v^{(l)}$ che dipende dall'informazione locale e dagli stati dei vicini. Se $L_j(v)$ rappresenta le feature del nodo, $\hat{W}$ la dinamica ricorrente del reservoir e $\overline{w}_{l_j}$ i pesi di input fissati, una forma tipica e
$$
h_v^{(l)}=\tanh\left(\sum_{j=0}^{L^v}\overline{w}_{l_j}L_j(v)+\sum_{u \in N(v)}\hat{W}h_u^{(l-1)}\right).
$$
La formula rappresenta una dinamica ricorrente locale che propaga informazione sul grafo; operativamente, il reservoir costruisce embedding contestuali senza richiedere ottimizzazione dei pesi ricorrenti.

Una volta ottenuti gli stati nodali, si costruisce una rappresentazione del grafo e si applica un readout lineare o poco profondo. Se $X(h(g))$ indica la rappresentazione aggregata del grafo $g$ ottenuta dagli stati del reservoir e $\mathbf{W}_{out}$ il readout addestrabile, si scrive
$$
y(g)=\mathbf{W}_{out}X(h(g)).
$$
Il significato operativo e che la parte complessa della dinamica viene mantenuta fissa, mentre l'apprendimento si concentra sulla mappa finale verso l'output.

La Graph Echo State Network e utile quando si vogliono ridurre tempi di addestramento e costo computazionale rispetto a modelli ricorrenti completamente addestrati. In cambio, l'espressivita dipende molto dalla qualita del reservoir iniziale e dalla capacita del readout di sfruttare gli stati generati.

Proprieta chiave:
- estende il reservoir computing al dominio dei grafi
- non addestra end-to-end la dinamica ricorrente interna
- separa costruzione degli embedding e apprendimento del readout
- privilegia efficienza e stabilita rispetto a piena adattivita


### Graph Echo state network
La [[Graph Echo State Network]] e l'approccio alle reti per grafi basato su reservoir randomizzati e su [[Reservoir Computing - Echo State Network (ESN)|Echo State Network]], dove si usa un vettore di stato $h$ per il reservoir.
$$\begin{cases}

\mathbf{h}_v^{(l)}=\tanh\left( \sum^{L^v}_{j=0}\overline{w_{l_j}}L_j(v) + \sum_{u\in  N(v)  } \hat{W}h_u^{(l-1)}\right) \\
y(\mathbf{g})=\mathbf{W}_{out}X(\mathbf{h}(\mathbf{g}))
\end{cases}
$$
![[IMG - Dynamical System.png]]
