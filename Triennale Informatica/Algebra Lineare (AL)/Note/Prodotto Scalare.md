---
Course: "[[Algebra Lineare (AL)]]"
topic: nota
tags:
  - AL
---
# Prodotto Scalare
---
__sia__ $V$ una [[Spazi Vettoriali|spazio vettoriale]]
__allora__ Il __prodotto scalare__ e un [[Operazioni algebriche|operazione]] su $V$ e definito come 
$$\begin{array}{}
V \times V \rightarrow \mathbb{R} \\
(v,w)\mapsto\langle v,w\rangle
\end{array}$$
e questa soddisfa i seguenti _assiomi_
1. $\langle v+v',w\rangle=\langle v,w\rangle+\langle v',w\rangle$
2. $\langle\lambda v,w\rangle=\lambda\langle v,w\rangle$
3. $\langle v,w+w'\rangle=\langle v,w\rangle+\langle v,w'\rangle$
4. $\langle v,\lambda w\rangle=\lambda\langle v,w\rangle$
5. $\langle v,w\rangle=\langle w,v\rangle$
per ogni $v,v',w,w' \in V$ e ogni $\lambda \in \mathbb{R}$

### Classificazione prodotti scalari:

**Prodotto scalare degenere e definito positivo.** Introduciamo ora due importanti assiomi aggiuntivi.

**Definizione 7.1.2.** Un prodotto scalare su $V$ e:

- _degenere_ se esiste $v \neq 0$ tale che $\langle v, w \rangle = 0$ per ogni $w \in V$;
- _definito positivo_ se $\langle v, v \rangle > 0$ per ogni $v \in V$ non nullo.

I due assiomi appena introdotti sono mutuamente esclusivi.

**Proposizione 7.1.3.** Un prodotto scalare definito positivo non e degenere.

**Altri tipi di prodotti scalari.** Oltre a _degenere_ e _definito positivo_, esistono altri aggettivi che descrivono alcune proprieta che puo avere un dato prodotto scalare.

**Definizione 7.1.28.** Un prodotto scalare su $V$ e:

- _semi-definito positivo_ se $\langle v, v \rangle \geq 0$ per ogni $v \in V$;
- _definito negativo_ se $\langle v, v \rangle < 0$ per ogni $v \in V$ non nullo;
- _semi-definito negativo_ se $\langle v, v \rangle \leq 0$ per ogni $v \in V$;
- _indefinito_ se esistono $v$ e $w$ per cui $\langle v, v \rangle > 0$ e $\langle w, w \rangle < 0$.

**Esercizio 7.1.29.** Consideriamo una matrice diagonale $D$, con elementi $d_1, \dots, d_n$ sulla diagonale. Il prodotto scalare $g_D$ e:

- _semi-definito positivo_ $\iff d_i \geq 0$ per ogni $i$;
- _definito negativo_ $\iff d_i < 0$ per ogni $i$;
- _semi-definito negativo_ $\iff d_i \leq 0$ per ogni $i$;
- _indefinito_ $\iff$ esistono $i$ e $j$ con $d_i > 0$ e $d_j < 0$.
