---
Course: "[[Algebra Lineare (AL)]]"
topic: 
tags:
  - AL
---
# Base Ortogonale e Ortonormale
---
_sia_ $V$ uno [[Spazio Vettoriale|Spazio vettoriale]] munito di [[Prodotto Scalare|prodotto scalare]]
_allora_ Una _base Ortogonale_ di $V$  è una [[Base di uno spazio vettoriale|base]] dove tutti i _[[Vettori Ortogonali|vettori sono ortogonali]]_ tra loro, ovvero vale che $$\langle v_i,v_j\rangle=0 \ \forall i\not=j$$
e' detta _ortonormale_ il prodotto scalare e' definito positivo e se il numero $g(v_i,v_i)$ é 1,0,-1

### Teorema di Sylvester (Esistenza)
esiste sempre una _base ortogonale_ per uno [[Spazio Vettoriale|spazio vettoriale]] 

### Normalizzazione
una volta trovata una base possiamo sempre renderla _ortogonale_ sostituendo i vettori con questo criterio
$$W_i=\begin{cases}
\ \ \ \ \ \ \ \ v_i & if  & \langle v_i,v_i\rangle =0 \\
\displaystyle \frac{v_i}{\sqrt{ |\langle v_i,v_i\rangle }|}  &  else &
\end{cases}$$