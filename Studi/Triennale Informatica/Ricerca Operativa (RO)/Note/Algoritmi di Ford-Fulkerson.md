---
Subject: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic:
---


# Algoritmi di Ford-Fulkerson
---

### *Teorema*
Se le capacita degli archi di un [[Struttura dati - Grafo|grafo]] sono intere, allora l [[Algoritmi|algoritmo]] di Ford-Fulkerson trova un flusso di valore massimo dopo un numero finito di iterazioni.
al ultima iterazione un taglio di capacita minima $(N_n,N_t)$ si può calcolare nel modo seguente:

$N_s =\{i\in N \ |$  esiste in $G(x)$ un cammino orientato da $s$  a  $i\}$

$N_t =\{i\in N \ |$  non esiste in $G(x)$ un cammino orientato da $s$  a  $i\}$

un altro taglio di capacita minima $(N_s',N_t')$ si può ottenere nel modo seguente

$N_s' =\{i\in N \ |$ non  esiste in $G(x)$ un cammino orientato da $i$ a  $t\}$

$N_t' =\{i\in N \ |$  esiste in $G(x)$ un cammino orientato da $i$ a  $t\}$

un taglio di capacita minima è unico se e solo se i due tagli precedenti coincidono

### Dimostrazione
segue dalla [[Condizione di Ottimalità Max flow - Min cut]]

### *Algoritmo*

1. Poni $x =0$ (flusso nullo su tutti gli archi) e $G(x)=G$
2. se esiste un cammino aumentate $C$ rispetto ad $x$ allora aggiorna il flusso
    1. calcola $\delta = \min \{r_{ij}:(i,j)\in C\}$ (max quantità da spedire lungo $C$)
    2. per ogni $(i,j) \in C$ allora $x_{ij}=x_{ij}+\delta$
    3. per ogni $(j,i) \in C$ allora $x_{ij}=x_{ij}-\delta$
3. aggiorna il grafo residuo $g(x)$ e torna al passo 2.

>[!info]- Spiegazione ad alto livello
>Ad ogni iterazione cerca un cammino aumentante rispetto al flusso corrente
>
>Se Esiste un cammino aumentante l algoritmo aggiorna il flusso spedendo su tale cammino il massimo flusso possibile pari alla minima capacita residua degli archi di tale cammino
>
>se non esiste un cammino aumentante l algoritmo si ferma perché il flusso corrente è di valore massimo. Inoltre l algoritmo trova anche un taglio di capacita minima 


### problematiche

![[UniPi-Appunti/Studi/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 1 13.png]]

![[UniPi-Appunti/Studi/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 2 8.png]]

![[UniPi-Appunti/Studi/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 3 6.png]]

![[UniPi-Appunti/Studi/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 4 4.png]]