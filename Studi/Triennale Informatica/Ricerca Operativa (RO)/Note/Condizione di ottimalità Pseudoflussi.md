---
Course: Ricerca Operativa
topic: nota
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Condizione di ottimalità Pseudoflussi
---

### Condizione di ottimalità
ad ogni flusso $x$ associamo il [[Struttura dati - Grafo|grafo]] residuo $G(x) = (N,A')$ in cui l insieme degli archi $A'$ è cosi definito:
- se $(i,j) \in A$ con $x_{ij}<u_{ij}$ allora $(i,j) \in A'$ con capacita residua $r_{ij}=u_{ij}-x_{ij}$ e costo $c_{ij}'=c_{ij}$
-  se $(i,j) \in A$ con $x_{ij}>0$ allora $(j,i) \in A'$ con capacita residua $r_{ji}=x_{ij}$ e costo $c_{ji}'=-c_{ij}$

### Teorema 
Sia $x$ un flusso ammissibile $x$ è ottimo se e solo se in $G(x)$ non esistono cicli orientanti di costo negativo

#### Definizine 
Un ciclo orientato in G(x) è chiamato ciclo aumentante rispetto a x


![[UniPi-Appunti/Studi/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 1 5.png]]
