---
type: nota
course: Data Base
topic: 
tags:
  - FDI
Parent MOC: "[[Data Base (DB)]]"
---

# Dipendenze funzionali nei DB
---
Le _dipendenze funzionali_ sono una _formalizzazione_ del concetto di vincolo dei dati su un altro dato.
questo _formalismo_ è necessario per analizzare la qualità di un [[Introduzione ai Data Base|Database]] e per poterlo trasformare in [[Normalizzazione di schemi relazionali|forma normale]]  

#### Dipendenza funzionale (Definizione)
_Sia_ 
- una schema di [[Relazioni tra insiemi|relazione]] $R(T)$
- $X$ e $Y$ sottoinsiemi di attributi di $T$ 
_allora_ una _dipendenza funzionale_ è un [[Modellazione della conoscenza#Conoscenza concreta|vincolo di integrita]] sulle istanze della relazione tale che$$ 
\begin{array}{}
X \rightarrow Y  & \iff &  \forall t_{1},t_{2} \in  r,t_{1}[X]=t_{2}[X] \\
 & \implies &  t_{1}[Y]=t_{2}[Y] 
\end{array}
$$ 
 
