---
Course: "[[Generative and Deep Learning (GDL)]]"
tags:
  - GDL
Area:
topic:
SubTopic:
---

# Meccanismo del message passing
---
## Message passing
Il **Deep Learning for Graph** converge oggi nel paradigma del **message passing**, cioe nella famiglia delle [[Message Passing Neural Network (MPNN)|Message Passing Neural Networks]] e, piu in generale, delle [[Deep Graph Networks (DGN)]], in cui ogni layer e un round locale di comunicazione. Se $h_v^{(k)}$ e l'embedding del nodo $v$ allo step $k$ e $\mathcal{N}(v)$ il suo vicinato, si definisce prima il messaggio aggregato
$$
m_v^{(k)}=\mathrm{AGG}\left(\{h_u^{(k)}:u \in \mathcal{N}(v)\}\right)
$$
e poi l'aggiornamento
$$
h_v^{(k+1)}=\mathrm{UPDATE}\left(h_v^{(k)},m_v^{(k)}\right).
$$
La prima formula rappresenta la sintesi del vicinato, la seconda la fusione tra stato corrente e contesto; operativamente, dopo $K$ layer il nodo dipende in generale dai nodi entro distanza $K$, cioe il **receptive field** cresce con la profondita. Una formulazione equivalente separa esplicitamente il contributo dei vicini da quello del nodo stesso:
$$
h_v^{(l)}=\sigma\left(W^{(l)}\,\mathrm{AGG}\left(\{h_i^{(l-1)}:i \in N(v)\}\right)+\hat{W}^{(l)}h_v^{(l-1)}\right)
$$
dove $W^{(l)}$ trasforma l'informazione aggregata, $\hat{W}^{(l)}$ il contributo auto-riferito e $\sigma$ la non linearita; operativamente, il modello separa informazione locale e informazione contestuale. ![[IMG - Graph message passing.png]]
![[IMG - message passing congregatore a dimensoine variabile.png]]
![[IMG - message passing su grafi di diverso tipi.png]]

Il **Deep Learning for Graph** dipende in modo cruciale dall'aggregatore, perche il vicinato e un multinsieme non ordinato e `AGG` deve essere permutation invariant. Somma, media e massimo sono le scelte classiche, ma non hanno la stessa espressivita: la somma preserva la molteplicita delle occorrenze, mentre media e massimo possono collassare multinsiemi distinti nello stesso output. Operativamente, la scelta dell'aggregatore determina la capacita del modello di contare pattern locali e distinguere strutture, ed e alla base di architetture come la [[Graph Convolutional Network (GCN)|Graph Convolutional Network]] quando l'aggregazione viene incorporata in operatori convolutivi su grafo, come generalizzazione delle [[Convolutional Neural Network (CNN)|convolutional neural network]] a domini non regolari.


Le [[Deep Graph Networks (DGN)]] formalizzano il quadro generale dei modelli neurali per grafi. L’idea centrale dei DGN è il **Message Passing**, un processo iterativo che permette ai nodi di aggiornare il proprio stato in base alle informazioni ricevute dai vicini.
 Passaggi fondamentali:
1. Ogni __nodo__ calcola un __messaggio__ come funzione della sua __label__, dei suoi vicini $\mathcal{N}_v$ e delle sua connessioni, manda il messaggio a tutti i suoi vicini.
2. I __nodi__ che ricevano i messaggi li aggregano con una funzione __invariante alla permutazione__ ovvero non cambia con l ordine di arrivo dei messaggi.
3. Il nodo aggiorna il proprio __stato__ combinando i messaggi con pesi liberi $W$

L’iterazione del processo di Message Passing permette di diffondere l’informazione tra tutti i nodi del grafo.
![[IMG - Message passing On SDL.png]]

Lo stato non dipende solo dal vicinato locale $\mathcal{N}_v$: le iterazioni di questo meccanismo MP permettono la diffusione delle informazioni tra tutti i nodi, raggiungendo tutti gli altri.  

Infine, è possibile emettere un output __per ciascun nodo__ o __per l'intero grafo__ attraverso un'aggregazione invariante alla permutazione delle rappresentazioni dei nodi, nota anche come __global pooling__

Piu formalmente abbiamo che:
$$\mathbf{h}_v^{(l)}= AGG_{\mathbf{W}^{(l)}}(L_vh_u^{(l-1)},\{h_u^(l-1): u \in  \mathcal{N}(v)\}) \ \ l= 1,\dots L$$dove:
- $AGG_{\mathbf{W}^{(l)}}$  aggrega (propaga) i __messaggi__ dai nodi vicini, includendo un operatore invariante per permutazione sull'insieme dei vicini (ad esempio, una somma) e combinazioni delle attivazioni delle unità della rete neurale in $h$, dove $\mathbf{W}$ sono i parametri liberi del modello. 
- $L_v$ rappresentano le etichette dei nodi.  
- $\mathcal{N}$ è definito in base alla matrice di adiacenza $A$ del grafo.

- Applicare questo calcolo a ciascun nodo del grafo corrisponde a una visita parallela e non ordinata del grafo a ogni iterazione $l$.
Abbiamo una grande flessibilità nell'implementazione di questi operatori, con molte variazioni di modello disponibili.
- $\mathbf{h}^{(l)}=relu(\hat{A}h^{l-1}W^{(l)})\hat{A}$ (GCN)
- $\mathbf{h}^{(l)}=f(W^{(l)}_1h^{l-1}+W^{(l)})Ah^{l-1}$



