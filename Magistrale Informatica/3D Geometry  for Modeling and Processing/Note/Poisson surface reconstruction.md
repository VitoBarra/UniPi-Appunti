---
Course: "[[3D Geometry for Modeling and Processing (3GMP)]]"
tags:
  - 3GMP
Area: 
topic: 
SubTopic: 
---

# Poisson surface reconstruction
---
Il **Poisson surface reconstruction** è un metodo di [[Ricostruzione di superfici del mondo reale con rappresentazioni point base|ricostruzione di superfici]] che si distingue per robustezza e stabilità numerica.  si costruisce di una **funzione indicatrice** a partire da una [[Point Cloud (nuvola di punti)|nuvola di punti orientata]].

La **funzione indicatrice** $\chi(x)$ è definita come:$$
\chi_M(x) =
\begin{cases}
1 & \text{if } x \in  M \\
0 & \text{se } x \not\in  M
\end{cases}
$$L'obiettivo è quindi quello di trovare una funzione $\chi_M$ il cui gradiente $\nabla \chi_M$ sia quanto più vicino possibile al campo delle normali $\vec{n}$ associate ai punti della nuvola. Questo si formalizza come un problema di minimizzazione:
$$
\min_{\chi}  \left\| \nabla \chi_M(x) - \vec{V}(x) \right\|$$
dove $\vec{V}(x)$ è un campo vettoriale che approssima le normali orientate della superficie. L’approccio sfrutta il fatto che $\nabla \chi$ è significativo solo lungo la superficie, dove assume direzione e verso coerenti con le normali della superficie stessa.


![[IMG - da nuvola di punti orientati a funzione indicatrice.png]]

![[IMG - relazione point cloud orientati e gradiente della funzione indicatrice.png]]

Per costruire $\vec{V}(x)$ a partire da una nuvola di punti orientati, si utilizza una struttura dati ad **[[Indici Spaziali - Quad-Tree e Oct-Tree|octree]]**. Il campo vettoriale viene ottenuto per accumulazione locale delle normali all’interno delle celle dell’octree, pesando ciascun contributo in base alla densità dei punti presenti nella cella stessa. Questo processo produce una rappresentazione adattiva del campo delle normali, ben definita solo nelle regioni dove i dati sono affidabili.

Una volta ottenuto il campo vettoriale $\vec{V}$, il problema si riduce alla risoluzione di un’equazione di Poisson:
$$
\Delta \chi = \nabla \cdot \vec{V}
$$
Questa formulazione consente di applicare tecniche numeriche consolidate per la risoluzione di equazioni ellittiche con condizioni al contorno, sfruttando anche il parallelismo tra le celle dell’octree, ciascuna trattabile in modo indipendente.
![[IMG - esempio punti orientati (cavallo).png]]

![[IMG - esempio punti orientati con oct-tree (cavallo).png]]

![[IMG - esempio complete con tutti i passaggi (cavallo).png]]