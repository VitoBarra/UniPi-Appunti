---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# GRN - inferenza - GENIE3
---
**GENIE3 (GEne Network Inference with Ensemble of trees)** è un metodo di **[[Concetti generali del Machine Learning|machine learning]]** per l’[[GRN - inferenza|inferenza]] delle [[Gene Regulatory Networks (GRN)|GRN]] che formula il problema della ricostruzione della rete come una serie di problemi di **[[Algoritmi di learning supervisionato|regressione supervisionata]]**.

L’idea centrale è stimare l’espressione di ciascun gene target a partire dall’espressione degli altri geni, interpretando i possibili regolatori come **variabili predittive**.

Dato un insieme di $n$ geni e una **expression matrix**$$X\in\mathbb{R}^{m\times n}$$dove:
- $m$ è il numero di esperimenti
- $n$ è il numero di geni
- $x_{ij}$ rappresenta l’espressione del gene $j$ nell’esperimento $i$

l’algoritmo considera ogni gene $g$ come **target gene** e costruisce un modello predittivo:$$y_g = f(X_{-g})$$dove:
- $y_g$ è il vettore delle espressioni del gene $g$
- $X_{-g}$ rappresenta l’espressione di tutti gli altri geni
Il modello $f$ viene appreso tramite **[[Random Forest|Random Forest]]** o altri [[Ensemble Learning|ensemble]] di **decision trees**.

In una Random Forest:
- ogni albero apprende una funzione che predice l’espressione del gene target
- ad ogni nodo dell’albero viene selezionata una variabile predittiva che massimizza la riduzione dell’errore

Durante l’addestramento è possibile stimare l’**importanza delle variabili**, che misura quanto ciascun gene contribuisce alla predizione del gene target. Se $X_r$ rappresenta l’espressione del gene regolatore candidato $r$, il peso dell’interazione regolatoria viene definito come$$w_{r,g}\propto importance(X_r \Rightarrow y_g)$$Questo valore riflette quanto la variabile $X_r$ è rilevante nel predire l’espressione del gene $g$.  Ripetendo il processo per tutti i geni target si ottiene una matrice di pesi$$W=(w_{ij})$$dove $w_{ij}$ rappresenta l’importanza del gene $i$ nella predizione del gene $j$.

La matrice $W$ definisce una rete regolatoria pesata in cui:
- i nodi rappresentano geni
- gli archi $i\rightarrow j$ indicano una possibile regolazione
- il peso dell’arco rappresenta la forza dell’influenza stimata
Per ottenere la rete finale è possibile applicare una soglia sui pesi oppure selezionare gli archi con importanza più elevata.
![[IMG - GRN - inferenza - GENIE3.png]]
  
Dal punto di vista computazionale l’algoritmo addestra un modello di regressione indipendente per ogni gene target utilizzando come predittori i **possibili regolatori**.  
  
Siano:  
- $p$ numero totale di geni  
- $K$ numero di regolatori candidati  
- $T$ numero di alberi nella [[Random Forest|Random Forest]]  
- $N$ numero di campioni  
  
Addestrando una foresta per ciascun gene bersaglio il costo computazionale complessivo è approssimativamente:  
$$O(p \times K \times T \times N\log N)$$  
Struttura computazionale dell’algoritmo:  
- per ogni gene target $g_j$ viene addestrata una [[Random Forest|Random Forest]] che predice l’espressione di $g_j$  
- le variabili di input sono le espressioni dei $K$ regolatori candidati  
- l’importanza delle variabili negli alberi produce i punteggi regolatore $\rightarrow$ target  
  
Problema di scalabilità:  
- se non si limita l’insieme dei regolatori allora $K \sim p$  
- la complessità diventa quindi approssimativamente quadratica in $p$  
  
Strategie di riduzione della complessità:  
- filtrare i geni mantenendo solo un sottoinsieme ad alta varianza per ridurre $p$  
- limitare i regolatori ai fattori di trascrizione per ridurre $K$  
- sfruttare il parallelismo intrinseco addestrando i modelli su processori multi-core  
  
Dopo il calcolo dei punteggi regolatore–target la rete viene costruita a partire dalla matrice dei pesi $W$:  
- applicazione di una soglia globale (ad esempio quantile) oppure selezione dei top-$k$ archi per gene target  
- costruzione del grafo diretto pesato della rete regolatoria  
- rimozione degli auto-archi ($i \rightarrow i$)  
- eventuale filtraggio degli archi mantenendo solo relazioni [[fattore di trascrizione|TF]] $\rightarrow$ gene target