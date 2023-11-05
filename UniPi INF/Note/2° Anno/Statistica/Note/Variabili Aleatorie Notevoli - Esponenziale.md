---
type: nota
course: Statistica
topic: 
tags:
  - STAT
Parent MOC: "[[Statistica (STAT)]]"
---
# Variabili Aleatorie Notevoli - Esponenziale
---

#### Variabili esponenziali
la _[[Variabili Aleatorie (Casuali)|variabile aleatoria]]_ con densita esponenziale di parametro $\lambda>0$ è definita come $$f(x)=\begin{cases}
	\lambda e^{-\lambda x} &  x>0 \\
    0  & x \leq 0
\end{cases}$$
e si vede che la densita è effettivamente una [[Definizione di Probabilita|probabilità]] con l espressone $$  \left .\int_{0}^{+\infty} \lambda e^{-\lambda x}  \, dx =-e^{-\lambda x}\right|_{0}^{+\infty}=1$$
poiché la densita prende valori diversi da $0$ solo per $x$ positivi si ha che $\mathcal{P}\{X \leq 0  \}=0$

>[!tip]
>la variabile esponenzioale descrive _ad esempio_ il tempo di attesa tra due eventi aleatori

##### Memoria della variabile (Teoria)
la _variabile esponenziale_ è _senza memoria_ e vale perciò che $$\mathcal{P}\{ X\leq s+t \mid X>s\} = \mathcal{P}\{ X \leq t \}$$
dove il $\mid$ è il simbolo per la [[Probabilita condizionata|probabilita condizionata]]
