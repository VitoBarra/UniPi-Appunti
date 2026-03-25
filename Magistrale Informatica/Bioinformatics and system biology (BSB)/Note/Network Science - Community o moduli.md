---
Course: "[[Bioinformatics and Systems Biology (BSB)]]"
tags:
  - BSB
Area:
topic:
SubTopic:
---

# Network Science - Community o moduli
---
In [[Network Science|Network Science]] una **community** o **modulo** e un [[Insiemi Matematici|sottoinsieme]] di nodi di un [[Graph Theory|grafo]] che:
- sono **fortemente connessi tra loro**
- hanno **poche connessioni con il resto della rete**
L'identificazione dei moduli permette di analizzare il sistema a livello **mesoscopico**, tra il singolo nodo e l'intera rete.
![[IMG - Network Science - comunity.png]]

Si distinguono:
- **strong communities**: ogni nodo ha piu connessioni interne che esterne
- **weak communities**: il numero totale di connessioni interne e maggiore di quello delle connessioni esterne

### Network proximity
La **network proximity** indica quanto due community risultino vicine o separate nella rete. La nozione si basa sulle [[Definizione di distanza|distanze]] tra singoli nodi, dove $d(a,b)$ e la lunghezza del **cammino minimo** tra $a$ e $b$.

L'**average shortest path distance** e la media di tutte le distanze minime tra i nodi dei due moduli: $$d_{avg}(A,B)=\frac{1}{|A||B|}\sum_{a\in A}\sum_{b\in B}d(a,b)$$ Questa quantita e **simmetrica** e **non negativa**, ma in generale $d_{avg}(A,A)\neq 0$, quindi non e una distanza metrica tra moduli. Inoltre e sensibile alla presenza di [[Network Science|hub]], che tendono ad abbassare la media nascondendo i cammini piu lunghi e rari.

La **closest-path distance** misura invece, per ogni nodo di $A$, la distanza dal nodo piu vicino di $B$: $$d_c(A,B)=\frac{1}{|A|}\sum_{a\in A}\min_{b\in B}d(a,b)$$ Anche questa quantita e **non negativa**, ma non e in generale **simmetrica**, perche la media viene calcolata solo sui nodi di $A$. Se $A$ e piccolo e concentrato vicino a una porzione di $B$, mentre $B$ e piu esteso o disperso, si puo avere $d_c(A,B)<d_c(B,A)$.

La **separation** confronta la distanza media tra i due moduli con la loro compattezza interna e puo essere scritta riusando $d_{avg}$: $$s(A,B)=d_{avg}(A,B)-\frac{d_{avg}(A,A)+d_{avg}(B,B)}{2}$$ Se $s(A,B)<0$, i moduli risultano vicini o **parzialmente sovrapposti**, se $s(A,B)>0$, risultano **separati**.
