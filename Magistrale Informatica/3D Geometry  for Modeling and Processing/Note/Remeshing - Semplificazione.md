---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic:
---

# Remeshing - Semplificazione
---
Gli algoritmi di **[[Meshing e il Remeshing|remeshing]] per la semplificazione** consentono di trasformare una [[Mesh Poligonali|mesh]] complessa in una versione più semplice, riducendo il numero di triangoli senza compromettere eccessivamente la qualità dei dettagli. Questo è particolarmente utile quando una mesh contiene superfici planari rappresentate da un numero eccessivo di triangoli, anche in assenza di una reale necessità. Un caso tipico si verifica con l'algoritmo **[[Marching cube da superfici implicite a mesh|Marching cube]]**, il quale campiona la superficie in modo regolare, introducendo un elevato numero di triangoli anche in aree dove non sono strettamente necessari.
![[IMG - Remeshing Semplificazione.png]]


Una delle possibili applicazioni degli **algoritmi di semplificazione** è l'implementazione dei **Level of Detail (LOD)**, un concetto secondo cui il numero di triangoli di una mesh dovrebbe essere maggiore quanto più essa è vicina all'osservatore, ovvero quanto più pixel occupa sullo schermo. Questo perché, all'aumentare della distanza, i dettagli diventano comunque invisibili.![[IMG - level of detail.png]]
La relazione tra il numero di triangoli e l'accuratezza non è lineare: inizialmente è possibile ridurre la complessità senza introdurre **errori** significativi, ma oltre un certo punto, anche una piccola riduzione può causare distorsioni  evidenti.![[IMG - correlazione complessita e errore.png]]

in questo contesto l'errore di distorsione si può definire in due modi principali 
- di **similarità di apparenza**.
- di **similarità geometrica**


la **similarità di apparenza**  è complessa da definire siccome dipende fortemente dalle condizioni di  [[Algoritmi di renderizzazione|rendering]], quello che si fa solitamente è renderizare le due mesh in condizioni simili e poi usare gli algoritmi classici del [[Immage Processing|Immage Processing]] per guardare alle **Differenza tra due oggetti**. 
Un modo semplice per definire la differenza è la seguente: $$D(I_1, I_2) = \frac{1}{n^2} \sum_x \sum_y d(I_1(x,y), I_2(x,y))$$Questa formula calcola la distanza tra due immagini confrontando pixel per pixel tramite una funzione di differenza $d$.![[IMG - Similarita di apparenza.png]]


la **similarità geometrica** è invece piu facile da definire infatti si tratta da misurare una certa distanza $d$ tra le due mesh. Le distanze solitamente scelte sono di due tipi 
- $L_2$ la [[distanza euclidea|distanza euclidea]] media
- $L_{inf}$ la [[Norme Matriciali e Norme Vettoriali|norma infinita]] anche detta in questo contesto **distanza di Hausdorff** 
![[IMG - Distanza geometrica.png]]

La **distanza di Hausdorff** tra due [[Insiemi Matematici|insiemi]] $S_1$ e $S_2$ è definita come:$$D_H(S_1, S_2) = \max_{x \in S_1} \left( \min_{y \in S_2} d(x,y) \right)$$Questa pero non rispecchia la definizione di distanza infatti non è **simmetrica**, si puo pero definire una sua versione simmetrica come:$$D(S_1, S_2) = \max \{ D_H(S_1, S_2), D_H(S_2, S_1) \}$$![[IMG - Distanza di Hausdarff.png]]
Questa distanza pero è difficile da calcolare esattamente e quindi si approssima campionando in modo uniforme e denso gli insiemi $S_1$ e $S_2$.

la **distanza di Hausdorff** tende ad essere preferita perche piu rappresentativa ed è piu robusta, rispetto alla media, ai casi in cui i triangoli sono molti piccoli anche piu piccoli della distanza tra un campione e un altro. 




### Formalizzazione del problema di semplificazione 
Formalmente il problema di semplificare una [[Mesh Poligonali|mesh]] è definito come
**Sia** una [[Mesh Poligonali|mesh]]  $M = (V, F)$
**Obiettivo:** Trovare $M' = (V', F')$ tale che:
  - $|V'| = n < |V|$ e la distanza $\| M - M' \|$ sia minima, 
  oppure 
  - $\| M - M' \| < \epsilon$ e $|V'|$ sia minimo.


Trovare una soluzione a questo problema in particolare alla seconda forma del obiettivo è un problema di [[Complessita|complessità]] [[Classi di complessita - NP-hard|Np-Hard]], rendendolo quindi difficile da trattare. Quindi per risolvere il problema lo si usa usando delle euristiche.

Generalmente le soluzioni con euristiche funzionano bene tranne nei casi in cui ci sono pochi poligoni ma è una casistica non critica perche non ha comunque senso cercare un errore basso, e quindi preservare i dettagli, quando i dettagli non ci sono in ogni caso.

Uno degli algoritmi principali che risolve questo problema è l'[[Algoritmo di Remeshing semplificazione - Collapse|edge Collapsing]]




