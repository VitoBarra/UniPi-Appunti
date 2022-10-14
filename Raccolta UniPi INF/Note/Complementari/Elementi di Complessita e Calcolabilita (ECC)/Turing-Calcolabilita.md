---
type: nota
course: Elementi di calcolabilita e complessita
topic: 
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# Turing-Calcolabilita
---
dati $\Sigma_0 ,\Sigma_1 ,\Sigma$ Alfabeti con $\#,\rhd  \not \in\Sigma_0 \cup \Sigma_1$ e $\Sigma_0 \cup \Sigma_1 \subset \Sigma$
e $f:\Sigma^*_0 \rightarrow \Sigma^*_1$ una funzione allora si diche che una [[Macchina di Turing]]  calcola $f \iff$ 
$$
 
\forall w \in \Sigma^*_0: f(w) = z \iff (q_0,\trianglerighteq w) \rightarrow^*(h,\rhd z \underline{\!\#\!})$$
Ovvero se esiste una macchina di Turing che con una sequenza di passi trasforma l ingresso $w$ nel output $z\#$
 

