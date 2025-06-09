---
Course: "[[Statistica (STAT)]]"
topic: nota
tags:
  - STAT
---
# Probabilità condizionata
---
preso uno _[[Definizione di Probabilità#Probabilità assiomatica secondo Kolmogorov (definizione)|spazio delle probabilità]]_ $(\Omega,\mathcal{F},\mathcal{P})$ conoscendo l’esito di un evento $B$ _non trascurabile_ si possono fare delle considerazioni su un _altro evento_ $A$ anche esse non trascurabile modificandone cosi la _[[Definizione di Probabilità|Definizione di Probabilità]]_
infatti abbiamo che la _Probabilità Condizionata_ di $A$ rispetto a $B$ è definita come$$
\mathcal{P}(A|B) = \frac{\mathcal{P}(A \cap B)}{\mathcal{P}(B)}
$$
ed è immediato notare che $$\mathcal{P}(A|B)\mathcal{P}(B)=\mathcal{P}(B|A)\mathcal{P}(A)$$
>[!example]-
>nel caso del uscita di un numero sulla rullette
>- $A = \{16\}$
>- $B =\{2,4,\dots,36\}$ cioè i numeri pari
>abbiamo che
>$$
>\mathbf{P}(A|B) = \frac{\mathbf{P}(A \cap B)}{\mathbf{P}(B)} = \frac{\frac{1}{37}}{\frac{18}{37}}=\frac{1}{18}
>$$

In _generale_ vale che presi  $A_1,\dots,A_n$ ovvero per $n$ _eventi_  e supponendo che $A_1 \cap\dots \cap A_{n-1}$ si  un evento non trascurabile allora$$
\mathcal{P}(A_1 \cap\dots \cap A_n) = \mathcal{P}(A_1)\mathcal{P}(A_2|A_1) \dots\mathcal{P}(A_n|A_1 \cap\dots \cap A_{n-1})
$$ questa è chiamata _formula del condizionamento ripetuto_
la _dimostrazione_ di questo è immediata e basta sostituire ogni termine con la definizione di _probabilità condizionata_ 

>[!tip]
>per $A_{1} \cap\dots\cap A_{k}$ per $k\in[1,n-1)$ l _evento_ non è trascurabile

