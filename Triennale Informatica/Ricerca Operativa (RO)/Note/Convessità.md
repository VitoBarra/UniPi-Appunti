---
Course: "[[Ricerca Operativa (RO)]]"
tags:
  - RO
topic:
---


# Convessità
---

### Combinazione convessa

Siano $\boldsymbol{x}_1,\dots,\boldsymbol{x}_m \in \mathbb{R}^n$ dei [[Vettori|vettori]]  
se esistono coefficienti $\lambda_1,\dots,\lambda_m \in [0,1]$ con $\sum_{i=1}^m\lambda_i=1$, tale che$$
\boldsymbol{x} =\sum_{i=1}^m \lambda_ix_i
$$Allora un vettore $\boldsymbol{x} \in \mathbb{R}^n$ è detto **combinazione convessa** 

la combinazione convessa è detta
- **propria** se $\lambda_1,\dots,\lambda_m \in (0,1)$
- **impropria** se $\lambda_1,\dots,\lambda_m \not\in (0,1)$

### Insieme Convesso
_Sia_ Un [[Insiemi Matematici|insieme]] $K \subseteq \mathbb{R}^n$  
_Se_ $\forall x,y   \in   \mathbb{K}  \land \forall \lambda \in [0,1]$ vale $$
\begin{array}
\lambda x+(1-\lambda)y   & \in &    \mathbb{K}  \\
\end{array}
$$_allora_ $K$ è detto **convesso**

in pratica se $K$ contiene due punti $x_1$ e $x_2$ allora contiene anche tutto il segmento di estremi $x_1$ e $x_2$ , segmento attenuto con [[Interpolazione Lineare|interpolazione lineare]]
![[UniPi-Appunti/Triennale Informatica/Ricerca Operativa (RO)/Media/Untitled 23.png]]

