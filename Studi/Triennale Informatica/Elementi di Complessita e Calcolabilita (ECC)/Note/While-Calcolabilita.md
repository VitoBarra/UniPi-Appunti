---
Subject: Elementi di calcolabilita e complessita
topic: nota
tags: ECC
---

Prev: [[Elementi di Complessità e Calcolabilità (ECC)]]

# While-Calcolabilita
---

dato un comando $C$ calcola $f: \N\rightarrow \N$, oppure $f$ è WHILE$-Calcolabile \iff$ 
$$\forall n \in \N, \forall \sigma \in Var \rightarrow \N | \sigma(x) = x $$
$$f(n)=m \iff \langle C,\sigma\rangle \rightarrow^*\sigma’ e \ \sigma’(x)=m  $$ essere WHILE-calcolabile significa che può essere calcolato dal [[Linguaggi FOR e WHILE|Linguaggi WHILE]]
