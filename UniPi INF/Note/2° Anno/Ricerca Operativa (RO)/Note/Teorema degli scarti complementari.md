---
type: nota
course: Ricerca Operativa
topic: 
tags: RO
---

Prev: [[Ricerca Operativa (RO)]]

# Teorema degli scarti complementari
---
**_Teorema_**
supponiamo che $\overline{x}$ sia una soluzione ammissibile del del primale $(\mathcal{P})$ allora $\overline{x}$  è ottima se e solo se esiste una soluzione $\overline{y}$ del sistema



$$
\begin{cases}
\overline{y}^TA=c^T \ \ \ \ \ \ \ \ \ \ \ \ \  \text{(ammisibilita }\\
\overline{y} \geq 0 \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \  \text{duale)}\\
\overline{y}^T(b-A\overline{x}) =0
\ \ \ \ \ \ \ \overline{x} \ e \ \overline{y} \text{ sono in scarti complementari}
\end{cases}
$$

Qualunque soluzione $\overline{y}$ di questo sistema è una soluzione ottima del duale $(\mathcal{D})$

