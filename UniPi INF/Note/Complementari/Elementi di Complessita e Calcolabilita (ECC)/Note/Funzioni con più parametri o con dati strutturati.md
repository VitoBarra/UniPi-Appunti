
---
type: nota
course: Elementi di calcolabilita e complessita
topic: 
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Funzioni con più parametri o con dati strutturati
---
la [[Macchina di Turing]] e i [[Linguaggi FOR e WHILE]] possono [[Turing-Calcolabilita|calcolare]] una [[Funzioni|funzione]] con un solo parametro nei numeri naturali $\mathbb{N}$ ma questo non ci limita l utilizzo di più parametri e di dati strutturati siccome basta trovare una codifica di quei dati in un numero naturale.
La [[Funzioni|funzione]] di codifica deve essere una  [[Funzioni#Funzioni Biunivoche|funzioni biunivoca]] siccome devono essere [[Funzioni]] per rendere la decodifica non ambigua.

e si utilizzano come :
1. Dato $x$ in formato $A$ codificano come $y$ in formato $B$ utilizzabile Dalla macchia di Turing o dal linguaggio WHILE o FOR .
2. Applica la MDT a $y$ e se e qua di ottieni $z$ in formato $B$
3. Traduci $z$ dal formato $B$ al formato $A$

## Esempi
### calcolare funzioni in 2 variabili:
Per calcolare una funzione in 2 bisogna codificare i due numeri in unico numero quindi avere una funzione di decodifica del tipo $Co:\N \times \N \rightarrow \N$ 
In questo caso la funzione è:
$$ (x,y)\rightarrow \frac12 (x^2+2xy+y^2+3x+y) $$
E la sua funzione di decodifica è del tipo $DeCo:\N \rightarrow \N \times \N$  ed è :
$$n\rightarrow(n-\frac12k\times (k+1),k-(n-\frac12k\times(k+1)))$$
Dove 
$$k = \left\lfloor \frac12(\sqrt{1+8 n}-1) \right\rfloor$$
Questa codifica si può visualizzare con 
![[66CEA436-3E6E-44B8-80B1-D90A4890C489.jpeg]]
Dove x e y sono mappati sugli indici della matrice.


>[!note] Osservazioni
> Questo diversi modi di rappresentare i dati non cambia la nozione di [[Nozione di Calcolabilità|Calcolabilità]] Ovvero rappresentare i dati in formati diversi  non fa variare la classe delle funzioni calcolabili. Questo siccome si stra trasformato unafunzione che lavora su un tipo di dato in un altra che lavora su un altro tipo di dato equivalente  

