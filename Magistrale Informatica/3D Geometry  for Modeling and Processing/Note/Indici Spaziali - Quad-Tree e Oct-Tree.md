---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
Course 2: "[[Computer Grafica (CG)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Indici Spaziali - Quad-Tree e Oct-Tree
---
I **Quad-Tree** (2D) e gli **Oct-Tree** (3D) sono [[Indici spaziali|Indici spaziali]] **gerarchici**, basati su [[Alberi|alberi]].

Per costruire un **Quad-Tree**, lo spazio viene [[Partizione di un insieme|partizionato]] ricorsivamente in sotto-regioni. Ogni nodo dell’[[Alberi|albero]] rappresenta una regione; se ha figli, ognuno di essi rappresenta una sotto-regione del nodo padre.  

Ogni nodo ha esattamente $4$ figli (Quad-Tree) o $8$ (Oct-Tree) se necessario. I figli vengono aggiunti solo se la regione contiene troppe [[Computer grafica - Primitive Geometriche|primitive]], superando una certa soglia. Le regioni vuote restano intatte: la struttura è quindi **adattiva**.
![[IMG - indici spaziali Quad-tree.jpeg]]

Esistono due varianti principali di Quad-Tree:
- **Region Quad-Tree**: le 4 sotto-regioni hanno uguale area e centro fisso.
- **Point Quad-Tree**: le regioni sono determinate da una primitiva (punto), usata come centro per suddividere lo spazio.
![[IMG - Indici spaziali quad-tree 2D.png]]

Sono solitamente usati per memorizzare terreni![[IMG - Indici spaziali Quad-tree uso per terreni.png]] e sono facilmente usabbili anche in 3D![[IMG - Octa-tree uso.png]]


##### dettagli implementativi
I vantaggi dei **Quad-Tree** e **Oct-Tree** risiedono nella loro struttura implicita: posizione e dimensione delle celle sono determinate automaticamente dalla gerarchia.

È possibile rappresentare l'albero in un array lineare, evitando puntatori espliciti. Se la gerarchia è completa, l'esplorazione risulta semplice ed efficiente:

- In un **Quad-Tree**, i figli del nodo $i$ si trovano agli indici da $4i+1$ a $4i+4$, e il genitore è $\lfloor i/4 \rfloor$.
- In un **Oct-Tree**, i figli del nodo $i$ si trovano agli indici da $8i+1$ a $8i+8$, e il genitore è $\lfloor i/8 \rfloor$.

Queste relazioni aritmetiche ottimizzano l'accesso e la navigazione.

Un'altra tecnica consiste nel mappare la struttura in array bidimensionali ordinati secondo la **Z-Filling Curve** (o **Morton Ordering**), rendendola più [[Cache|cache friendly]].

Senza questo ordinamento, l'accesso alla memoria è efficiente solo lungo una direzione (es. righe o colonne), mentre risulta inefficiente nell'altra. Usando invece la Z-Filling Curve, si garantisce una buona **località spaziale** in entrambe le direzioni, aumentando la probabilità di cache hit.

L’accesso alla struttura avviene tramite **interleaving** dei bit degli indici $(x, y)$, ottenendo così l’indice lineare nell’array secondo l’ordine di Morton.

![[IMG - Z-Filling curve.jpeg]]



